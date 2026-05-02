# 工作笔记

## dyfh

* 实习期, 要做一个[ubifs](https://www.kernel.org/doc/html/latest/filesystems/ubifs.html)的文件系统镜像
* 在 [u-boot](https://www.u-boot.org) 上通过 [“hush” shell](https://github.com/u-boot/u-boot/blob/master/doc/usage/cmdline.rst) 实现启动脚本, 扩充 u-boot 命令
* 完成 u-boot 对 vxWorks 的 boot 工作
* 利用 [lua](https://www.lua.org) 语言实现 [wireshark](https://www.wireshark.org) 私有二进制协议的 [插件](https://www.wireshark.org/docs/wsdg_html_chunked/wsluarm.html)
* 学习 [ffmpeg](https://ffmpeg.org/) 实现 H264 和 acc 编码, 然后 RTMP 推流
* 学些 mp3 编码库 [lame](https://lame.sourceforge.io)
* 应用 google [tesseract](https://github.com/tesseract-ocr/tesseract) 实现 OCR sdk
* 应用 OpenSIFT 实现图像的模式匹配
* 应用 [VBScript](https://www.vandyke.com/support/tips/scripting/index.html#:~:text=This%20user%27s%20guide%20explains%20the%20essentials%20of%20using,the%20scripting%20manual%20in%20PDF%20format%20%281.36%20MB%29) 在 [SecureCRT](https://www.vandyke.com/products/securecrt/) 上实现自动化测试脚本.
* 学习 [Texlive](https://tug.org/texlive/) 编写研发文档

## jl

* 在 [SourceInsight](https://www.sourceinsight.com) 中实现一些实用的 [宏](https://www.sourceinsight.com/doc/v4/userguide/index.html#t=Manual%2FMacro_Language%2FMacro_Language.htm)
* 学习 Android 手机 ROM 的开发, 传感器方向

## ty

* 应用 [libjson-rpc-cpp](https://github.com/cinemast/libjson-rpc-cpp) 实现 CS RPC。它使用 [json](https://www.json.org) 做为 schemma 的描述.
* 应用 [libcurl](https://curl.se/libcurl/) 实现 RPC 的 Http Transport
* 应用 [libevent](https://libevent.org) 实现高性能的网络数据包处理
* 应用 [libconfig](https://github.com/hyperrealm/libconfig) 实现项目配置文件管理
* 通过 SelectMap 在 u-boot 阶段完成 Xilinx FPGA 的配置
* 接触并学习 [libiio](https://github.com/analogdevicesinc/libiio) 等
* 接触并学习 [GnuRadio](https://www.gnuradio.org), 在 [PLUTO SDR](https://www.analog.com/en/resources/evaluation-hardware-and-software/evaluation-boards-kits/adalm-pluto.html) 上学习 SDR 相关知识

## jw

* 学习 [DVB](https://dvb.org) 有关的知识
* 通过 [SCPI](https://en.wikipedia.org/wiki/Standard_Commands_for_Programmable_Instruments) 协议实现对上位机响应的控制

## yn

* 学习 Android 传感器框架, 实现温度传感器的界面显示

## hrxb

* 学习 [OpenWrt](https://openwrt.org), 构建 ROM
* 使用 [ffmpeg](https://ffmpeg.org/) 实现延迟摄影功能
* 实现固件的 A/B OTA

## xntt

* 学习 linux [alsa](https://www.alsa-project.org/wiki/Main_Page) [driver](https://www.kernel.org/doc/html/latest/sound/kernel-api/writing-an-alsa-driver.html), 并实现 ADC/DAC 芯片驱动
* 学习并研究 linux [Thermal](https://www.kernel.org/doc/html/latest/driver-api/thermal/index.html)机制, 并配置温控策略
* 深入研究 Andorid Legacy OTA 中 edify 脚本, 对齐进行扩展
* 深入研究 Android Recovery 中的 UI, 实现 LED 对 OTA 进度的展示
* 学习并实现 AMOLED 的 DSI 显示驱动
* 学习并编写 DTS(Overlay) 硬件配置

## zcyx

* 学习通过 [bsdiff](https://github.com/mendsley/bsdiff) 实现文件系统的 OTA

## qft

* 学习 dm-verity 技术, 并通过其实现文件系统的 OTA
* 接触并学习 IDA Pro / Kali Linux

## xm

* 学习 SecureBoot 原理, 并在产品中启用该功能, 完成支持环节中遇到的各种问题
* 实现 屏幕/音频/按键/电源等驱动
* 实现 Android A/B 全量/差量的 OTA 升级
* 完成工厂测试系统的制作与集成
* 学习通过 SCPI 协议控制仪器仪表
* 学习并制作小功率音频功率放大器(模拟)

## amz

* 学习音频输入切换相关的驱动代码, 完成 Bug 的排查
* 学习屏幕显示相关技术

## dpx

* 完成 I2S 输入驱动调试
* 解决 QSPI Nand Flash 驱动问题
* eMMC 驱动相关的开发工作

## xyxk

* 完成 Android ROM 构建相关的开发工作
* 完成音频产品的原理图审核工作
* 完成服务端的适配工作

## zxzl

* 学习 WASM, 编译相关代码在浏览器中测试其运行
* 实现 Android 屏幕录制功能

## ahjk

* 通过 ffmpeg 扩展 ExoPlayer 支持 Opus 音频编码
* 通过 ffmpeg 实现 视频转码
* 通过 WebRTC 实现端到端的 RTC 传输

## zyb

* 完成基于 Yocto 的 ROM 构建
* 修改并配置 Wayland 实现显示相关的业务需求
* 基于 Jenkins + Docker 实现 ROM 的分布式构建
* 基于 OpenGL ES 在 android native 实现 WebRTC 渲染及部分效果器
* 基于 NDK AMediaCodec 实现 WebRTC 编码的硬解码
* 学习并通过 FreeType 实现字体在 OpenGL ES 中的渲染

## yxkj

* 通过 qemu 实现对 Linux Module/Application 的调试
* 学习 Ofono 框架, 学习 Qt Framework并实现一个时钟部件
* 学习 Op-TEE, 及其相关的原理

## wlqc

* 通过 libcurl 实现 SecureBoot SignTool的在线签名
* 修改 avbtool 实现 AVB 在线签名
* 实现 Op-TEE 的 TA (自研算法)
* 实现 Android JSEE Framework 框架
* 设计并实现 HDCP 密钥分发系统
* 实现多语言的 ECIES 算法实现
* 学习并验证 ECC 相关的签名/密钥交换算法

## lxqc

* 将开源的 CyberRT sharememory 代码适配自研 DDS 项目
* 学习并使用 conan 完成 VBS Example的版本发布
* 学习并使用 ANTLR 完成 VSCode 对 IDL的补全(Type Script)
* 使用 ANTLR 完成 IDL 到 XML 的转换(C++)
* 使用 pybind11 实现了 DDS 动态类型到静态类型的绑定
* 学习 eBNF 并辨析了 MLIR TableGen 文件的文法解析
* 通过 construct 实现了私有二进制数据封装的解析