# ECIES 设计方案

## 1. 目标

本文设计一个以 ECDH 为核心的 ECIES-like 混合加密方案，用于“接收方长期公钥 + 发送方临时密钥”场景。

核心目标：

- 用 ECDH 得到共享秘密。
- 用 KDF 派生对称加密密钥和 nonce。
- 用 AEAD 加密业务明文。
- 支持识别输入公钥/私钥的算法类型，尽量自动选择能做 DH 的密钥。
- 明确区分“签名密钥”和“密钥协商密钥”，避免误用 Ed25519/ECDSA 密钥直接做 ECDH。

优先建议：如果项目允许直接采用标准协议，优先采用 HPKE，即 RFC 9180。本文方案是 ECIES 风格的工程设计，可作为自定义协议或内部封装参考。

---

## 2. 推荐密码套件

### 2.1 默认套件

```text
SuiteID: ECIES-X25519-HKDF-SHA256-AES-256-GCM-v1
KEM:     X25519
KDF:     HKDF-SHA256
AEAD:    AES-256-GCM
Hash:    SHA-256
```

推荐理由：

- X25519 专门用于 ECDH，接口简单，工程误用概率低。
- HKDF-SHA256 普遍可用，适合从 ECDH 原始共享秘密派生多个子密钥。
- AES-256-GCM 硬件加速普遍；若目标平台缺少 AES 加速，可替换为 ChaCha20-Poly1305。

### 2.2 可选套件

```text
ECIES-X25519-HKDF-SHA256-CHACHA20-POLY1305-v1
ECIES-P256-HKDF-SHA256-AES-256-GCM-v1
ECIES-P384-HKDF-SHA384-AES-256-GCM-v1
```

选择原则：

| 场景 | 推荐 |
|---|---|
| 新协议、新系统 | X25519 + HKDF-SHA256 + AES-256-GCM/ChaCha20-Poly1305 |
| 需要兼容国密/合规/NIST 生态 | P-256 或 P-384 ECDH |
| 移动端、无 AES 加速 | ChaCha20-Poly1305 |
| 硬件安全模块只支持 NIST 曲线 | P-256/P-384 ECDH |

---

## 3. 密钥类型识别与 DH 密钥选择

### 3.1 基本原则

不要把签名密钥直接当作 DH 密钥使用。

常见密钥用途：

| 算法/曲线 | 常见用途 | 能否直接做 ECDH | 处理方式 |
|---|---:|---:|---|
| X25519 | ECDH/KEM | 可以 | 直接使用 |
| X448 | ECDH/KEM | 可以 | 直接使用 |
| secp256r1 / prime256v1 / P-256 | ECDH 或 ECDSA | 视 KeyUsage 而定 | 仅当用途允许 keyAgreement 时使用 |
| secp384r1 / P-384 | ECDH 或 ECDSA | 视 KeyUsage 而定 | 仅当用途允许 keyAgreement 时使用 |
| secp521r1 / P-521 | ECDH 或 ECDSA | 视 KeyUsage 而定 | 仅当用途允许 keyAgreement 时使用 |
| Ed25519 | EdDSA 签名 | 不可以 | 不做 DH；寻找关联的 X25519 密钥 |
| Ed448 | EdDSA 签名 | 不可以 | 不做 DH；寻找关联的 X448 密钥 |
| ECDSA-with-SHA256 | 签名算法标识 | 不可以直接判断 | 解析底层 EC key 和 KeyUsage |

### 3.2 自动选择逻辑

输入可能是：证书、公钥、私钥、JWK、PEM、DER 或内部 KeyHandle。

选择规则：

