# yazi-ffi

## Purpose

Thin FFI/platform shims (e.g. libc helpers) used by lower-level crates.

**Crate description (Cargo.toml):** Yazi foreign function interface

## Dependencies (workspace)

`yazi-macro`

## Module map

Public/internal modules exported from the crate root:

- `cf_dict`
- `cf_string`
- `disk_arbitration`
- `io_kit`

## Main files

- `src/lib.rs` — entry/core
- `src/cf_dict.rs` (file)
- `src/cf_string.rs` (file)
- `src/disk_arbitration.rs` (file)
- `src/io_kit.rs` (file)
- `src/lib.rs` (file)

## Key public items

- **src/cf_dict.rs**: `struct CFDict`
- **src/cf_string.rs**: `struct CFString`

## Source layout (partial)

```
src/cf_dict.rs
src/cf_string.rs
src/disk_arbitration.rs
src/io_kit.rs
src/lib.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
