# yazi-adapter

## Purpose

Renders preview images in the terminal via protocol-specific drivers (Kitty, iTerm2, Sixel, Überzug, Chafa) with ICC/color handling.

**Crate description (Cargo.toml):** Yazi image adapter

## Dependencies (workspace)

`yazi-config`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

## Module map

Public/internal modules exported from the crate root:

- `drivers`
- `adapter`
- `adapters`
- `icc`
- `image`
- `info`

## Main files

- `src/lib.rs` — entry/core
- `src/adapter.rs` (file)
- `src/adapters.rs` (file)
- `src/drivers` (dir)
- `src/icc.rs` (file)
- `src/image.rs` (file)
- `src/info.rs` (file)
- `src/lib.rs` (file)

## Key public items

- **src/adapter.rs**: `enum Adapter`
- **src/image.rs**: `struct Image`
- **src/info.rs**: `type ImageFormat`, `type ImageColor`, `type ImageOrientation`, `struct ImageInfo`
- **src/lib.rs**: `static ADAPTOR`, `static WSL`, `fn init`

## Source layout (partial)

```
src/adapter.rs
src/adapters.rs
src/drivers/chafa.rs
src/drivers/iip.rs
src/drivers/kgp.rs
src/drivers/kgp_old.rs
src/drivers/mod.rs
src/drivers/sixel.rs
src/drivers/ueberzug.rs
src/icc.rs
src/image.rs
src/info.rs
src/lib.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
