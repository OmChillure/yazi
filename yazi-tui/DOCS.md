# yazi-tui

## Purpose

Ratatui-oriented TUI building blocks and layout helpers specific to Yazi.

**Crate description (Cargo.toml):** Yazi terminal user interface

## Dependencies (workspace)

`yazi-config`, `yazi-emulator`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

## Module map

Public/internal modules exported from the crate root:

- `backend`
- `option`
- `raterm`
- `state`

## Main files

- `src/lib.rs` — entry/core
- `src/backend.rs` (file)
- `src/lib.rs` (file)
- `src/option.rs` (file)
- `src/raterm.rs` (file)
- `src/state.rs` (file)

## Key public items

- **src/backend.rs**: `struct RatermBackend`
- **src/raterm.rs**: `static STATE`, `struct Raterm`
- **src/state.rs**: `struct RatermState`

## Source layout (partial)

```
src/backend.rs
src/lib.rs
src/option.rs
src/raterm.rs
src/state.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
