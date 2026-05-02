# SPAKE2+ 协议 — OpenSSL 3.0 实现

## 概述

SPAKE2+（Augmented Password-Authenticated Key Exchange）是一种增强型口令认证密钥交换协议。与普通 SPAKE2 相比，SPAKE2+ 额外提供了 **Augmented 属性**：即使服务端数据库泄露，攻击者无法直接冒充客户端（需要额外破解口令）。

本实现使用 **P-256（secp256r1）** 椭圆曲线，完整跑通协议双方的计算流程，验证共享密钥的一致性。

## 协议流程与公式

### 1. 密码派生

```
pwKey = scrypt(password="000000", salt=[0;40], N=32768, r=8, p=1, len=80)

z0 || z1 = pwKey          // 拆分为前 40 字节和后 40 字节
  z0 = z0_raw mod (n-1)   // 映射到 [0, n-2]
  z1 = z1_raw mod (n-1)

w0 = z0 + 1               // 映射到 [1, n-1]，保证非零
w1 = z1 + 1
```

其中 `n` 是 P-256 的阶：
```
n = 0xFFFFFFFF00000000FFFFFFFFFFFFFFFFBCE6FAADA7179E84F3B9CAC2FC632551
```

### 2. 公开参数

- **G** — P-256 生成元
- **M、N** — 协议的 nothing-up-my-sleeve 公开点（来自 SPAKE2+ 规范）

### 3. 协议消息

```
Client → Server:
    X = x·G + w0·M          # Ephemeral DH mask blinded by password
    L = w1·G                # Augmented verification commitment

Server → Client:
    Y = y·G + w0·N          # Ephemeral DH mask blinded by password
```

`x`、`y` 为随机标量（32 字节随机数后 `mod (n-1)`）。

### 4. 共享密钥计算

**Client 方（Prover）— 收到 Y 后：**

```
Y - w0·N = y·G + w0·N - w0·N = y·G           // 剥离密码盲化因子
     Zp = x · (Y - w0·N) = x·y·G              // ECDH 共享秘密
     Vp = w1 · (Y - w0·N) = w1·y·G            // Augmented 验证值
```

**Server 方（Verifier）— 收到 X、L 后：**

```
X - w0·M = x·G + w0·M - w0·M = x·G           // 剥离密码盲化因子
     Zv = y · (X - w0·M) = x·y·G              // ECDH 共享秘密
     Vv = y · L = y·w1·G                      // Augmented 验证值
```

### 5. 核心恒等式

```
Zp = Zv = x·y·G          → 会话密钥双方一致
Vp = Vv = w1·y·G         → Augmented 验证值双方一致
```

**Augmented 的意义**：`Vp/Vv` 依赖 `w1`（来自口令），Server 通过比对 `Vv` 与 `Vp` 可以确认 Client 确实知道口令。即使 Server 的 `w0` 泄露，攻击者没有 `w1` 也无法生成正确的 `V` 值。

## OpenSSL 3.0 API 对照

| 操作 | OpenSSL 3.0 API | 说明 |
|------|----------------|------|
| 创建曲线 | `EC_GROUP_new_by_curve_name(NID_X9_62_prime256v1)` | P-256 |
| 获取生成元 | `EC_GROUP_get0_generator(group)` | 返回常量指针，无需释放 |
| 获取阶 | `EC_GROUP_get_order(group, n, ctx)` | 曲线阶 |
| 获取余因子 | `EC_GROUP_get_cofactor(group, h, ctx)` | P-256 余因子 = 1 |
| 点乘 + 点加 | `EC_POINT_mul(group, r, n, q, m, ctx)` | `r = n·G + m·q` |
| 纯点乘 | `EC_POINT_mul(group, r, NULL, q, m, ctx)` | `r = m·q`（无 G 项） |
| 点加 | `EC_POINT_add(group, r, a, b, ctx)` | `r = a + b` |
| 点取反 | `EC_POINT_invert(group, a, ctx)` | `a = -a`（加法逆元） |
| 口令派生 | `EVP_PBE_scrypt(pass, plen, salt, slen, N, r, p, maxmem, out, olen)` | scrypt 派生 |
| 随机数 | `RAND_bytes(buf, len)` | 真随机数 |
| hex 解码为点 | `EC_POINT_hex2point(group, hex, NULL, ctx)` | 自动解析 uncompressed 格式 |
| 点编码为 hex | `EC_POINT_point2hex(group, p, POINT_CONVERSION_UNCOMPRESSED, ctx)` | 返回 hex 字符串 |

