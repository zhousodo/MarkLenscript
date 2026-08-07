<div align="center">

# 镜笺 Lenscript

**跨平台照片 EXIF 水印 / 边框工具 —— 24 套样式，一套纯 Rust 引擎驱动 5 个客户端**

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![Release](https://img.shields.io/github/v/release/zhousodo/lenscript)](https://github.com/zhousodo/lenscript/releases)
[![Website](https://img.shields.io/badge/在线使用-mark.lenscript.cn-brightgreen)](https://mark.lenscript.cn)
[![QQ群](https://img.shields.io/badge/QQ%E7%BE%A4-824558022-12B7F5)](#交流与支持)

**[简体中文](README.md)** | [English](README.en.md)

<img src="docs/assets/hero.jpg" width="640" alt="镜笺 Lenscript 相机照片 EXIF 水印示例：奶油底签样式，Sony α7C II 机型、镜头、拍摄参数、日期署名与品牌 Logo">

</div>

不覆盖输入文件、不降低输出分辨率：JPEG 以质量 100 + 4:4:4 重编码，PNG 像素无损。
功能对标 [Semi-Utils](https://github.com/leslievan/semi-utils)，但用**一套纯 Rust 引擎驱动多个客户端**。

> 一套引擎（`lenscript-core`，无 OS 依赖、资产内嵌、可编译到 native / wasm / 移动端）
> + 多个薄客户端。核心只有一份，各端只是展示/布局不同。

🌐 **无需安装，浏览器直接用：[mark.lenscript.cn](https://mark.lenscript.cn)**（照片全程在本地处理，不上传服务器）

## 样式一览（24 套内置，同一张照片真实渲染）

| | | |
|:---:|:---:|:---:|
| <img src="docs/assets/styles/standard-watermark.jpg" alt="照片水印样式：标准水印，机型/镜头/参数/时间+品牌Logo底栏"> **标准水印** | <img src="docs/assets/styles/standard-watermark-2.jpg" alt="照片水印样式：标准水印2，圆角阴影留白社交分享风"> **标准水印2** | <img src="docs/assets/styles/cream-caption.jpg" alt="照片水印样式：奶油底签，奶油色底栏机型镜头参数日期署名"> **奶油底签** |
| <img src="docs/assets/styles/midnight-gold.jpg" alt="照片水印样式：黑金夜行，夜景街拍黑金底栏"> **黑金夜行** | <img src="docs/assets/styles/editorial-topline.jpg" alt="照片水印样式：极简顶栏，不裁切照片的克制顶栏"> **极简顶栏** | <img src="docs/assets/styles/technical-plate.jpg" alt="照片水印样式：技术铭牌，深色技术底栏曝光参数"> **技术铭牌** |
| <img src="docs/assets/styles/blurred-background.jpg" alt="照片水印样式：背景模糊，模糊背景居中相框"> **背景模糊** | <img src="docs/assets/styles/soft-focus.jpg" alt="照片水印样式：柔焦，圆角相卡浮于放大模糊背景"> **柔焦** | <img src="docs/assets/styles/bottom-right-parameters.jpg" alt="照片水印样式：右下角参数，极简直印"> **右下角参数** |
| <img src="docs/assets/styles/centered-logo.jpg" alt="照片水印样式：logo居中，中心品牌Logo相机信息"> **logo居中** | <img src="docs/assets/styles/dark-border.jpg" alt="照片水印样式：暗色边框，夜景街拍沉稳质感"> **暗色边框** | <img src="docs/assets/styles/polaroid.jpg" alt="照片水印样式：拍立得，白色留白底部题注相纸风"> **拍立得** |
| <img src="docs/assets/styles/black-gallery.jpg" alt="照片水印样式：黑框画廊，黑色画廊卡纸作品集"> **黑框画廊** | <img src="docs/assets/styles/minimal.jpg" alt="照片水印样式：简约，轻量字体大留白"> **简约** | <img src="docs/assets/styles/film-stamp.jpg" alt="照片水印样式：胶片，右下角橙色胶片戳日期"> **胶片** |
| <img src="docs/assets/styles/magazine.jpg" alt="照片水印样式：杂志，极简底栏大留白杂志封面"> **杂志** | <img src="docs/assets/styles/centered-caption.jpg" alt="照片水印样式：居中题注，白色相框画廊标签"> **居中题注** | <img src="docs/assets/styles/dark-polaroid.jpg" alt="照片水印样式：暗色拍立得，暖调深色相纸复古胶片"> **暗色拍立得** |
| <img src="docs/assets/styles/floating-label.jpg" alt="照片水印样式：浮签，左下角浮签式淡字直印"> **浮签** | <img src="docs/assets/styles/corner-label.jpg" alt="照片水印样式：角标，左上角机型日期小字"> **角标** | <img src="docs/assets/styles/minimal-centered.jpg" alt="照片水印样式：极简中置，品牌Logo机型居中白字"> **极简中置** |
| <img src="docs/assets/styles/centered-two-line.jpg" alt="照片水印样式：中置双行，Logo机型参数双行居中"> **中置双行** | <img src="docs/assets/styles/kodak-35mm-film.jpg" alt="照片水印样式：柯达胶片，135胶片条齿孔柯达黄"> **柯达胶片** | <img src="docs/assets/styles/medium-format-film.jpg" alt="照片水印样式：中画幅胶片，120圆角黑框竖排KODAK帧号"> **中画幅胶片** |

> 展示图为压缩预览；实际导出为全分辨率原质量。样张由 CLI 用同一张测试照片真实渲染生成。

## 状态（诚实）

| 平台 | 状态 |
|---|---|
| Linux / Windows / macOS 桌面（Tauri） | ✅ 可构建（CI 出安装包）；Linux 本机构建验证过 |
| Android | ✅ CI 可出测试签名 APK；正式发布签名需配置稳定 keystore secrets |
| Web（浏览器 WebAssembly，无需安装） | ✅ 可用：[mark.lenscript.cn](https://mark.lenscript.cn) |
| 本地网页应用（原生小服务） | ✅ 可用 |
| CLI | ✅ 可用 |
| iOS | ⏳ 计划中（需 Mac/CI，暂无工程） |

引擎的可移植性（可编译到 wasm32）由 CI 守卫；**已出货 5 端，iOS 待做**。详见
[`STATUS.md`](STATUS.md)。当前稳定版本与变更记录见 [`CHANGELOG.md`](CHANGELOG.md)。

## 亮点

- **保真是底线**：导出 JPEG 恒质量 100 + 4:4:4（无色度下采样）或 PNG 无损；**分辨率永不下采样**。
  JPEG 保留清理后的 EXIF、ICC 与 XMP；PNG 写回清理后的机型、镜头、光圈、快门、ISO、焦距、
  日期、方向和最终像素尺寸。GPS 默认移除，保护隐私。预览才用缩略图提速。
  详见 [`docs/FIDELITY.md`](docs/FIDELITY.md)。
- **24 套稳定内置模板**（集中在 `lenscript-core` 单一注册表，各端共用）；可移动信息只提供
  顶部/底部，保留样式原有水平锚点，不再使用容易误触和遮挡的九宫格。
- **品牌 Logo**：34 条目录（29 个相机 + 手机厂商真实 logo，透明背景，另含小米×徕卡等 5 组联名标），按 EXIF 自动匹配 + 手动选择 + 自定义上传。
- **机型美化**：把 EXIF 生涩代号（`ILCE-7CM2`）显示成厂商官方写法（`Sony α7C II`；尼康 Z 用双线 ℤ 字标）——
  数据经 ExifTool 源码 + 厂商核实，见 [`docs/CAMERA-MODELS.md`](docs/CAMERA-MODELS.md)，且**运行时可自行扩展**（[`docs/CONFIG.md`](docs/CONFIG.md)）。
- **署名/作者**（© 可开关）、逐照片机型兜底、明确的样式能力提示；桌面文件夹批处理会先复核
  来源与保存位置，多图导出只选择一次目录、重名不覆盖。
- 离线 **Free/Pro 授权**基座（Ed25519 签名，引擎不感知授权）——已就绪但当前不设门禁，见 [`docs/MONETIZATION.md`](docs/MONETIZATION.md)。
- **匿名使用统计默认开启**（opt-out，可随时在设置里关闭）：仅发送功能使用计数，照片、文件名与拍摄
  信息永不上传，客户端不存任何设备标识；事件白名单公开在 [`docs/ANALYTICS.md`](docs/ANALYTICS.md)。

## 快速开始

前置：Rust（`rustup`）。WSL 下构建 `cc` 需 `export PATH="/usr/bin:$PATH"`。

```bash
# 查看稳定样式 ID，再按 ID 渲染；安装后的 CLI 不依赖仓库模板文件
cargo run --locked --release -p lenscript-cli -- templates
cargo run --locked --release -p lenscript-cli -- render path/to/photo.jpg \
  --style standard-watermark -o out.jpg -a "你的署名"
# 文件夹批处理
cargo run --locked --release -p lenscript-cli -- batch path/to/input-dir \
  --style standard-watermark -o path/to/output-dir
# 自定义 JSON 改用互斥的 --template path/to/template.json

# 本地网页应用：启动后浏览器打开 http://127.0.0.1:8787
cargo run --locked --release -p lenscript-web

# 浏览器 (WebAssembly) 网页端：构建后用任意静态服务器托管 web/
bash scripts/build-web.sh            # 需 wasm-pack；构建 + 部署到 web/pkg + 导出守卫
python3 -m http.server -d web 8080   # 然后打开 http://127.0.0.1:8080

# 桌面 app（Tauri）：需 cargo install tauri-cli
cd crates/lenscript-desktop && cargo run                 # 开发运行（WSL 需 GDK_BACKEND=x11）
cargo tauri build                                        # 出原生安装包
# Android / Windows / macOS 安装包见 CI（.github/workflows/build-*.yml，tag/dispatch 触发）
# 及 docs/BUILD-ANDROID.md / docs/BUILD-WINDOWS.md
```

## 仓库结构

- `crates/lenscript-core` — **核心引擎**（EXIF / 模板 pipeline / 文字与 logo 渲染 / 保真编码）；可编译到 native / wasm。
- `crates/lenscript-cli` — 无 GUI 驱动（二进制名 `lenscript`），渲染 / 批处理 / 验收。
- `crates/lenscript-web` — 本地网页应用（`tiny_http` 小服务，拖照片→选模板→预览下载）。
- `crates/lenscript-wasm` — 浏览器（WebAssembly）绑定层（独立 workspace）。
- `crates/lenscript-desktop` — Tauri 桌面 + Android 外壳（独立 workspace）。
- `crates/lenscript-license` — 离线 Ed25519 授权（仅验签默认编入，签名走 `sign` feature）。
- `web/` — 部署用的 wasm 网页应用静态页（`web/pkg` 由 `scripts/build-web.sh` 生成，已 gitignore）。
- `scripts/` — Web 构建、版本一致性、稳定制品打包与导出同步守卫。
- `deploy/` — Caddy 配置与“GitHub Release → 生产服务器”部署脚本；服务器全景图见
  [`deploy/SERVER-OVERVIEW.md`](deploy/SERVER-OVERVIEW.md)，从零部署的可粘贴步骤见
  [`deploy/QUICKSTART.md`](deploy/QUICKSTART.md)。
- `docs/` — 架构 / 验收 / 保真 / 配置 / 机型规范 / 商业化；[`STATUS.md`](STATUS.md) 只记录当前事实。
- [`docs/STYLE-CATALOG.md`](docs/STYLE-CATALOG.md) — 样式 ID、家族/变体、候选晋级和真实渲染矩阵制度。
- [`AGENTS.md`](AGENTS.md) — AI/新维护者强制入口；分支、敏感信息和交接红线。
- [`docs/INSTALLATION.md`](docs/INSTALLATION.md) — 新机器环境、多端构建和服务器迁移完整手册。

## 版本与发布

任何修复或新需求都必须先从稳定 `master` 创建 `fix/`、`feature/` 或 `docs/` 分支，通过 PR 和
CI 后才考虑合并；禁止直接在 `master` 开发或推送。完整制度见
[`docs/DEVELOPMENT.md`](docs/DEVELOPMENT.md)。

应用版本以根 `Cargo.toml` 为准，WASM、Desktop、桌面插件和 Tauri 清单必须保持一致：

```bash
bash scripts/check-version.sh
```

稳定版本要求使用禁止移动的 annotated `vX.Y.Z` tag。Tag 工作流会从精确 commit 生成
GitHub Release 网页归档、manifest 和 SHA-256；生产服务器只下载并校验该 Release，不接收本地
上传、不部署 `master`、不保留旧代码。完整流程见 [`deploy/SERVER.md`](deploy/SERVER.md)。

首次安装、Linux/Windows/macOS/Android/WebAssembly 的精确环境和产物位置见
[`docs/INSTALLATION.md`](docs/INSTALLATION.md)；GitHub 管理员一次性设置见
[`docs/GITHUB-ADMIN.md`](docs/GITHUB-ADMIN.md)。

## 工程质量门（每次提交前）

根 workspace、独立 WASM、独立 Desktop、wasm32 可移植构建及 `cargo-deny` 必须全绿；
库生产路径不以 `unwrap/panic` 处理不可信输入。详见 [`docs/ACCEPTANCE.md`](docs/ACCEPTANCE.md)。

## 交流与支持

镜笺由一名热爱摄影的学生独立开发和维护。

- **QQ 交流群：824558022** —— 交流反馈、问题排查、样片共创，欢迎加入。
- **在线使用 / 支持入口：[mark.lenscript.cn](https://mark.lenscript.cn)**
- 觉得好用请点一个 ⭐ **Star**——这是对独立开发者最直接的支持，也能让更多摄影爱好者发现镜笺。

项目会继续免费使用；如果镜笺曾帮你更体面地分享一张照片，可自愿打赏支持服务器、
域名、测试设备和多平台适配成本。支持不影响任何功能，未成年人请先征得监护人同意。

| 微信打赏 | 支付宝打赏 |
|:---:|:---:|
| <img src="web/support/wechat.jpg" width="180" alt="微信打赏二维码"> | <img src="web/support/alipay.jpg" width="180" alt="支付宝打赏二维码"> |

## 致谢

- **[Semi-Utils](https://github.com/leslievan/semi-utils)**（Apache-2.0）——本项目的功能蓝本与出发点，感谢
  leslievan 与全体贡献者的开创性工作。
- **Rust 生态**：[`image`](https://github.com/image-rs/image)、[`minijinja`](https://github.com/mitsuhiko/minijinja)、
  [`Tauri`](https://tauri.app)、[`wasm-bindgen` / `wasm-pack`](https://rustwasm.github.io) 等优秀开源项目
  （完整清单见 [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md)）。
- **字体**：阿里巴巴普惠体 2.0、Roboto、DejaVu Sans（许可与子集化说明见 NOTICE / THIRD_PARTY_LICENSES）。
- **QQ 群的每一位测试者与样片提供者**——真实设备上的每一条反馈都让镜笺更接近"能用"到"好用"。

## 许可

源码为 **Apache-2.0 衍生**（基于 Semi-Utils，Apache-2.0）；完整条款见 [`LICENSE`](LICENSE)，
主要第三方依赖与资产许可见 [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md)，归属说明见
[`NOTICE`](NOTICE)。已编译的应用另含 Free/Pro 授权基座（见 [`docs/MONETIZATION.md`](docs/MONETIZATION.md)）。
品牌 logo 为各自商标，仅用于标注照片来源，商用前请自行核实再分发权（NOTICE §logos）。
商标、字体商用/再分发及启用 HEIC 时的 LGPL 履约，发布前仍需专业法律审查。
