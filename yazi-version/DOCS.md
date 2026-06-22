# yazi-version

## Purpose

Version/build identity string and related constants for CLI banners and DDS.

**Crate description (Cargo.toml):** Yazi version information

## Dependencies (workspace)

_none (leaf or external-only)_

## Module map

Public/internal modules exported from the crate root:

_See `src/lib.rs` or `src/main.rs`._

## Main files

- `src/lib.rs` — entry/core
- `src/lib.rs` (file)

## Key public items

- **src/lib.rs**: `fn version`, `fn version_long`, `fn version_full`

## Source layout (partial)

```
src/lib.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
