# 文档索引

> 个人技术笔记 & 学习资料汇总

---

## 资源收藏

- [[links/ai_urls.md|AI / LLM 工具收藏]] — AI/LLM 相关工具链与开源项目链接汇总 (Ollama, LangChain, llama.cpp, MinerU 等)
- [[links/csdiy_links.md|CS自学指南 · 必学工具]] — csdiy.wiki 必学工具板块参考资料 (Vim, Git, LaTeX, Docker, Scoop, 实用工具箱等)

---

## 编译器

### LLVM 基础
- [[compile/llvm/llvm.md|LLVM 编译与安装]] — 从源码构建 LLVM 18.x
- [[compile/llvm/ir.md|LLVM IR 基础]] — SSA 形式、类型系统、IR 核心概念
- [[compile/llvm/llvm_ir_build.md|LLVM IR Build API]] — IRBuilder、Value 继承体系

### LLVM 教程 (Getting Started)
- [[compile/llvm/getting_started/helloworld.md|HelloWorld]] — LLVM 编译器实战教程 3.6
- [[compile/llvm/getting_started/llvm-use.md|LLVM 使用]] — 工具链简介 (教程 3.3)
- [[compile/llvm/getting_started/tokens.md|获取 Tokens]] — clang 词法分析
- [[compile/llvm/getting_started/ast_statics.md|AST 统计]] — 语法树节点统计
- [[compile/llvm/getting_started/visit.md|Clang Visitor]] — RecursiveASTVisitor 遍历子节点
- [[compile/llvm/getting_started/serverity.md|诊断信息]] — clang 诊断/错误信息获取

### Clang 工具
- [[compile/clang/clang-format.md|clang-format]] — 代码格式化工具与配置
- [[compile/clang/clang_ast.md|clang AST]] — 语法树结构分析
- [[compile/clang/clang_tool.md|clang tool]] — 编写 RecursiveASTVisitor 工具

### Clang 编译器前端
- [[compile/llvm/clang_compiler/syntax-check.md|Syntax Check]] — 《Clang Compiler Frontend》语法检查示例

### LLVM 后端
- [[compile/llvm/llvm_cpu0.md|LLVM Cpu0 后端]] — 自定义后端实现
- [[compile/llvm/cpu0_tblgen.md|Cpu0 TableGen]] — Cpu0 后端的 TableGen 描述

### TableGen
- [[compile/llvm/tblgen.md|TableGen 笔记]] — 寄存器、指令等 Record 定义

### MLIR
- [[compile/llvm/mlir.md|MLIR]] — 多层中间表示入门

### ANTLR
- [[compile/llvm/antlr-Kaleidoscope.md|Kaleidoscope 语法]] — ANTLR4 实现 LLVM Kaleidoscope 语言
- [[compile/llvm/antlr-TOY.md|TOY 语法]] — ANTLR4 实现 MLIR TOY 语言

### DDS (数据分发服务)
- [[dds/fastdds.md|Fast-DDS]] — 从源码编译安装 eProsima Fast-DDS
- [[dds/IDL_DynamicType.md|IDL DynamicType]] — 使用 ANTLR4 Cpp Runtime 实现 DynamicType Visitor
- [[dds/IDL.g4]] — IDL 的 ANTLR4 语法文件

### 其他
- [[compile/llvm/launch.json]] — VSCode 调试配置

---

## 安全

### OpenSSL
- [[security/openssl_android.md|Android 上编译 OpenSSL]] — NDK 交叉编译 OpenSSL
- [[security/openssl_curl.md|cURL + OpenSSL]] — 使用 OpenSSL 的 libcurl 示例
- [[security/openssl_curl_cust.md|cURL + 自定义签名]] — libcurl 集成自定义签名函数

### 密码协议
- [[security/openssl_spake2_plus.md|SPAKE2+ (C)]] — C 语言实现 CCC3.0 SPAKE2+ 协议
- [[security/openssl_spake2_plus_rust.md|SPAKE2+ (Rust)]] — Rust 实现 CCC3.0 SPAKE2+ 协议
- [[security/SPAKE2Plus_OpenSSL.md|SPAKE2+ (OpenSSL 3.0)]] — P-256 椭圆曲线实现 SPAKE2+，含完整协议流程与共享密钥验证
- [[security/go_custkey.md|Go 自定义签名]] — Go 语言集成自定义签名接口

### 协议设计
- [[security/ECIES_DESIGN_GPT.md|ECIES 设计方案]] — 以 ECDH 为核心的 ECIES-like 混合加密方案，含 KDF + AEAD 工程设计

---

## 数学

### 高等数学 (同济版)
- [[math/tjgs.md|高等数学（同济版）]] — 函数与极限、导数与微分、微分中值定理、不定积分、定积分

### 其他数学
- [[math/gd.md|线性方程组的解]] — 矩阵消元法
- [[math/gl.md|概率论基本概念]] — 随机实验、统计规律性
- [[math/hm.md|基础概念]] — 区间表示等基础
- [[math/sym.md|LaTeX 符号表]] — 希腊字母等符号语法

### 数学工具
- [[math/python/sympyt.ipynb]] — SymPy 符号计算 Notebook

---

## 其它

- [[works.md|工作笔记]] — 历年来各家公司的工作经历与技术实践记录 (ubifs, u-boot, lua, ffmpeg, OCR, SDR, OTA, SecureBoot, OpenGL ES, WebRTC, Op-TEE, DDS, ANTLR…)

### 图表 (PlantUML)
- [[plantumls/android_security.puml]] — Android 安全架构图
- [[plantumls/cpu0_deps.puml]] — Cpu0 后端依赖关系图
- [[plantumls/llvm-backend.puml]] — LLVM 后端流程图
- [[plantumls/llvm-llc.puml]] — LLVM LLC 工具流程图

### 脚本
- [[scripts/gerrit_query.sh]] — Gerrit 查询脚本

---

> 最后更新: 2026-05-03
