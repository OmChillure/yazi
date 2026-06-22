# yazi-core

## Purpose

Core domain models: tabs, folders, files, tasks, input/pick/confirm UI state, preview/spot, and the manager glue.

**Crate description (Cargo.toml):** Yazi core logic

## Dependencies (workspace)

`yazi-adapter`, `yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-vfs`, `yazi-watcher`, `yazi-widgets`, `yazi-prebuilt`

## Module map

Public/internal modules exported from the crate root:

- `app`
- `cmp`
- `confirm`
- `help`
- `input`
- `mgr`
- `notify`
- `pick`
- `spot`
- `tab`
- `tasks`
- `which`
- `core`
- `highlighter`
- `proxy`

## Main files

- `src/lib.rs` — entry/core
- `src/app` (dir)
- `src/cmp` (dir)
- `src/confirm` (dir)
- `src/core.rs` (file)
- `src/help` (dir)
- `src/highlighter.rs` (file)
- `src/input` (dir)
- `src/lib.rs` (file)
- `src/mgr` (dir)
- `src/notify` (dir)
- `src/pick` (dir)
- `src/proxy.rs` (file)
- `src/spot` (dir)
- `src/tab` (dir)
- `src/tasks` (dir)
- `src/which` (dir)

## Key public items

- **src/app/plugin.rs**: `struct PluginOpt`, `enum PluginMode`, `trait PluginCallback`
- **src/app/quit.rs**: `struct QuitOpt`
- **src/cmp/cmp.rs**: `struct Cmp`
- **src/cmp/item.rs**: `struct CmpItem`
- **src/cmp/option.rs**: `struct CmpOpt`
- **src/confirm/confirm.rs**: `struct Confirm`
- **src/core.rs**: `struct Core`
- **src/help/help.rs**: `struct Help`
- **src/highlighter.rs**: `struct Highlighter`
- **src/input/input.rs**: `struct Input`
- **src/mgr/batcher.rs**: `struct Batcher`
- **src/mgr/cd.rs**: `enum CdSource`
- **src/mgr/displace.rs**: `struct DisplaceOpt`
- **src/mgr/filter.rs**: `struct FilterOpt`
- **src/mgr/find.rs**: `struct FindDoOpt`
- **src/mgr/mgr.rs**: `struct Mgr`
- **src/mgr/mimetype.rs**: `struct Mimetype`
- **src/mgr/open.rs**: `struct OpenOpt`, `struct OpenDoOpt`
- **src/mgr/search.rs**: `struct SearchOpt`, `enum SearchVia`
- **src/mgr/tabs.rs**: `struct Tabs`
- **src/mgr/yanked.rs**: `struct Yanked`
- **src/notify/level.rs**: `enum MessageLevel`
- **src/notify/message.rs**: `struct Message`
- **src/notify/mod.rs**: `const NOTIFY_BORDER`, `const NOTIFY_SPACING`
- **src/notify/notify.rs**: `struct Notify`

## Source layout (partial)

```
src/app/mod.rs
src/app/plugin.rs
src/app/quit.rs
src/cmp/cmp.rs
src/cmp/item.rs
src/cmp/mod.rs
src/cmp/option.rs
src/confirm/confirm.rs
src/confirm/mod.rs
src/core.rs
src/help/help.rs
src/help/mod.rs
src/highlighter.rs
src/input/input.rs
src/input/mod.rs
src/lib.rs
src/mgr/batcher.rs
src/mgr/cd.rs
src/mgr/displace.rs
src/mgr/filter.rs
src/mgr/find.rs
src/mgr/mgr.rs
src/mgr/mimetype.rs
src/mgr/mod.rs
src/mgr/open.rs
src/mgr/search.rs
src/mgr/tabs.rs
src/mgr/yanked.rs
src/notify/level.rs
src/notify/message.rs
src/notify/mod.rs
src/notify/notify.rs
src/notify/option.rs
src/pick/mod.rs
src/pick/pick.rs
src/proxy.rs
src/spot/lock.rs
src/spot/mod.rs
src/spot/spot.rs
src/tab/backstack.rs
src/tab/finder.rs
src/tab/folder.rs
src/tab/history.rs
src/tab/mod.rs
src/tab/mode.rs
src/tab/preference.rs
src/tab/preview.rs
src/tab/preview_lock.rs
src/tab/selected.rs
src/tab/tab.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
