# yazi-fm

## Purpose

Main `yazi` file-manager binary: event loop, terminal setup, dispatcher wiring actors/scheduler/plugins together.

**Crate description (Cargo.toml):** Yazi file manager

## Dependencies (workspace)

`yazi-actor`, `yazi-adapter`, `yazi-binding`, `yazi-boot`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-parser`, `yazi-plugin`, `yazi-proxy`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-tui`, `yazi-vfs`, `yazi-watcher`, `yazi-widgets`

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
- `tasks`
- `which`
- `dispatcher`
- `executor`
- `logs`
- `panic`
- `root`
- `router`
- `signals`

## Main files

- `src/main.rs` — entry/core
- `src/app` (dir)
- `src/cmp` (dir)
- `src/confirm` (dir)
- `src/dispatcher.rs` (file)
- `src/executor.rs` (file)
- `src/help` (dir)
- `src/input` (dir)
- `src/logs.rs` (file)
- `src/main.rs` (file)
- `src/mgr` (dir)
- `src/notify` (dir)
- `src/panic.rs` (file)
- `src/pick` (dir)
- `src/root.rs` (file)
- `src/router.rs` (file)
- `src/signals.rs` (file)
- `src/spot` (dir)
- `src/tasks` (dir)
- `src/which` (dir)

## Key public items

_See source for exported APIs._

## Source layout (partial)

```
src/app/app.rs
src/app/mod.rs
src/app/render.rs
src/cmp/cmp.rs
src/cmp/mod.rs
src/confirm/body.rs
src/confirm/buttons.rs
src/confirm/confirm.rs
src/confirm/list.rs
src/confirm/mod.rs
src/dispatcher.rs
src/executor.rs
src/help/bindings.rs
src/help/help.rs
src/help/mod.rs
src/input/input.rs
src/input/mod.rs
src/logs.rs
src/main.rs
src/mgr/mod.rs
src/mgr/modal.rs
src/mgr/preview.rs
src/notify/mod.rs
src/notify/notify.rs
src/panic.rs
src/pick/list.rs
src/pick/mod.rs
src/pick/pick.rs
src/root.rs
src/router.rs
src/signals.rs
src/spot/mod.rs
src/spot/spot.rs
src/tasks/list.rs
src/tasks/mod.rs
src/tasks/progress.rs
src/tasks/tasks.rs
src/which/cand.rs
src/which/mod.rs
src/which/which.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
