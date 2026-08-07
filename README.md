<div align="center">

# 镜笺 Lenscript

**跨平台照片 EXIF 水印 / 边框工具 —— 24 套样式，一套纯 Rust 引擎驱动 5 个客户端**

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![Website](https://img.shields.io/badge/在线使用-mark.lenscript.cn-brightgreen)](https://mark.lenscript.cn)
[![QQ群](https://img.shields.io/badge/QQ%E7%BE%A4-824558022-12B7F5)](#交流与支持)

**[English](README.en.md)** ｜ 简体中文

**这是镜笺的展示仓库**（只放介绍与图片，不含源代码）。
源代码在 **[github.com/zhousodo/lenscript](https://github.com/zhousodo/lenscript)**。

**在线使用：[https://mark.lenscript.cn](https://mark.lenscript.cn)**

<img src="images/hero.jpg" width="640" alt="镜笺 Lenscript 相机照片 EXIF 水印示例：奶油底签样式，Sony α7C II 机型、镜头、拍摄参数、日期署名与品牌 Logo">

</div>

## 这是什么

镜笺给你的照片加上一条好看的 EXIF 信息栏或边框——相机型号、镜头、光圈快门 ISO、
拍摄时间、你的署名，再配上品牌 Logo。24 套内置样式，一套纯 Rust 引擎驱动，
不覆盖原文件、不降低分辨率：JPEG 以质量 100 + 4:4:4 重编码，PNG 像素无损。

功能对标 [Semi-Utils](https://github.com/leslievan/semi-utils)，是在其基础上用
Rust 重写、扩展样式与多端支持的衍生项目（Apache-2.0）。

## 五个客户端，一套引擎

- **浏览器（WebAssembly）**——打开网页即用，无需安装：**[mark.lenscript.cn](https://mark.lenscript.cn)**
- **桌面应用**（Windows / macOS / Linux，基于 Tauri）
- **本地网页应用**——启动一个小服务，浏览器打开本机地址使用
- **命令行 CLI**——批量处理、脚本集成
- **Android**

五端共用同一套渲染引擎和样式库，效果一致，只是界面不同。

## 照片全程在本地处理

**不会上传你的照片。** 无论浏览器版、桌面版还是命令行，所有渲染都在你自己的设备上完成，
不经过任何服务器。GPS 位置信息默认从输出中移除。

镜笺包含一个**默认开启（可在设置中关闭）的匿名使用统计**：只发送功能使用次数这类计数，
不会发送照片、文件名或拍摄信息，也不会在你的设备上存储任何标识符。

## 样式一览（24 套内置，同一张照片真实渲染）

| | | |
|:---:|:---:|:---:|
| <img src="images/styles/standard-watermark.jpg" alt="照片水印样式：标准水印，机型/镜头/参数/时间+品牌Logo底栏"> **标准水印** | <img src="images/styles/standard-watermark-2.jpg" alt="照片水印样式：标准水印2，圆角阴影留白社交分享风"> **标准水印2** | <img src="images/styles/cream-caption.jpg" alt="照片水印样式：奶油底签，奶油色底栏机型镜头参数日期署名"> **奶油底签** |
| <img src="images/styles/midnight-gold.jpg" alt="照片水印样式：黑金夜行，夜景街拍黑金底栏"> **黑金夜行** | <img src="images/styles/editorial-topline.jpg" alt="照片水印样式：极简顶栏，不裁切照片的克制顶栏"> **极简顶栏** | <img src="images/styles/technical-plate.jpg" alt="照片水印样式：技术铭牌，深色技术底栏曝光参数"> **技术铭牌** |
| <img src="images/styles/blurred-background.jpg" alt="照片水印样式：背景模糊，模糊背景居中相框"> **背景模糊** | <img src="images/styles/soft-focus.jpg" alt="照片水印样式：柔焦，圆角相卡浮于放大模糊背景"> **柔焦** | <img src="images/styles/bottom-right-parameters.jpg" alt="照片水印样式：右下角参数，极简直印"> **右下角参数** |
| <img src="images/styles/centered-logo.jpg" alt="照片水印样式：logo居中，中心品牌Logo相机信息"> **logo居中** | <img src="images/styles/dark-border.jpg" alt="照片水印样式：暗色边框，夜景街拍沉稳质感"> **暗色边框** | <img src="images/styles/polaroid.jpg" alt="照片水印样式：拍立得，白色留白底部题注相纸风"> **拍立得** |
| <img src="images/styles/black-gallery.jpg" alt="照片水印样式：黑框画廊，黑色画廊卡纸作品集"> **黑框画廊** | <img src="images/styles/minimal.jpg" alt="照片水印样式：简约，轻量字体大留白"> **简约** | <img src="images/styles/film-stamp.jpg" alt="照片水印样式：胶片，右下角橙色胶片戳日期"> **胶片** |
| <img src="images/styles/magazine.jpg" alt="照片水印样式：杂志，极简底栏大留白杂志封面"> **杂志** | <img src="images/styles/centered-caption.jpg" alt="照片水印样式：居中题注，白色相框画廊标签"> **居中题注** | <img src="images/styles/dark-polaroid.jpg" alt="照片水印样式：暗色拍立得，暖调深色相纸复古胶片"> **暗色拍立得** |
| <img src="images/styles/floating-label.jpg" alt="照片水印样式：浮签，左下角浮签式淡字直印"> **浮签** | <img src="images/styles/corner-label.jpg" alt="照片水印样式：角标，左上角机型日期小字"> **角标** | <img src="images/styles/minimal-centered.jpg" alt="照片水印样式：极简中置，品牌Logo机型居中白字"> **极简中置** |
| <img src="images/styles/centered-two-line.jpg" alt="照片水印样式：中置双行，Logo机型参数双行居中"> **中置双行** | <img src="images/styles/kodak-35mm-film.jpg" alt="照片水印样式：柯达胶片，135胶片条齿孔柯达黄"> **柯达胶片** | <img src="images/styles/medium-format-film.jpg" alt="照片水印样式：中画幅胶片，120圆角黑框竖排KODAK帧号"> **中画幅胶片** |

> 展示图为压缩预览；实际导出为全分辨率原质量。样张由 CLI 用同一张测试照片真实渲染生成。

## 在线体验

**[mark.lenscript.cn](https://mark.lenscript.cn)** —— 浏览器打开即用，不需要安装任何东西，
照片在你的浏览器里处理，不会离开你的设备。

## 交流与支持

镜笺由一名热爱摄影的学生独立开发和维护。

- **QQ 交流群：824558022** —— 交流反馈、问题排查、样片共创，欢迎加入。
- 觉得好用请去源代码仓库 [github.com/zhousodo/lenscript](https://github.com/zhousodo/lenscript)
  点一个 ⭐ **Star**——这是对独立开发者最直接的支持。

项目会继续免费使用；如果镜笺曾帮你更体面地分享一张照片，可自愿打赏支持服务器、
域名、测试设备和多平台适配成本。支持不影响任何功能，未成年人请先征得监护人同意。

<div align="center">

| 微信打赏 | 支付宝打赏 |
|:---:|:---:|
| <img src="support/wechat.jpg" width="180" alt="微信打赏二维码"> | <img src="support/alipay.jpg" width="180" alt="支付宝打赏二维码"> |

</div>

## 致谢

**[Semi-Utils](https://github.com/leslievan/semi-utils)**（Apache-2.0）——本项目的功能蓝本与出发点，
感谢 leslievan 与全体贡献者的开创性工作。

## 关于本仓库

本仓库是镜笺面向用户的展示门面，只包含 README 与图片，**不含任何源代码**。
源代码、开发文档与工程细节都在 **[github.com/zhousodo/lenscript](https://github.com/zhousodo/lenscript)**。

镜笺源码为 Apache-2.0 衍生项目（基于 Semi-Utils，Apache-2.0），完整许可条款见源码仓库；
本展示仓库中的文字与图片同样以 [Apache-2.0 许可](LICENSE) 提供。品牌 Logo 为各自商标，
仅用于示例，不代表镜笺与相关厂商有任何合作关系。