## 实现思路

1. **单文件模拟双方**：代码不区分 Client/Server 进程，在一个 main() 中顺序计算双方的状态，目的是验证数学一致性。

2. **核心技巧 — 盲化因子剥离**：收到对端消息后，用 `w0` 乘以对应公开参数（M 或 N），取反后加到消息上，即可消去口令盲化层，得到纯粹的 DH 分量。

3. **EC_POINT_mul 的双重用途**：
   - 构造消息时：`X = x·G + w0·M` → 一次 `EC_POINT_mul` 调用
   - 计算共享密钥时：`Zp = x · (Y - w0·N)` → `EC_POINT_mul` 只做纯点乘（传 NULL 作为 n 参数）

4. **EC_POINT_invert 求加法逆元**：OpenSSL 通过 `EC_POINT_invert` 直接计算椭圆曲线上的负点，等价于 `-(w0·N)`，配合 `EC_POINT_add` 实现减法。

## 完整代码

```c
// SPAKE2+ protocol implementation using OpenSSL 3.0
// References:
//   - SPAKE2+ draft: https://datatracker.ietf.org/doc/draft-irtf-cfrg-spake2-plus/
//   - Curve: P-256 (secp256r1, X9_62_PRIME256V1)

#include <stdio.h>
#include <string.h>
#include <openssl/bn.h>
#include <openssl/ec.h>
#include <openssl/evp.h>
#include <openssl/obj_mac.h>
#include <openssl/rand.h>

static void print_hex(const char *label, const unsigned char *data, size_t len) {
    printf("%s: ", label);
    for (size_t i = 0; i < len; i++)
        printf("%02x", data[i]);
    printf("\n");
}

static void print_bn_hex(const char *label, const BIGNUM *bn) {
    char *hex = BN_bn2hex(bn);
    printf("%s: %s\n", label, hex ? hex : "(null)");
    OPENSSL_free(hex);
}

static void print_point_hex(const char *label, const EC_GROUP *group,
                            const EC_POINT *point, BN_CTX *ctx) {
    char *hex = EC_POINT_point2hex(group, point,
                                   POINT_CONVERSION_UNCOMPRESSED, ctx);
    printf("%s: %s\n", label, hex ? hex : "(null)");
    OPENSSL_free(hex);
}

int main(void) {
    BN_CTX *bn_ctx = BN_CTX_new();

    /* ---------- curve setup ---------- */
    EC_GROUP *group = EC_GROUP_new_by_curve_name(NID_X9_62_prime256v1);
    const EC_POINT *G = EC_GROUP_get0_generator(group);

    BIGNUM *ONE = BN_new();
    BN_set_word(ONE, 1);

    print_point_hex("G", group, G, bn_ctx);

    BIGNUM *n = BN_new();
    EC_GROUP_get_order(group, n, bn_ctx);
    print_bn_hex("n", n);

    BIGNUM *h = BN_new();
    EC_GROUP_get_cofactor(group, h, bn_ctx);
    print_bn_hex("h", h);

    BIGNUM *nMinusOne = BN_dup(n);
    BN_sub_word(nMinusOne, 1);
    print_bn_hex("nMinusOne", nMinusOne);

    /* ---------- public parameters M, N ---------- */
    const char m_hex[] = "048624e6926e81d7d6e43f636868528282c451d5ecfa3de74cab078011a4827d5e53fcc6d0e990f9da157e1125640f86d0a0739cc4dbd7efe4fcb4e541f8150ac7";
    const char n_hex[] = "0408adacc492da7806cfbd43ac770f4e8dae0260bc31ce34fcee9fb39a628db19a3922ab64dafa3adda43fb35e1941704cf67af0bf70ea506a51993dc85e2e118c";

    EC_POINT *M = EC_POINT_hex2point(group, m_hex, NULL, bn_ctx);
    EC_POINT *N_pt = EC_POINT_hex2point(group, n_hex, NULL, bn_ctx);

    print_point_hex("M", group, M, bn_ctx);
    print_point_hex("N", group, N_pt, bn_ctx);

    /* ---------- password derivation (scrypt) ---------- */
    unsigned char pwKey[80];
    unsigned char salt[40] = {0};

    // scrypt memory needed: 128 * N * r * p = 128 * 32768 * 8 * 1 = 33.5 MB
    if (EVP_PBE_scrypt("000000", 6, salt, sizeof(salt),
                       32768, 8, 1, 64 * 1024 * 1024,
                       pwKey, sizeof(pwKey)) != 1) {
        fprintf(stderr, "EVP_PBE_scrypt failed\n");
        return 1;
    }
    print_hex("pwKey", pwKey, sizeof(pwKey));

    /* split pwKey → z0 (bytes 0-39), z1 (bytes 40-79) */
    BIGNUM *_z0 = BN_bin2bn(pwKey, 40, NULL);
    BIGNUM *_z1 = BN_bin2bn(pwKey + 40, 40, NULL);
    print_bn_hex("z0", _z0);

    // z0 = _z0 mod (n-1),  z1 = _z1 mod (n-1)
    BIGNUM *z0 = BN_new();
    BIGNUM *z1 = BN_new();
    BN_mod(z0, _z0, nMinusOne, bn_ctx);
    BN_mod(z1, _z1, nMinusOne, bn_ctx);

    // w0 = z0 + 1,  w1 = z1 + 1
    BIGNUM *w0 = BN_new();
    BIGNUM *w1 = BN_new();
    BN_add(w0, z0, ONE);
    BN_add(w1, z1, ONE);

    print_bn_hex("w0", w0);
    print_bn_hex("w1", w1);

    /* ---------- random scalars x, y ---------- */
    unsigned char rand_buf[32];
    BIGNUM *x = BN_new();
    BIGNUM *y = BN_new();

    RAND_bytes(rand_buf, sizeof(rand_buf));
    BIGNUM *_x = BN_bin2bn(rand_buf, sizeof(rand_buf), NULL);
    print_bn_hex("x (raw)", _x);
    BN_mod(x, _x, nMinusOne, bn_ctx);
    print_bn_hex("x", x);

    RAND_bytes(rand_buf, sizeof(rand_buf));
    BIGNUM *_y = BN_bin2bn(rand_buf, sizeof(rand_buf), NULL);
    print_bn_hex("y (raw)", _y);
    BN_mod(y, _y, nMinusOne, bn_ctx);
    print_bn_hex("y", y);

    /* ---------- protocol messages ---------- */
    // EC_POINT_mul(group, r, n, q, m, ctx)  →  r = n·G + m·q

    // X = x·G + w0·M
    EC_POINT *X = EC_POINT_new(group);
    EC_POINT_mul(group, X, x, M, w0, bn_ctx);
    print_point_hex("X", group, X, bn_ctx);

    // Y = y·G + w0·N
    EC_POINT *Y = EC_POINT_new(group);
    EC_POINT_mul(group, Y, y, N_pt, w0, bn_ctx);
    print_point_hex("Y", group, Y, bn_ctx);

    // L = w1·G  (n=NULL → no n·G term, just m·q = w1·G)
    EC_POINT *L = EC_POINT_new(group);
    EC_POINT_mul(group, L, NULL, G, w1, bn_ctx);
    print_point_hex("L", group, L, bn_ctx);

    /* ---------- Prover side: Zp, Vp ---------- */
    // N' = -w0·N
    EC_POINT *N_mul_w0 = EC_POINT_new(group);
    EC_POINT_mul(group, N_mul_w0, NULL, N_pt, w0, bn_ctx);
    EC_POINT_invert(group, N_mul_w0, bn_ctx);

    // Zp_add = Y + (-w0·N) = y·G
    EC_POINT *Zp_add = EC_POINT_new(group);
    EC_POINT_add(group, Zp_add, Y, N_mul_w0, bn_ctx);

    // Zp = x · Zp_add = x·y·G
    EC_POINT *Zp = EC_POINT_new(group);
    EC_POINT_mul(group, Zp, NULL, Zp_add, x, bn_ctx);
    print_point_hex("Zp", group, Zp, bn_ctx);

    // Vp = w1 · Zp_add = w1·y·G
    EC_POINT *Vp = EC_POINT_new(group);
    EC_POINT_mul(group, Vp, NULL, Zp_add, w1, bn_ctx);
    print_point_hex("Vp", group, Vp, bn_ctx);

    /* ---------- Verifier side: Zv, Vv ---------- */
    // M' = -w0·M
    EC_POINT *M_mul_w0 = EC_POINT_new(group);
    EC_POINT_mul(group, M_mul_w0, NULL, M, w0, bn_ctx);
    EC_POINT_invert(group, M_mul_w0, bn_ctx);

    // Zv_sub = X + (-w0·M) = x·G
    EC_POINT *Zv_sub = EC_POINT_new(group);
    EC_POINT_add(group, Zv_sub, X, M_mul_w0, bn_ctx);

    // Zv = y · Zv_sub = x·y·G
    EC_POINT *Zv = EC_POINT_new(group);
    EC_POINT_mul(group, Zv, NULL, Zv_sub, y, bn_ctx);
    print_point_hex("Zv", group, Zv, bn_ctx);

    // Vv = y · L = w1·y·G
    EC_POINT *Vv = EC_POINT_new(group);
    EC_POINT_mul(group, Vv, NULL, L, y, bn_ctx);
    print_point_hex("Vv", group, Vv, bn_ctx);

    /* ---------- cleanup ---------- */
    EC_POINT_free(Vv);    EC_POINT_free(Zv);    EC_POINT_free(Zv_sub);
    EC_POINT_free(M_mul_w0);
    EC_POINT_free(Vp);    EC_POINT_free(Zp);    EC_POINT_free(Zp_add);
    EC_POINT_free(N_mul_w0);
    EC_POINT_free(L);     EC_POINT_free(Y);     EC_POINT_free(X);
    EC_POINT_free(N_pt);  EC_POINT_free(M);

    BN_free(y);           BN_free(_y);
    BN_free(x);           BN_free(_x);
    BN_free(w1);          BN_free(w0);
    BN_free(z1);          BN_free(z0);
    BN_free(_z1);         BN_free(_z0);
    BN_free(nMinusOne);   BN_free(h);           BN_free(n);
    BN_free(ONE);

    EC_GROUP_free(group);
    BN_CTX_free(bn_ctx);

    return 0;
}
```

