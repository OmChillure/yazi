# yazi-proxy

## Purpose

Thin proxies that send app/mgr/tab/input events into the runtime (used by plugins and subsystems).

**Crate description (Cargo.toml):** Yazi event proxy

## Dependencies (workspace)

`yazi-config`, `yazi-core`, `yazi-macro`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-widgets`

## Module map

Public/internal modules exported from the crate root:

- `app`
- `cmp`
- `confirm`
- `input`
- `mgr`
- `notify`
- `pick`
- `tasks`
- `which`

## Main files

- `src/lib.rs` — entry/core
- `src/app.rs` — entry/core
- `src/app.rs` (file)
- `src/cmp.rs` (file)
- `src/confirm.rs` (file)
- `src/input.rs` (file)
- `src/lib.rs` (file)
- `src/macros.rs` (file)
- `src/mgr.rs` (file)
- `src/notify.rs` (file)
- `src/pick.rs` (file)
- `src/tasks.rs` (file)
- `src/which.rs` (file)

## Key public items

- **src/app.rs**: `struct AppProxy`
- **src/cmp.rs**: `struct CmpProxy`
- **src/confirm.rs**: `struct ConfirmProxy`
- **src/input.rs**: `struct InputProxy`
- **src/mgr.rs**: `struct MgrProxy`
- **src/notify.rs**: `struct NotifyProxy`
- **src/pick.rs**: `struct PickProxy`
- **src/tasks.rs**: `struct TasksProxy`
- **src/which.rs**: `struct WhichProxy`

## Source layout (partial)

```
src/app.rs
src/cmp.rs
src/confirm.rs
src/input.rs
src/lib.rs
src/macros.rs
src/mgr.rs
src/notify.rs
src/pick.rs
src/tasks.rs
src/which.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
