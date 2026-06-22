# yazi-parser

## Purpose

Parses user/plugin payloads and command arguments into strongly-typed event/action structs.

**Crate description (Cargo.toml):** Yazi form parser

## Dependencies (workspace)

`yazi-binding`, `yazi-boot`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-scheduler`, `yazi-shared`, `yazi-term`, `yazi-vfs`, `yazi-widgets`

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
- `spark`
- `spot`
- `tasks`
- `which`
- `arrow`
- `void`

## Main files

- `src/lib.rs` — entry/core
- `src/app` (dir)
- `src/arrow.rs` (file)
- `src/cmp` (dir)
- `src/confirm` (dir)
- `src/help` (dir)
- `src/input` (dir)
- `src/lib.rs` (file)
- `src/macros.rs` (file)
- `src/mgr` (dir)
- `src/notify` (dir)
- `src/pick` (dir)
- `src/spark` (dir)
- `src/spot` (dir)
- `src/tasks` (dir)
- `src/void.rs` (file)
- `src/which` (dir)

## Key public items

- **src/app/deprecate.rs**: `struct DeprecateForm`
- **src/app/dnd.rs**: `struct DndForm`
- **src/app/lua.rs**: `struct LuaForm`
- **src/app/mouse.rs**: `struct MouseForm`
- **src/app/plugin.rs**: `struct PluginForm`
- **src/app/quit.rs**: `struct QuitForm`
- **src/app/reflow.rs**: `struct ReflowForm`
- **src/app/title.rs**: `struct TitleForm`
- **src/app/update_progress.rs**: `struct UpdateProgressForm`
- **src/arrow.rs**: `struct ArrowForm`
- **src/cmp/close.rs**: `struct CloseForm`
- **src/cmp/show.rs**: `struct ShowForm`
- **src/cmp/trigger.rs**: `struct TriggerForm`
- **src/confirm/close.rs**: `struct CloseForm`
- **src/confirm/show.rs**: `struct ShowForm`
- **src/help/toggle.rs**: `struct ToggleForm`
- **src/input/close.rs**: `struct CloseForm`
- **src/mgr/bulk_exit.rs**: `struct BulkExitForm`
- **src/mgr/cd.rs**: `struct CdForm`
- **src/mgr/close.rs**: `struct CloseForm`
- **src/mgr/copy.rs**: `struct CopyForm`, `enum CopySeparator`
- **src/mgr/create.rs**: `struct CreateForm`
- **src/mgr/displace_do.rs**: `struct DisplaceDoForm`
- **src/mgr/download.rs**: `struct DownloadForm`
- **src/mgr/filter.rs**: `struct FilterForm`

## Source layout (partial)

```
src/app/deprecate.rs
src/app/dnd.rs
src/app/lua.rs
src/app/mod.rs
src/app/mouse.rs
src/app/plugin.rs
src/app/quit.rs
src/app/reflow.rs
src/app/title.rs
src/app/update_progress.rs
src/arrow.rs
src/cmp/close.rs
src/cmp/mod.rs
src/cmp/show.rs
src/cmp/trigger.rs
src/confirm/close.rs
src/confirm/mod.rs
src/confirm/show.rs
src/help/mod.rs
src/help/toggle.rs
src/input/close.rs
src/input/mod.rs
src/lib.rs
src/macros.rs
src/mgr/bulk_exit.rs
src/mgr/cd.rs
src/mgr/close.rs
src/mgr/copy.rs
src/mgr/create.rs
src/mgr/displace_do.rs
src/mgr/download.rs
src/mgr/escape.rs
src/mgr/filter.rs
src/mgr/find.rs
src/mgr/find_arrow.rs
src/mgr/find_do.rs
src/mgr/hardlink.rs
src/mgr/hidden.rs
src/mgr/hover.rs
src/mgr/linemode.rs
src/mgr/link.rs
src/mgr/mod.rs
src/mgr/open.rs
src/mgr/open_do.rs
src/mgr/paste.rs
src/mgr/peek.rs
src/mgr/remove.rs
src/mgr/rename.rs
src/mgr/reveal.rs
src/mgr/search.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