```text
function select_dh_key(identity):
    keys = parse_all_keys(identity)

    # 1. 优先选择显式 DH/KEM 密钥
    for key in keys:
        if key.algorithm in [X25519, X448] and key.usage allows keyAgreement:
            return key

    # 2. 其次选择 NIST EC keyAgreement 密钥
    for key in keys:
        if key.curve in [P-256, P-384, P-521] and key.usage allows keyAgreement:
            return key

    # 3. 如果只有签名密钥，不自动转换
    if exists key where key.algorithm in [Ed25519, Ed448, ECDSA]:
        raise NeedKeyAgreementKey(
            "Only signature key found. ECIES requires X25519/X448/ECDH keyAgreement key."
        )

    raise UnsupportedKey("No supported DH key found")
```

### 3.3 Ed25519 与 X25519 的关系

Ed25519 和 X25519 都基于 Curve25519 系列，但用途、编码和算法标识不同。

工程上不要默认把 Ed25519 私钥转换成 X25519 私钥，原因：

- 这会破坏密钥用途隔离。
- 证书、JWK、KMS/HSM 的 KeyUsage 通常明确区分 sign 与 keyAgreement。
- 不同库对转换支持不一致，容易造成互操作和安全审计问题。

可以支持“绑定密钥”机制：一个身份同时持有 Ed25519 签名密钥和 X25519 加密密钥，并由签名密钥对 X25519 公钥做认证。

示例：

```text
IdentityKey:
  sign_alg: Ed25519
  sign_pub: ...
  kem_alg:  X25519
  kem_pub:  ...
  binding_sig = Ed25519.Sign(sign_priv, "ECIES key binding v1" || kem_alg || kem_pub)
```

接收方或目录服务发布：

```json
{
  "sign_alg": "Ed25519",
  "sign_pub": "...",
  "kem_alg": "X25519",
  "kem_pub": "...",
  "binding_sig": "..."
}
```

验证流程：

```text
Verify(sign_pub, "ECIES key binding v1" || kem_alg || kem_pub, binding_sig)
```

验证通过后，ECIES 使用 `kem_pub` 做 ECDH，而不是使用 `sign_pub`。

---

## 4. 加密消息格式

建议采用二进制 TLV 或 protobuf/cbor。下面给出逻辑结构：

```text
ECIESMessageV1 {
    magic:          "ECIES1"
    suite_id:       string
    kem_alg:        string
    ephemeral_pub:  bytes
    salt:           bytes
    nonce:          bytes optional
    aad:            bytes optional
    ciphertext:     bytes
    tag:            bytes
    sender_key_id:  bytes optional
    recipient_kid:  bytes optional
}
```

说明：

- `ephemeral_pub`：发送方临时 ECDH 公钥。
- `salt`：KDF salt，建议 16 或 32 字节随机数。
- `nonce`：AEAD nonce。可以随机生成，也可以从 KDF 派生。推荐从 KDF 派生，避免 nonce 重用。
- `aad`：附加认证数据，不加密但参与认证，例如协议版本、suite_id、sender、recipient、业务 header。
- `recipient_kid`：接收方密钥 ID，用于找到对应私钥。
- `sender_key_id`：如果需要发送方认证，可填发送方签名公钥 ID 或静态 ECDH 公钥 ID。

推荐把如下字段纳入 AAD：

```text
AAD = encode(
  magic,
  suite_id,
  kem_alg,
  ephemeral_pub,
  salt,
  recipient_kid,
  sender_key_id,
  external_aad
)
```

---

## 5. 密钥派生设计

ECDH 输出不应直接作为对称密钥使用，必须经过 KDF。

### 5.1 ECDH

```text
zz = ECDH(ephemeral_private, recipient_public)
```

对 X25519：

```text
zz = X25519(eph_sk, recipient_pk)
if zz == 32 zero bytes:
    reject
```

对 NIST 曲线：

- 必须验证对方公钥是否在曲线上。
- 必须拒绝无穷远点。
- 根据库和曲线要求做 subgroup/order 检查。

### 5.2 HKDF 输入

