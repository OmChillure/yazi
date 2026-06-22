# yazi-tty

## Purpose

Low-level TTY access: alternate screen, stdin/stdout handles, terminal mode control.

**Crate description (Cargo.toml):** Yazi TTY access layer

## Dependencies (workspace)

`yazi-macro`, `yazi-shim`

## Module map

Public/internal modules exported from the crate root:

- `handle`
- `reader`
- `tty`
- `writer`

## Main files

- `src/lib.rs` — entry/core
- `src/handle.rs` (file)
- `src/lib.rs` (file)
- `src/reader.rs` (file)
- `src/tty.rs` (file)
- `src/writer.rs` (file)

## Key public items

- **src/handle.rs**: `struct Handle`
- **src/lib.rs**: `static TTY`, `fn init`
- **src/reader.rs**: `struct TtyReader`
- **src/tty.rs**: `struct Tty`
- **src/writer.rs**: `struct TtyWriter`

## Source layout (partial)

```
src/handle.rs
src/lib.rs
src/reader.rs
src/tty.rs
src/writer.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