## 编译与运行

```bash
gcc -o spake2plus src/spake2plus.c \
    -I$(brew --prefix openssl@3)/include \
    -L$(brew --prefix openssl@3)/lib -lcrypto \
    -Wno-deprecated-declarations

./spake2plus
```

预期输出中 `Zp == Zv` 且 `Vp == Vv`，证明双方计算结果一致。

### 实际运行输出

```text
G: 046B17D1F2E12C4247F8BCE6E563A440F277037D812DEB33A0F4A13945D898C2964FE342E2FE1A7F9B8EE7EB4A7C0F9E162BCE33576B315ECECBB6406837BF51F5
n: FFFFFFFF00000000FFFFFFFFFFFFFFFFBCE6FAADA7179E84F3B9CAC2FC632551
h: 01
nMinusOne: FFFFFFFF00000000FFFFFFFFFFFFFFFFBCE6FAADA7179E84F3B9CAC2FC632550
M: 048624E6926E81D7D6E43F636868528282C451D5ECFA3DE74CAB078011A4827D5E53FCC6D0E990F9DA157E1125640F86D0A0739CC4DBD7EFE4FCB4E541F8150AC7
N: 0408ADACC492DA7806CFBD43AC770F4E8DAE0260BC31CE34FCEE9FB39A628DB19A3922AB64DAFA3ADDA43FB35E1941704CF67AF0BF70EA506A51993DC85E2E118C
pwKey: 7fd6112660bf21010f510aaf8da2de695ef3af49584e3a0574e2e7625080cdaa34ecf6328e4ac1fd6443b77f5f37dc97c8aae09966d744b18f4e11b72ce24423f548288d6f9d2084026f1e41a90e2bc5
z0: 7FD6112660BF21010F510AAF8DA2DE695EF3AF49584E3A0574E2E7625080CDAA34ECF6328E4AC1FD
w0: 70102BAFAD0DAC42807534567F2E1620E0609C05E80E0D293C9F7CF8065672CE
w1: 27E2BD30A35BB09AA99597701B9E435588DBED3E6095A447A8CAB114CD239196
x (raw): 2E5384F1FCA945617818EFAC730A26CA9FBBB1F5F1D013D95E4DD84B92DA073C
x: 2E5384F1FCA945617818EFAC730A26CA9FBBB1F5F1D013D95E4DD84B92DA073C
y (raw): 266170B103106588F80C376445C486B4CDB78A2EA5B32BE22E3893505F47C3C8
y: 266170B103106588F80C376445C486B4CDB78A2EA5B32BE22E3893505F47C3C8
X: 04404DF3FF14B8C785C60F9459267733863888056643BE27BCBB5794044D1CCB15662AE0AA47E3711A74E06D628B4BB2D5C30DC2B76A34D92776DC970B4DE57E53
Y: 042C307AA6D3EABAFD5FEFBEF730F76619225FBC6B964D69E26BABB8CA7F5FC2E3361CFDC4E0FFDDFC62C0F7ECA879011DF046ED683B7965F22B0552A0209F1762
L: 0430A7AE9972122834A93DA8FF7C16EE0A5390BF9FBBB69E310F004889C809D184116893D35F52B69F955A4DCD96B9C8AC8F527F1829FEC1F21AD7B18B4734F7E7
Zp: 04834C33E759BCA7D491A932590F82F1CFB1BDB00FAC8FB81F786E37F4B3F11B14267EF43F0C7D68DCE0213D1722CF73AF0447A8B3DF160815BA679CDF57317CE2
Vp: 04B970919E54D660EF4E41AF8AB0AE4C98C386E88AEB704BEAEE84E74822675174638C831631E83A93A9A1220D9742C97E8590EDE85D63DB158F74E7B2E1DF2D35
Zv: 04834C33E759BCA7D491A932590F82F1CFB1BDB00FAC8FB81F786E37F4B3F11B14267EF43F0C7D68DCE0213D1722CF73AF0447A8B3DF160815BA679CDF57317CE2
Vv: 04B970919E54D660EF4E41AF8AB0AE4C98C386E88AEB704BEAEE84E74822675174638C831631E83A93A9A1220D9742C97E8590EDE85D63DB158F74E7B2E1DF2D35
```

验证：

- **Zp == Zv** ✅ — 双方 ECDH 共享密钥一致
- **Vp == Vv** ✅ — Augmented 验证值一致
- **L** 固定不变（与 Rust 版本相同），因为 `w1` 由口令确定性派生且 `G` 固定
- **x、y、X、Y** 每次运行不同，因为随机数变化
