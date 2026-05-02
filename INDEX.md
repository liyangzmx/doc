# 文档索引

> 个人技术笔记 & 学习资料汇总

---

## 工作笔记

- [[works.md|工作笔记]] — 历年来各家公司的工作经历与技术实践记录 (ubifs, u-boot, lua, ffmpeg, OCR, SDR, OTA, SecureBoot, OpenGL ES, WebRTC, Op-TEE, DDS, ANTLR…)

---

## 编程语言 & 绑定

### Rust
- [[coding/rust/rust.md|Rust 学习资源]] — 官方教程、Rust圣经、宏小册、嵌入式、FFI 等学习资料汇总
- [[coding/rust/BuildScript.md|Rust Build Script]] — Cargo build script 的使用：命令执行、bindgen 绑定生成

### Java / JNI
- [[coding/java/jni.md|JNI / Android NDK]] — Java Native Interface 规范、Android NDK 集成、CMake 配置

### C/C++
- [[coding/cpp/libs/glfw.md|GLFW + glad]] — 使用 conan + CMake 搭建 OpenGL 开发环境，附三角形渲染示例

### Python 绑定
- [[binding/pybind11.md|pybind11]] — C++ 与 Python 互操作，conan + CMake 集成示例

---

## 编译技术 (LLVM / Clang / MLIR)

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

### 其他非 Markdown 文件
- [[compile/llvm/launch.json]] — VSCode 调试配置

---

## 网络

- [[net/xdp/xdp_bpf_example.md|XDP / BPF]] — bpf-examples 项目构建与使用

---

## DDS (数据分发服务)

- [[dds/fastdds.md|Fast-DDS]] — 从源码编译安装 eProsima Fast-DDS
- [[dds/rustdds.md|RustDDS]] — Rust 实现的 DDS 示例
- [[dds/IDL_DynamicType.md|IDL DynamicType]] — 使用 ANTLR4 Cpp Runtime 实现 DynamicType Visitor
- [[dds/IDL.g4]] — IDL 的 ANTLR4 语法文件

---

## 安全 & 加密

### OpenSSL
- [[security/openssl_android.md|Android 上编译 OpenSSL]] — NDK 交叉编译 OpenSSL
- [[security/openssl_curl.md|cURL + OpenSSL]] — 使用 OpenSSL 的 libcurl 示例
- [[security/openssl_curl_cust.md|cURL + 自定义签名]] — libcurl 集成自定义签名函数

### 密码协议
- [[security/openssl_spake2_plus.md|SPAKE2+ (C)]] — C 语言实现 CCC3.0 SPAKE2+ 协议
- [[security/openssl_spake2_plus_rust.md|SPAKE2+ (Rust)]] — Rust 实现 CCC3.0 SPAKE2+ 协议
- [[security/go_custkey.md|Go 自定义签名]] — Go 语言集成自定义签名接口

---

## Linux 内核 & 嵌入式

### QEMU 调试
- [[linux/qemu/debug_kernel_via_qemu.md|QEMU 调试内核]] — 通过 QEMU 调试 Linux 内核/模块
- [[linux/qemu/riscv-yocto.md|RISC-V Yocto]] — Docker 中搭建 RISC-V Yocto 构建环境

### 内存管理
- [[linux/swap.md|Linux Swap]] — 创建和管理 swap 文件

### NuttX RTOS
- [[nuttx/nuttx_stm32f4discovery.md|NuttX on STM32]] — 在 STM32F4 Discovery 上运行 NuttX

---

## WebAssembly

- [[WebAssembly/WebAssembly.md|WebAssembly]] — 使用 emscripten/emcc 编译，conan 集成，CMake 配置

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

## 图表 (PlantUML)

- [[plantumls/android_security.puml]] — Android 安全架构图
- [[plantumls/cpu0_deps.puml]] — Cpu0 后端依赖关系图
- [[plantumls/llvm-backend.puml]] — LLVM 后端流程图
- [[plantumls/llvm-llc.puml]] — LLVM LLC 工具流程图

---

## 脚本

- [[scripts/gerrit_query.sh]] — Gerrit 查询脚本

---

> 最后更新: 2026-05-02
