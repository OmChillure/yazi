# yazi-proxy

## Purpose

Thin event/command proxy layer: ergonomic helpers that send domain events (app, mgr, input, tasks, etc.) into the actor/core event system without every caller depending on low-level event construction.

## Dependencies

- `yazi-config`, `yazi-core`, `yazi-macro`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-widgets`
- External: `anyhow`, `tokio`

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | Module exports |
| `src/macros.rs` | Proxy macros reducing boilerplate |
| `src/app.rs` | App-level proxies (quit, resize, render…) |
| `src/mgr.rs` | Manager/tab proxies (cd, select, hover…) |
| `src/cmp.rs` | Completion popup proxies |
| `src/confirm.rs` | Confirm dialog proxies |
| `src/input.rs` | Input bar proxies |
| `src/notify.rs` | Notification proxies |
| `src/pick.rs` | Picker proxies |
| `src/tasks.rs` | Task list proxies |
| `src/which.rs` | Which-key proxies |

## Key concepts

| Concept | Description |
|---------|-------------|
| Proxy functions | Construct and emit typed events for each UI subsystem |
| Macros | Shorthand for common emit patterns |

## Notes

Used heavily by plugins/Lua bindings and actors so business logic stays decoupled from event wiring.
