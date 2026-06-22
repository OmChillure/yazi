# yazi-plugin

## Purpose

Lua plugin host: loads plugins, runs previewers/fetchers/preloaders, exposes Ya/UI/FS APIs.

**Crate description (Cargo.toml):** Yazi plugin system

## Dependencies (workspace)

`yazi-adapter`, `yazi-binding`, `yazi-boot`, `yazi-codegen`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-proxy`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-vfs`, `yazi-widgets`

## Module map

Public/internal modules exported from the crate root:

- `elements`
- `external`
- `fs`
- `keymap`
- `pubsub`
- `runtime`
- `tasks`
- `theme`
- `utils`
- `slim`
- `standard`

## Main files

- `src/lib.rs` — entry/core
- `src/elements` (dir)
- `src/external` (dir)
- `src/fs` (dir)
- `src/keymap` (dir)
- `src/lib.rs` (file)
- `src/pubsub` (dir)
- `src/runtime` (dir)
- `src/slim.rs` (file)
- `src/standard.rs` (file)
- `src/tasks` (dir)
- `src/theme` (dir)
- `src/utils` (dir)

## Key public items

- **src/elements/elements.rs**: `fn compose`
- **src/external/fd.rs**: `struct FdOpt`, `fn fd`
- **src/external/rg.rs**: `struct RgOpt`, `fn rg`
- **src/external/rga.rs**: `struct RgaOpt`, `fn rga`
- **src/fs/fs.rs**: `fn compose`
- **src/keymap/keymap.rs**: `fn compose`
- **src/lib.rs**: `fn init`
- **src/pubsub/pubsub.rs**: `struct Pubsub`
- **src/runtime/runtime.rs**: `fn compose`
- **src/slim.rs**: `fn slim_lua`
- **src/standard.rs**: `static LUA`
- **src/theme/theme.rs**: `fn compose`, `fn reset`
- **src/utils/utils.rs**: `fn compose`

## Source layout (partial)

```
src/elements/elements.rs
src/elements/mod.rs
src/external/fd.rs
src/external/mod.rs
src/external/rg.rs
src/external/rga.rs
src/fs/fs.rs
src/fs/mod.rs
src/fs/op.rs
src/keymap/keymap.rs
src/keymap/mod.rs
src/lib.rs
src/pubsub/mod.rs
src/pubsub/pubsub.rs
src/runtime/mod.rs
src/runtime/plugin.rs
src/runtime/runtime.rs
src/runtime/term.rs
src/slim.rs
src/standard.rs
src/tasks/mod.rs
src/tasks/option.rs
src/tasks/task.rs
src/theme/mod.rs
src/theme/theme.rs
src/utils/app.rs
src/utils/cache.rs
src/utils/call.rs
src/utils/image.rs
src/utils/json.rs
src/utils/layer.rs
src/utils/log.rs
src/utils/mod.rs
src/utils/preview.rs
src/utils/process.rs
src/utils/spot.rs
src/utils/sync.rs
src/utils/target.rs
src/utils/tasks.rs
src/utils/text.rs
src/utils/time.rs
src/utils/user.rs
src/utils/utils.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
