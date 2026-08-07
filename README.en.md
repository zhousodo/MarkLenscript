<div align="center">

# Lenscript (镜笺)

**Cross-platform photo EXIF watermark & frame tool — 26 styles, one pure-Rust engine, 5 clients**

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![Website](https://img.shields.io/badge/try%20it%20online-mark.lenscript.cn-brightgreen)](https://mark.lenscript.cn)
[![QQ Group](https://img.shields.io/badge/QQ%20Group-824558022-12B7F5)](#community--support)

**中文版说明请看 [README.md](README.md)**

**This is the showcase repository** (README and images only, no source code).
Source code lives at **[github.com/zhousodo/lenscript](https://github.com/zhousodo/lenscript)**.

**Try it online: [mark.lenscript.cn](https://mark.lenscript.cn)**

<img src="images/hero.jpg" width="640" alt="Lenscript photo EXIF watermark example: cream caption style with Sony a7C II camera model, lens, exposure parameters, date, signature and brand logo">

</div>

## What it does

Lenscript stamps your photos with a good-looking EXIF info bar or frame — camera model,
lens, aperture/shutter/ISO, timestamp, your signature, and a brand logo. 24 built-in
styles, all driven by one pure-Rust engine. It never overwrites your source file and
never downscales the output: JPEG is re-encoded at quality 100 with 4:4:4 (no chroma
subsampling), PNG is pixel-lossless.

Feature-comparable to [Semi-Utils](https://github.com/leslievan/semi-utils), built as a
Rust rewrite with more styles and multi-platform support (Apache-2.0).

## Five clients, one engine

- **Browser (WebAssembly)** — nothing to install, just open **[mark.lenscript.cn](https://mark.lenscript.cn)**
- **Desktop app** (Windows / macOS / Linux, built with Tauri)
- **Local web app** — start a small local server and use it from your browser
- **Command-line tool** — batch processing and scripting
- **Android**

All five share the same rendering engine and style catalog. Same output, different
interfaces.

## Your photos never leave your device

**Nothing is uploaded.** Browser, desktop, or CLI — every client renders locally, and no
photo ever touches a server. GPS location data is stripped from the output by default.

Lenscript includes **anonymous usage statistics, on by default and switchable off in
settings**: only feature-usage counts are sent. Never photos, filenames, or shooting
metadata, and no device identifier is stored on your machine.

## Style gallery (26 built-in styles, all rendered from the same test photo)

| | | |
|:---:|:---:|:---:|
| <img src="images/styles/standard-watermark.jpg" alt="photo watermark style: standard watermark bar with camera model, lens, exposure and brand logo"> **Standard** | <img src="images/styles/standard-watermark-2.jpg" alt="photo watermark style: rounded corners, shadow and padding for social sharing"> **Standard 2** | <img src="images/styles/cream-caption.jpg" alt="photo watermark style: cream caption bar with model, lens, parameters, date and signature"> **Cream Caption** |
| <img src="images/styles/midnight-gold.jpg" alt="photo watermark style: midnight gold bar for night street photography"> **Midnight Gold** | <img src="images/styles/editorial-topline.jpg" alt="photo watermark style: restrained editorial top bar, photo never cropped"> **Editorial Topline** | <img src="images/styles/technical-plate.jpg" alt="photo watermark style: dark technical plate with exposure parameters"> **Technical Plate** |
| <img src="images/styles/blurred-background.jpg" alt="photo watermark style: blurred background with centered frame"> **Blurred Background** | <img src="images/styles/soft-focus.jpg" alt="photo watermark style: rounded photo card floating on an enlarged blurred backdrop"> **Soft Focus** | <img src="images/styles/bottom-right-parameters.jpg" alt="photo watermark style: minimal parameters printed at the bottom right corner"> **Corner Parameters** |
| <img src="images/styles/centered-logo.jpg" alt="photo watermark style: centered brand logo with camera info"> **Centered Logo** | <img src="images/styles/dark-border.jpg" alt="photo watermark style: dark border with white text for night scenes"> **Dark Border** | <img src="images/styles/polaroid.jpg" alt="photo watermark style: polaroid paper with white margins and bottom caption"> **Polaroid** |
| <img src="images/styles/black-gallery.jpg" alt="photo watermark style: black gallery mat with white text, portfolio look"> **Black Gallery** | <img src="images/styles/minimal.jpg" alt="photo watermark style: light typeface with generous whitespace"> **Minimal** | <img src="images/styles/film-stamp.jpg" alt="photo watermark style: orange film date stamp at the bottom right"> **Film Stamp** |
| <img src="images/styles/magazine.jpg" alt="photo watermark style: minimal bar with generous whitespace, magazine cover look"> **Magazine** | <img src="images/styles/centered-caption.jpg" alt="photo watermark style: white frame with centered caption like a gallery label"> **Centered Caption** | <img src="images/styles/dark-polaroid.jpg" alt="photo watermark style: warm dark polaroid paper with cream text, vintage film mood"> **Dark Polaroid** |
| <img src="images/styles/floating-label.jpg" alt="photo watermark style: floating label printed subtly at the bottom left"> **Floating Label** | <img src="images/styles/corner-label.jpg" alt="photo watermark style: small model and date label at the top left corner"> **Corner Label** | <img src="images/styles/minimal-centered.jpg" alt="photo watermark style: brand logo and model centered at the photo bottom"> **Minimal Centered** |
| <img src="images/styles/centered-two-line.jpg" alt="photo watermark style: logo and model on one line, parameters on the second, centered"> **Two-Line Centered** | <img src="images/styles/kodak-35mm-film.jpg" alt="photo watermark style: 35mm film strip with sprocket holes and Kodak yellow edge print"> **Kodak 35mm Film** | <img src="images/styles/medium-format-film.jpg" alt="photo watermark style: 120 medium format rounded black frame with vertical KODAK edge and frame number"> **Medium Format Film** |
| <img src="images/styles/minimal-zine.jpg" alt="photo watermark style: indie zine poster layout with oversized camera model and vermilion block"> **Minimal Zine** | <img src="images/styles/zine-cutout.jpg" alt="photo watermark style: small letterpressed paper card at the lower left with a vermilion index bar"> **Paper Cut-Out** | |

> Gallery images are compressed previews; actual exports are full-resolution at original
> quality. All samples were rendered by the CLI from the same test photo.

## Try it online

**[mark.lenscript.cn](https://mark.lenscript.cn)** — open it in any browser, no install
needed. Your photos are processed inside your own browser and never leave your device.

## Community & support

Lenscript is built and maintained by a single student who loves photography.

- **QQ group: 824558022** — questions, feedback, troubleshooting, and sample sharing.
- If you find it useful, please star the source repository
  [github.com/zhousodo/lenscript](https://github.com/zhousodo/lenscript) ⭐ — that is the
  most direct way to support an independent developer.

The project stays free to use. If Lenscript ever helped you share a photo you were proud
of, an optional tip helps cover servers, domains, test devices, and multi-platform work.
Tipping unlocks nothing — every feature stays available either way. Minors should ask a
guardian first.

<div align="center">

| WeChat | Alipay |
|:---:|:---:|
| <img src="support/wechat.jpg" width="180" alt="WeChat tipping QR code"> | <img src="support/alipay.jpg" width="180" alt="Alipay tipping QR code"> |

</div>

## Acknowledgements

**[Semi-Utils](https://github.com/leslievan/semi-utils)** (Apache-2.0) — the blueprint and
starting point for this project. Thanks to leslievan and every contributor for the
groundwork.

## About this repository

This repository is the user-facing showcase for Lenscript: README and images only,
**no source code**. Source code, development docs, and engineering details all live at
**[github.com/zhousodo/lenscript](https://github.com/zhousodo/lenscript)**.

Lenscript is an Apache-2.0 derivative work (based on Semi-Utils, Apache-2.0); full license
terms are in the source repository. The text and images in this showcase repository are
likewise provided under the [Apache-2.0 license](LICENSE). Brand logos are trademarks of
their respective owners, used here only to illustrate output, and do not imply any
affiliation or endorsement.