```text
salt = random(32)
info = "ECIES v1" || suite_id || kem_alg || recipient_kid || ephemeral_pub || context
prk  = HKDF-Extract(salt, zz)
key  = HKDF-Expand(prk, "key"   || info, 32)
nonce= HKDF-Expand(prk, "nonce" || info, 12)
```

如果使用 AES-128-GCM，则 `key` 长度为 16 字节。
如果使用 ChaCha20-Poly1305，则 `key` 长度为 32 字节，`nonce` 长度为 12 字节。

### 5.3 不推荐的派生方式

不要这样做：

```text
key = SHA256(zz)
```

原因：

- 没有 salt。
- 没有上下文绑定。
- 无法安全派生多个用途不同的子密钥。

---

## 6. 加密流程

```text
ECIES_Encrypt(recipient_identity, plaintext, external_aad):
    recipient_dh_pub = select_dh_key(recipient_identity)

    suite = choose_suite(recipient_dh_pub)

    eph_sk, eph_pk = GenerateEphemeralKeyPair(suite.kem_alg)

    zz = ECDH(eph_sk, recipient_dh_pub)
    reject_if_invalid_shared_secret(zz)

    salt = random(32)

    info = encode(
        "ECIES v1",
        suite.suite_id,
        suite.kem_alg,
        recipient_key_id(recipient_dh_pub),
        eph_pk,
        protocol_context
    )

    key   = HKDF(salt, zz, "key"   || info, suite.aead_key_len)
    nonce = HKDF(salt, zz, "nonce" || info, suite.nonce_len)

    aad = encode(
        "ECIES1",
        suite.suite_id,
        suite.kem_alg,
        eph_pk,
        salt,
        recipient_key_id(recipient_dh_pub),
        external_aad
    )

    ciphertext, tag = AEAD_Seal(key, nonce, plaintext, aad)

    zeroize(eph_sk, zz, key)

    return ECIESMessageV1(
        magic="ECIES1",
        suite_id=suite.suite_id,
        kem_alg=suite.kem_alg,
        ephemeral_pub=eph_pk,
        salt=salt,
        ciphertext=ciphertext,
        tag=tag,
        recipient_kid=recipient_key_id(recipient_dh_pub)
    )
```

---

## 7. 解密流程

```text
ECIES_Decrypt(recipient_private_keys, message, external_aad):
    assert message.magic == "ECIES1"

    suite = lookup_suite(message.suite_id)
    recipient_sk = find_private_key(recipient_private_keys, message.recipient_kid)

    assert recipient_sk supports suite.kem_alg
    validate_public_key(message.ephemeral_pub, suite.kem_alg)

    zz = ECDH(recipient_sk, message.ephemeral_pub)
    reject_if_invalid_shared_secret(zz)

    info = encode(
        "ECIES v1",
        message.suite_id,
        message.kem_alg,
        message.recipient_kid,
        message.ephemeral_pub,
        protocol_context
    )

    key   = HKDF(message.salt, zz, "key"   || info, suite.aead_key_len)
    nonce = HKDF(message.salt, zz, "nonce" || info, suite.nonce_len)

    aad = encode(
        "ECIES1",
        message.suite_id,
        message.kem_alg,
        message.ephemeral_pub,
        message.salt,
        message.recipient_kid,
        external_aad
    )

    plaintext = AEAD_Open(key, nonce, message.ciphertext, message.tag, aad)
    if authentication fails:
        return DecryptFailed

    zeroize(zz, key)
    return plaintext
```

---

## 8. 可选：发送方认证

普通 ECIES 只认证接收方：只有接收方能解密，但接收方不能确认发送方是谁。

如果需要发送方认证，有三种做法。

### 8.1 外层签名

发送方用签名私钥对完整消息签名：

```text
sig = Sign(sender_sign_sk, "ECIES signed message v1" || encoded_message)
```

消息增加：

```text
sender_sign_alg
sender_sign_pub_or_kid
signature
```

优点：

