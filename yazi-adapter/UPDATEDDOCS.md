# yazi-adapter — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Image/preview adapter backends (sixel, kitty, iterm2, etc.) for inline previews in the terminal.

> Cargo description: *Yazi image adapter*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-adapter`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 13 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-config`
- `yazi-emulator`
- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-tty`

### External (sample)

`ansi-to-tui`, `anyhow`, `base64`, `image`, `moxcms`, `palette`, `quantette`, `ratatui`, `strum`, `tokio`, `tracing`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/adapter` |
| module/file | `src/adapters` |
| module/file | `src/drivers` |
| module/file | `src/icc` |
| module/file | `src/image` |
| module/file | `src/info` |
| module/file | `src/lib.rs` |

### Notable source files

- `src/adapter.rs`
- `src/adapters.rs`
- `src/drivers/chafa.rs`
- `src/drivers/iip.rs`
- `src/drivers/kgp.rs`
- `src/drivers/kgp_old.rs`
- `src/drivers/mod.rs`
- `src/drivers/sixel.rs`
- `src/drivers/ueberzug.rs`
- `src/icc.rs`
- `src/image.rs`
- `src/info.rs`
- `src/lib.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `enum` | `Adapter` | `src/adapter.rs` |
| `fn` | `image_show` | `src/adapter.rs` |
| `fn` | `image_hide` | `src/adapter.rs` |
| `fn` | `image_erase` | `src/adapter.rs` |
| `fn` | `shown_load` | `src/adapter.rs` |
| `fn` | `shown_store` | `src/adapter.rs` |
| `fn` | `start` | `src/adapter.rs` |
| `fn` | `needs_ueberzug` | `src/adapter.rs` |
| `fn` | `matches` | `src/adapter.rs` |
| `struct` | `Adapters` | `src/adapters.rs` |
| `struct` | `Chafa` | `src/drivers/chafa.rs` |
| `struct` | `Iip` | `src/drivers/iip.rs` |
| `struct` | `Kgp` | `src/drivers/kgp.rs` |
| `struct` | `KgpOld` | `src/drivers/kgp_old.rs` |
| `struct` | `Sixel` | `src/drivers/sixel.rs` |
| `struct` | `Ueberzug` | `src/drivers/ueberzug.rs` |
| `fn` | `supported_compositor` | `src/drivers/ueberzug.rs` |
| `struct` | `Icc` | `src/icc.rs` |
| `fn` | `transform` | `src/icc.rs` |
| `struct` | `Image` | `src/image.rs` |
| `fn` | `precache` | `src/image.rs` |
| `fn` | `downscale` | `src/image.rs` |
| `fn` | `max_pixel` | `src/image.rs` |
| `fn` | `pixel_area` | `src/image.rs` |
| `type` | `ImageFormat` | `src/info.rs` |
| `type` | `ImageColor` | `src/info.rs` |
| `type` | `ImageOrientation` | `src/info.rs` |
| `struct` | `ImageInfo` | `src/info.rs` |
| `fn` | `new` | `src/info.rs` |
| `static` | `ADAPTOR` | `src/lib.rs` |
| `static` | `WSL` | `src/lib.rs` |
| `fn` | `init` | `src/lib.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(drivers);

yazi_macro::mod_flat!(adapter adapters icc image info);

use yazi_emulator::{Brand, CLOSE, EMULATOR, ESCAPE, Emulator, Mux, START, TMUX};
use yazi_shared::in_wsl;
use yazi_shim::cell::SyncCell;

pub static ADAPTOR: SyncCell<Adapter> = SyncCell::new(Adapter::Chafa);

// Image state
static SHOWN: SyncCell<Option<ratatui::layout::Rect>> = SyncCell::new(None);

// WSL support
pub static WSL: SyncCell<bool> = SyncCell::new(false);

pub fn init() -> anyhow::Result<()> {
	// WSL support
	WSL.set(in_wsl());

	// Emulator detection
	let mut emulator = Emulator::detect().unwrap_or_default();
	TMUX.set(emulator.kind.left() == Some(Brand::Tmux));

	// Tmux support
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-config`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

**Depended on by (workspace scan)**: `yazi-watcher`, `yazi-binding`, `yazi-widgets`, `yazi-core`, `yazi-plugin`, `yazi-fm`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-adapter`.*
