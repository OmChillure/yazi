# yazi-actor

## Purpose

Implements the actor-model command handlers that react to user and system events. Each user action (cd, enter, quit, plugin, etc.) is an actor method operating on shared app/context state.

**Crate description (Cargo.toml):** Yazi actor model

## Dependencies (workspace)

`yazi-binding`, `yazi-boot`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-parser`, `yazi-plugin`, `yazi-proxy`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-tui`, `yazi-vfs`, `yazi-watcher`, `yazi-widgets`

## Module map

Public/internal modules exported from the crate root:

- `app`
- `cmp`
- `confirm`
- `core`
- `help`
- `input`
- `lives`
- `mgr`
- `notify`
- `pick`
- `spot`
- `tasks`
- `which`
- `actor`
- `context`

## Main files

- `src/lib.rs` — entry/core
- `src/actor.rs` — entry/core
- `src/context.rs` — entry/core
- `src/actor.rs` (file)
- `src/app` (dir)
- `src/cmp` (dir)
- `src/confirm` (dir)
- `src/context.rs` (file)
- `src/core` (dir)
- `src/help` (dir)
- `src/input` (dir)
- `src/lib.rs` (file)
- `src/lives` (dir)
- `src/mgr` (dir)
- `src/notify` (dir)
- `src/pick` (dir)
- `src/spot` (dir)
- `src/tasks` (dir)
- `src/which` (dir)

## Key public items

- **src/actor.rs**: `trait Actor`
- **src/app/accept_payload.rs**: `struct AcceptPayload`
- **src/app/bootstrap.rs**: `struct Bootstrap`
- **src/app/deprecate.rs**: `struct Deprecate`
- **src/app/dnd.rs**: `struct Dnd`
- **src/app/focus.rs**: `struct Focus`
- **src/app/lua.rs**: `struct Lua`
- **src/app/mouse.rs**: `struct Mouse`
- **src/app/plugin.rs**: `struct Plugin`
- **src/app/plugin_do.rs**: `struct PluginDo`
- **src/app/quit.rs**: `struct Quit`
- **src/app/reflow.rs**: `struct Reflow`
- **src/app/resize.rs**: `struct Resize`
- **src/app/resume.rs**: `struct Resume`
- **src/app/stop.rs**: `struct Stop`
- **src/app/theme.rs**: `struct Theme`
- **src/app/title.rs**: `struct Title`
- **src/app/update_progress.rs**: `struct UpdateProgress`
- **src/cmp/arrow.rs**: `struct Arrow`
- **src/cmp/close.rs**: `struct Close`
- **src/cmp/show.rs**: `struct Show`
- **src/cmp/trigger.rs**: `struct Trigger`
- **src/confirm/arrow.rs**: `struct Arrow`
- **src/confirm/close.rs**: `struct Close`
- **src/confirm/show.rs**: `struct Show`

## Source layout (partial)

```
src/actor.rs
src/app/accept_payload.rs
src/app/bootstrap.rs
src/app/deprecate.rs
src/app/dnd.rs
src/app/focus.rs
src/app/lua.rs
src/app/mod.rs
src/app/mouse.rs
src/app/plugin.rs
src/app/plugin_do.rs
src/app/quit.rs
src/app/reflow.rs
src/app/resize.rs
src/app/resume.rs
src/app/stop.rs
src/app/theme.rs
src/app/title.rs
src/app/update_progress.rs
src/cmp/arrow.rs
src/cmp/close.rs
src/cmp/mod.rs
src/cmp/show.rs
src/cmp/trigger.rs
src/confirm/arrow.rs
src/confirm/close.rs
src/confirm/mod.rs
src/confirm/show.rs
src/context.rs
src/core/mod.rs
src/core/preflight.rs
src/help/arrow.rs
src/help/escape.rs
src/help/filter.rs
src/help/mod.rs
src/help/toggle.rs
src/input/close.rs
src/input/complete.rs
src/input/escape.rs
src/input/mod.rs
src/input/show.rs
src/lib.rs
src/lives/behavior.rs
src/lives/core.rs
src/lives/file.rs
src/lives/files.rs
src/lives/filter.rs
src/lives/finder.rs
src/lives/folder.rs
src/lives/lives.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