- 和 DH 密钥解耦。
- 适合 Ed25519/ECDSA 身份体系。
- 审计清晰。

缺点：

- 签名会暴露发送方身份，不适合匿名发送。

### 8.2 静态-临时 ECDH 认证

发送方也有一个长期 DH 密钥：

```text
zz1 = ECDH(eph_sender_sk, recipient_static_pk)
zz2 = ECDH(sender_static_sk, recipient_static_pk)
secret = HKDF-Extract(salt, zz1 || zz2)
```

优点：

- 不需要签名。
- 可以证明发送方持有某个静态 DH 私钥。

缺点：

- 发送方也必须有 keyAgreement 密钥。
- 协议复杂度增加。
- 仍然需要解决 sender_static_pk 的可信绑定问题。

### 8.3 直接采用 HPKE Auth 模式

如果需要标准化的发送方认证，推荐直接采用 HPKE Auth 模式，而不是自行扩展。

---

## 9. 签名算法识别与 DH 密钥选择策略

### 9.1 X.509 证书

证书中应检查：

- SubjectPublicKeyInfo.algorithm
- namedCurve / OID
- KeyUsage
- ExtendedKeyUsage，若业务定义了用途

策略：

```text
if algorithm == id-X25519:
    accept for keyAgreement
elif algorithm == id-ecPublicKey and namedCurve in [P-256, P-384, P-521]:
    require KeyUsage.keyAgreement
elif algorithm in [id-Ed25519, id-Ed448] or KeyUsage.digitalSignature only:
    reject for ECIES-DH
else:
    reject unsupported
```

### 9.2 JWK

JWK 识别字段：

```json
{
  "kty": "OKP",
  "crv": "X25519",
  "use": "enc",
  "key_ops": ["deriveKey", "deriveBits"]
}
```

接受条件：

```text
kty=OKP, crv=X25519/X448, key_ops contains deriveBits/deriveKey
或
kty=EC, crv=P-256/P-384/P-521, key_ops contains deriveBits/deriveKey
```

拒绝条件：

```text
crv=Ed25519/Ed448
use=sig
key_ops only contains sign/verify
```

### 9.3 PEM/DER 裸公钥

裸 PEM/DER 缺少用途信息时，默认保守：

- X25519/X448：可以作为 DH 公钥。
- P-256/P-384/P-521：只有在调用方明确声明 `purpose=keyAgreement` 时使用。
- Ed25519/Ed448：拒绝用于 DH。

---

## 10. 安全要求

### 10.1 必须项

- 每次加密必须生成新的临时 ECDH 密钥对。
- ECDH 输出必须经过 HKDF。
- AEAD nonce 不得在同一 key 下复用。
- AAD 必须绑定 suite_id、ephemeral_pub、salt、recipient_kid。
- 解密失败统一返回 `DecryptFailed`，不要区分 tag 错、曲线错、padding 错等细节。
- 私钥、共享秘密、派生密钥使用后应清零。
- 不允许降级到弱套件。
- 不允许把签名密钥静默转换为 DH 密钥。

### 10.2 公钥校验

X25519：

- 检查输出是否全 0。
- 使用成熟密码库，不自行实现 field arithmetic。

NIST 曲线：

- 检查点编码格式。
- 检查点在曲线上。
- 检查不是无穷远点。
- 检查曲线参数和预期 suite 一致。

### 10.3 随机数要求

需要 CSPRNG：

- ephemeral private key generation
- salt generation

不建议随机生成 AEAD nonce；推荐从 HKDF 派生 nonce。这样只要每次 ephemeral key 新鲜，nonce 即可避免重用。

---

## 11. 错误处理

错误类型可以内部细分，但对外统一：

```text
UnsupportedSuite
UnsupportedKey
NeedKeyAgreementKey
InvalidPublicKey
DecryptFailed
MalformedMessage
```

对攻击者可见的 API 建议只返回：

```text
InvalidMessage
```

