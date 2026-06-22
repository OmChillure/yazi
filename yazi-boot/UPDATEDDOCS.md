# yazi-boot — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Startup/boot orchestration: args, config paths, plugin preload, and early environment setup.

> Cargo description: *Yazi bootstrapper*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-boot`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `build.rs`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 5 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-version`
- `yazi-vfs`

### External (sample)

`clap`, `clap_complete`, `clap_complete_fig`, `clap_complete_nushell`, `futures`, `hashbrown`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/actions` |
| module/file | `src/args` |
| module/file | `src/boot` |
| module/file | `src/lib.rs` |

### Notable source files

- `src/actions/actions.rs`
- `src/actions/mod.rs`
- `src/args.rs`
- `src/boot.rs`
- `src/lib.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Actions` | `src/actions/actions.rs` |
| `fn` | `act` | `src/actions/actions.rs` |
| `struct` | `Args` | `src/args.rs` |
| `struct` | `Boot` | `src/boot.rs` |
| `static` | `ARGS` | `src/lib.rs` |
| `static` | `BOOT` | `src/lib.rs` |
| `fn` | `init` | `src/lib.rs` |
| `fn` | `init_default` | `src/lib.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(actions);

yazi_macro::mod_flat!(args boot);

use clap::Parser;
use yazi_shim::cell::RoCell;

pub static ARGS: RoCell<Args> = RoCell::new();
pub static BOOT: RoCell<Boot> = RoCell::new();

pub fn init() {
	ARGS.with(<_>::parse);
	BOOT.init(<_>::from(&*ARGS));

	actions::Actions::act(&ARGS);
}

pub fn init_default() {
	ARGS.with(<_>::default);
	BOOT.with(<_>::default);
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`, `yazi-vfs`

**Depended on by (workspace scan)**: `yazi-dds`, `yazi-parser`, `yazi-plugin`, `yazi-actor`, `yazi-fm`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-boot`.*
