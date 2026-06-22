# yazi-macro

## Purpose

Internal helper macros (`mod_pub!`, `mod_flat!`, render helpers) used across the workspace.

**Crate description (Cargo.toml):** Yazi macros

## Dependencies (workspace)

_none (leaf or external-only)_

## Module map

Public/internal modules exported from the crate root:

_See `src/lib.rs` or `src/main.rs`._

## Main files

- `src/lib.rs` — entry/core
- `src/actor.rs` — entry/core
- `src/context.rs` — entry/core
- `src/actor.rs` (file)
- `src/asset.rs` (file)
- `src/confirm.rs` (file)
- `src/context.rs` (file)
- `src/data.rs` (file)
- `src/event.rs` (file)
- `src/fmt.rs` (file)
- `src/fs.rs` (file)
- `src/input.rs` (file)
- `src/lib.rs` (file)
- `src/log.rs` (file)
- `src/module.rs` (file)
- `src/platform.rs` (file)
- `src/render.rs` (file)
- `src/stdio.rs` (file)

## Key public items

_See source for exported APIs._

## Source layout (partial)

```
src/actor.rs
src/asset.rs
src/confirm.rs
src/context.rs
src/data.rs
src/event.rs
src/fmt.rs
src/fs.rs
src/input.rs
src/lib.rs
src/log.rs
src/module.rs
src/platform.rs
src/render.rs
src/stdio.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
