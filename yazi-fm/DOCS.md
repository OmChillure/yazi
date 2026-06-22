# yazi-fm

## Purpose

Main **Yazi file manager** binary (`yazi`). Owns process entrypoint, subsystem initialization order, async app loop, signal handling, key/event dispatch, and ratatui rendering for all UI panels.

## Dependencies

- Almost every workspace crate (`yazi-actor`, `yazi-adapter`, `yazi-plugin`, `yazi-scheduler`, …)
- External: `tokio`, `ratatui`, `anyhow`, `tikv-jemallocator` (non-macOS/non-Windows), `fdlimit`, …

## Main files / modules

| Module | Role |
|--------|------|
| `src/main.rs` | Entry: init chain + `App::serve()` |
| `app/` | Application serve loop |
| `dispatcher.rs` | Routes events to handlers |
| `executor.rs` | Executes actions/actors |
| `router.rs` | Key/event routing by layer |
| `root.rs` | Root widget/layout |
| `signals.rs` | OS signal handling |
| `logs.rs` / `panic.rs` | Logging & panic hook |
| `mgr/`, `tasks/`, `input/`, … | Render modules per UI area |

## Startup sequence (`main`)

1. Panic hook, `yazi_shared::init()`, logs, fd limit
2. `yazi_fs` / `yazi_vfs` / `yazi_tty`
3. `yazi_config` / `yazi_boot`
4. `yazi_term` / `yazi_adapter`
5. `yazi_dds` / `yazi_widgets` / `yazi_watcher`
6. `yazi_runner::init(slim_lua)` / `yazi_plugin::init()`
7. `yazi_dds::serve()` then `App::serve()` on `LOCAL_SET`

## Key types

| Type | Description |
|------|-------------|
| `App` | Main async application |
| `Dispatcher` / `Executor` / `Router` | Input → actor pipeline |
| UI modules | Draw mgr/tasks/modals |

## Notes

Workspace default member. Companion CLI is `yazi-cli` (`ya`).