日志中可以记录更细粒度错误，但不要记录：

- 私钥
- ECDH 共享秘密
- HKDF 输出
- 明文
- 完整密文，如果业务敏感

---

## 12. 版本与套件协商

不要让发送方和接收方动态协商弱算法。

推荐策略：

- 接收方身份材料中声明支持的 suite 列表。
- 发送方选择第一个本地也支持的强套件。
- message 中写入 suite_id。
- 解密方必须检查 suite_id 是否被该 recipient key 允许。

示例：

```json
{
  "recipient_kid": "key-2026-04",
  "supported_suites": [
    "ECIES-X25519-HKDF-SHA256-AES-256-GCM-v1",
    "ECIES-X25519-HKDF-SHA256-CHACHA20-POLY1305-v1"
  ]
}
```

---

## 13. 与 HPKE 的关系

本文方案本质上接近 HPKE 的 Base 模式：

```text
encapsulated_key = ephemeral_pub
shared_secret    = DH(ephemeral_sk, recipient_pk)
key_schedule     = HKDF(shared_secret, info)
ciphertext       = AEAD_Seal(key, nonce, plaintext, aad)
```

如果没有强烈的自定义消息格式需求，建议直接实现 HPKE：

- Base 模式：只做接收方加密。
- Auth 模式：同时认证发送方 KEM 私钥。
- PSK/AuthPSK 模式：引入预共享密钥。

---

## 14. 最小测试向量建议

实现完成后至少覆盖：

1. X25519 加密/解密成功。
2. 解密端 recipient_kid 不匹配，失败。
3. 修改 ciphertext 任意 1 bit，失败。
4. 修改 AAD 任意 1 bit，失败。
5. 修改 ephemeral_pub，失败。
6. 重放同一消息：如果业务需要抗重放，应由上层 message_id/timestamp/nonce-cache 处理。
7. 输入 Ed25519 公钥作为 recipient key，应返回 NeedKeyAgreementKey。
8. 输入 ECDSA-only 证书，应拒绝用于 ECDH。
9. P-256 非法点，应拒绝。
10. X25519 全 0 shared secret，应拒绝。

---

## 15. 推荐 API

### 15.1 加密 API

```text
encrypt(
    recipient_identity: IdentityMaterial,
    plaintext: bytes,
    aad: bytes = b"",
    suite_policy: SuitePolicy = default_policy
) -> ECIESMessageV1
```

### 15.2 解密 API

```text
decrypt(
    private_key_store: PrivateKeyStore,
    message: ECIESMessageV1,
    aad: bytes = b""
) -> bytes | DecryptFailed
```

### 15.3 密钥选择 API

```text
select_key_agreement_key(
    identity: IdentityMaterial,
    policy: KeySelectionPolicy
) -> PublicKeyHandle
```

---

## 16. 工程建议

优先使用成熟库：

- libsodium：X25519、ChaCha20-Poly1305、Ed25519 生态成熟。
- BoringSSL/OpenSSL 3.x：X25519、P-256、HKDF、AES-GCM 支持完整。
- Rust：ring、RustCrypto、hpke crate。
- Go：crypto/ecdh、crypto/hkdf、crypto/cipher。

不要自行实现：

- 椭圆曲线点运算。
- AES-GCM。
- ChaCha20-Poly1305。
- HKDF。
- ASN.1/X.509 解析。

---

## 17. 参考标准

- RFC 9180: Hybrid Public Key Encryption，https://www.rfc-editor.org/rfc/rfc9180.html
- RFC 7748: Elliptic Curves for Security，https://datatracker.ietf.org/doc/html/rfc7748
- RFC 8410: Algorithm Identifiers for Ed25519, Ed448, X25519, and X448，https://www.rfc-editor.org/rfc/rfc8410.html
- SEC 1: Elliptic Curve Cryptography，https://www.secg.org/sec1-v2.pdf
