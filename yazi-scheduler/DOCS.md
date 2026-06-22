# yazi-scheduler

## Purpose

Async task scheduler/worker pool for Yazi: file ops (copy/cut/delete/trash/link/upload/download), process spawning, preload/fetch/plugin jobs, size calculation, hooks, progress, and cancellation. Priority channels (LOW/NORMAL/HIGH) drive throughput vs responsiveness.

## Dependencies

- `yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-runner`, `yazi-shared`, `yazi-term`, `yazi-vfs`
- External: `async-priority-channel`, `mlua`, `lru`, `tokio`, `hashbrown`, …

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Priority constants, exports |
| `src/scheduler.rs` | `Scheduler` public API |
| `src/worker.rs` | Worker tasks/handles |
| `src/task.rs` / `ongoing.rs` | Task records & in-flight set |
| `src/behavior.rs` | Scheduler behavior/config |
| `src/progress.rs` / `summary.rs` / `snap.rs` | Progress & snapshots |
| `src/proxy.rs` / `op.rs` / `out.rs` / `in.rs` | Task I/O plumbing |
| `src/cleanup.rs` | Teardown |
| `file/` | File operation tasks |
| `process/` | Bg/block/orphan processes |
| `preload/` / `fetch/` / `plugin/` | Preview/fetch/plugin jobs |
| `hook/` | Post-task hooks |
| `size/` | Directory size calc |

## Key types / methods

| Item | Description |
|------|-------------|
| `Scheduler::serve()` | Start worker pool |
| `file_copy` / `file_cut` / … | Enqueue FS operations |
| `cancel(id)` | Cancel task (may run cancel hook) |
| `shutdown()` | Abort worker handles |
| `Worker` | Internal queues and submit paths |
| `Task` / `TaskIn` / `TaskProg` | Task identity, input, progress |

## Notes

`Core::make()` starts tasks via `Tasks::serve()` which owns/links a scheduler. Hooks often invoke Lua via `yazi-runner`.
