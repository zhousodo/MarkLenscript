<div align="center">

# Lenscript (镜笺)

**Cross-platform photo EXIF watermark / frame tool — 24 styles, one pure-Rust engine driving 5 clients**

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![Release](https://img.shields.io/github/v/release/zhousodo/lenscript)](https://github.com/zhousodo/lenscript/releases)
[![Website](https://img.shields.io/badge/try%20online-mark.lenscript.cn-brightgreen)](https://mark.lenscript.cn)
[![QQ Group](https://img.shields.io/badge/QQ%20Group-824558022-12B7F5)](#community--support)

[简体中文](README.md) | **[English](README.en.md)**

<img src="docs/assets/hero.jpg" width="640" alt="Lenscript camera photo EXIF watermark example: cream caption style with Sony α7C II camera model, lens, exposure parameters, date, signature and brand logo">

</div>

Never overwrites your input files, never downscales your output: JPEG is re-encoded at
quality 100 with 4:4:4 (no chroma subsampling), PNG is pixel-lossless.
Feature-comparable to [Semi-Utils](https://github.com/leslievan/semi-utils), but built as
**one pure-Rust engine driving multiple thin clients**.

> One engine (`lenscript-core` — no OS dependencies, embedded assets, compiles to
> native / wasm / mobile) + several thin clients. There is exactly one core; the clients
> only differ in presentation.

🌐 **No install needed — use it right in your browser: [mark.lenscript.cn](https://mark.lenscript.cn)**
(photos are processed entirely on your device, never uploaded).

## Style gallery (24 built-in styles, all rendered from the same test photo)

| | | |
|:---:|:---:|:---:|
| <img src="docs/assets/styles/standard-watermark.jpg" alt="photo watermark style: standard watermark bar with camera model, lens, exposure and brand logo"> **Standard** | <img src="docs/assets/styles/standard-watermark-2.jpg" alt="photo watermark style: rounded corners, shadow and padding for social sharing"> **Standard 2** | <img src="docs/assets/styles/cream-caption.jpg" alt="photo watermark style: cream caption bar with model, lens, parameters, date and signature"> **Cream Caption** |
| <img src="docs/assets/styles/midnight-gold.jpg" alt="photo watermark style: midnight gold bar for night street photography"> **Midnight Gold** | <img src="docs/assets/styles/editorial-topline.jpg" alt="photo watermark style: restrained editorial top bar, photo never cropped"> **Editorial Topline** | <img src="docs/assets/styles/technical-plate.jpg" alt="photo watermark style: dark technical plate with exposure parameters"> **Technical Plate** |
| <img src="docs/assets/styles/blurred-background.jpg" alt="photo watermark style: blurred background with centered frame"> **Blurred Background** | <img src="docs/assets/styles/soft-focus.jpg" alt="photo watermark style: rounded photo card floating on an enlarged blurred backdrop"> **Soft Focus** | <img src="docs/assets/styles/bottom-right-parameters.jpg" alt="photo watermark style: minimal parameters printed at the bottom right corner"> **Corner Parameters** |
| <img src="docs/assets/styles/centered-logo.jpg" alt="photo watermark style: centered brand logo with camera info"> **Centered Logo** | <img src="docs/assets/styles/dark-border.jpg" alt="photo watermark style: dark border with white text for night scenes"> **Dark Border** | <img src="docs/assets/styles/polaroid.jpg" alt="photo watermark style: polaroid paper with white margins and bottom caption"> **Polaroid** |
| <img src="docs/assets/styles/black-gallery.jpg" alt="photo watermark style: black gallery mat with white text, portfolio look"> **Black Gallery** | <img src="docs/assets/styles/minimal.jpg" alt="photo watermark style: light typeface with generous whitespace"> **Minimal** | <img src="docs/assets/styles/film-stamp.jpg" alt="photo watermark style: orange film date stamp at the bottom right"> **Film Stamp** |
| <img src="docs/assets/styles/magazine.jpg" alt="photo watermark style: minimal bar with generous whitespace, magazine cover look"> **Magazine** | <img src="docs/assets/styles/centered-caption.jpg" alt="photo watermark style: white frame with centered caption like a gallery label"> **Centered Caption** | <img src="docs/assets/styles/dark-polaroid.jpg" alt="photo watermark style: warm dark polaroid paper with cream text, vintage film mood"> **Dark Polaroid** |
| <img src="docs/assets/styles/floating-label.jpg" alt="photo watermark style: floating label printed subtly at the bottom left"> **Floating Label** | <img src="docs/assets/styles/corner-label.jpg" alt="photo watermark style: small model and date label at the top left corner"> **Corner Label** | <img src="docs/assets/styles/minimal-centered.jpg" alt="photo watermark style: brand logo and model centered at the photo bottom"> **Minimal Centered** |
| <img src="docs/assets/styles/centered-two-line.jpg" alt="photo watermark style: logo and model on one line, parameters on the second, centered"> **Two-Line Centered** | <img src="docs/assets/styles/kodak-35mm-film.jpg" alt="photo watermark style: 35mm film strip with sprocket holes and Kodak yellow edge print"> **Kodak 35mm Film** | <img src="docs/assets/styles/medium-format-film.jpg" alt="photo watermark style: 120 medium format rounded black frame with vertical KODAK edge and frame number"> **Medium Format Film** |

> Gallery images are compressed previews; actual exports are full-resolution at original quality.
> All samples were rendered by the CLI from the same test photo.

## Status (honest)

| Platform | Status |
|---|---|
| Linux / Windows / macOS desktop (Tauri) | ✅ Builds (CI produces installers); Linux build verified locally |
| Android | ✅ CI produces test-signed APKs; production signing needs stable keystore secrets |
| Web (browser WebAssembly, no install) | ✅ Live at [mark.lenscript.cn](https://mark.lenscript.cn) |
| Local web app (tiny native server) | ✅ Working |
| CLI | ✅ Working |
| iOS | ⏳ Planned (needs Mac/CI; no project yet) |

Engine portability (wasm32 target) is guarded by CI; **5 clients shipped, iOS pending**.
See [`STATUS.md`](STATUS.md) and [`CHANGELOG.md`](CHANGELOG.md) (Chinese).

## Highlights

- **Fidelity first**: exports are JPEG quality 100 + 4:4:4 (no chroma subsampling) or lossless PNG;
  **resolution is never downscaled**. JPEG keeps sanitized EXIF, ICC and XMP; PNG writes back
  sanitized camera model, lens, aperture, shutter, ISO, focal length, date, orientation and final
  pixel dimensions. GPS is stripped by default for privacy. Thumbnails are used for previews only.
  Details: [`docs/FIDELITY.md`](docs/FIDELITY.md).
- **24 stable built-in templates**, registered once in `lenscript-core` and shared by every client.
- **Brand logos**: a 34-entry catalog (29 real camera + smartphone maker logos with transparent
  backgrounds, plus 5 co-brand marks like Xiaomi × Leica), auto-matched from EXIF, manually
  selectable, or custom-uploaded.
- **Model prettifying**: raw EXIF codes (`ILCE-7CM2`) are displayed the way vendors write them
  (`Sony α7C II`; Nikon Z gets the double-struck ℤ mark) — data verified against ExifTool sources
  and vendor pages, see [`docs/CAMERA-MODELS.md`](docs/CAMERA-MODELS.md), and extensible at
  runtime ([`docs/CONFIG.md`](docs/CONFIG.md)).
- **Signature/author** (© toggleable), per-photo model fallback for stripped EXIF, explicit
  per-style capability hints; desktop folder batch double-checks source and destination,
  multi-photo export picks the directory once and never overwrites on name clashes.
- Offline **Free/Pro licensing** foundation (Ed25519 signatures, engine is license-agnostic) —
  ready but currently ungated, see [`docs/MONETIZATION.md`](docs/MONETIZATION.md).
- **Anonymous usage statistics are on by default** (opt-out — turn them off anytime in settings): only feature
  usage counts are sent — photos, filenames, and shooting metadata never leave your device,
  and no device identifier is stored; the event whitelist is public in
  [`docs/ANALYTICS.md`](docs/ANALYTICS.md).

## Quick start

Prerequisite: Rust (`rustup`). On WSL, `cc` needs `export PATH="/usr/bin:$PATH"`.

```bash
# List stable style IDs, then render by ID; the installed CLI does not depend on repo files
cargo run --locked --release -p lenscript-cli -- templates
cargo run --locked --release -p lenscript-cli -- render path/to/photo.jpg \
  --style standard-watermark -o out.jpg -a "Your Name"
# Folder batch
cargo run --locked --release -p lenscript-cli -- batch path/to/input-dir \
  --style standard-watermark -o path/to/output-dir
# Custom JSON templates use the mutually-exclusive --template path/to/template.json

# Local web app: open http://127.0.0.1:8787 after starting
cargo run --locked --release -p lenscript-web

# Browser (WebAssembly) build: host web/ with any static server afterwards
bash scripts/build-web.sh            # needs wasm-pack
python3 -m http.server -d web 8080   # then open http://127.0.0.1:8080

# Desktop app (Tauri): needs cargo install tauri-cli
cd crates/lenscript-desktop && cargo run   # dev run (WSL needs GDK_BACKEND=x11)
cargo tauri build                          # native installers
# Android / Windows / macOS installers: see CI (.github/workflows/build-*.yml)
```

## Repository layout

- `crates/lenscript-core` — **the engine** (EXIF / template pipeline / text & logo rendering /
  fidelity encoding); compiles to native and wasm.
- `crates/lenscript-cli` — headless driver (binary `lenscript`): render / batch / acceptance.
- `crates/lenscript-web` — local web app (`tiny_http` server: drop photo → pick style → download).
- `crates/lenscript-wasm` — browser (WebAssembly) bindings (separate workspace).
- `crates/lenscript-desktop` — Tauri desktop + Android shell (separate workspace).
- `crates/lenscript-license` — offline Ed25519 licensing (verify-only by default).
- `web/` — static page for the wasm web app (`web/pkg` built by `scripts/build-web.sh`).
- `deploy/` — Caddy config and the "GitHub Release → production server" deploy script.
- `docs/` — architecture / acceptance / fidelity / config / camera-model conventions (Chinese).
- [`AGENTS.md`](AGENTS.md) — mandatory entry point for AI agents and new maintainers.

## Engineering quality gates

Root workspace, standalone WASM and Desktop workspaces, the wasm32 portability build and
`cargo-deny` must all be green; production paths never `unwrap`/`panic` on untrusted input.
See [`docs/ACCEPTANCE.md`](docs/ACCEPTANCE.md). Stable releases are immutable annotated
`vX.Y.Z` tags; the production server only deploys verified GitHub Release artifacts
([`deploy/SERVER.md`](deploy/SERVER.md)).

## Community & support

Lenscript is developed and maintained by a single student who loves photography.

- **QQ group: 824558022** — feedback, troubleshooting and sample-photo co-creation welcome.
- **Try online / support page: [mark.lenscript.cn](https://mark.lenscript.cn)**
- If you find it useful, please leave a ⭐ **Star** — the most direct support for an independent
  developer, and it helps more photographers discover Lenscript.

The project stays free to use. If Lenscript ever helped you share a photo more gracefully, you
can voluntarily tip to cover servers, domain, test devices and multi-platform costs. Tipping
never affects features; minors please ask a guardian first.

| WeChat tip | Alipay tip |
|:---:|:---:|
| <img src="web/support/wechat.jpg" width="180" alt="WeChat tipping QR code"> | <img src="web/support/alipay.jpg" width="180" alt="Alipay tipping QR code"> |

## Acknowledgements

- **[Semi-Utils](https://github.com/leslievan/semi-utils)** (Apache-2.0) — the functional
  blueprint and starting point of this project. Thanks to leslievan and all contributors for
  their pioneering work.
- **The Rust ecosystem**: [`image`](https://github.com/image-rs/image),
  [`minijinja`](https://github.com/mitsuhiko/minijinja), [`Tauri`](https://tauri.app),
  [`wasm-bindgen` / `wasm-pack`](https://rustwasm.github.io) and many more
  (full list in [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md)).
- **Fonts**: Alibaba PuHuiTi 2.0, Roboto, DejaVu Sans (licensing and subsetting notes in
  NOTICE / THIRD_PARTY_LICENSES).
- **Every tester and sample contributor in the QQ group** — real-device feedback is what moved
  Lenscript from "works" to "works well".

## License

Source code is an **Apache-2.0 derivative** (based on Semi-Utils, Apache-2.0); full terms in
[`LICENSE`](LICENSE), third-party dependency and asset licenses in
[`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md), attribution in [`NOTICE`](NOTICE).
Brand logos are trademarks of their respective owners, used only to indicate the camera that
took a photo; verify redistribution rights before commercial use (NOTICE §logos).
