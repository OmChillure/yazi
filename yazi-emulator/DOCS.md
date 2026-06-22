# yazi-emulator

## Purpose

Detects terminal emulator capabilities (graphics protocols, color, keyboard) for adapter and rendering choices.

**Crate description (Cargo.toml):** Yazi terminal emulator database

## Dependencies (workspace)

`yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

## Module map

Public/internal modules exported from the crate root:

- `brand`
- `dimension`
- `emulator`
- `mux`
- `unknown`

## Main files

- `src/lib.rs` — entry/core
- `src/brand.rs` (file)
- `src/dimension.rs` (file)
- `src/emulator.rs` (file)
- `src/lib.rs` (file)
- `src/mux.rs` (file)
- `src/unknown.rs` (file)

## Key public items

- **src/brand.rs**: `enum Brand`
- **src/dimension.rs**: `struct Dimension`
- **src/emulator.rs**: `static EMULATOR`, `struct Emulator`
- **src/mux.rs**: `static TMUX`, `static ESCAPE`, `static START`, `static CLOSE`, `struct Mux`
- **src/unknown.rs**: `struct Unknown`

## Source layout (partial)

```
src/brand.rs
src/dimension.rs
src/emulator.rs
src/lib.rs
src/mux.rs
src/unknown.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
