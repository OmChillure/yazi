# yazi-scheduler

## Purpose

Background task scheduler for copy/move/delete/download/plugin/preload work with progress reporting.

**Crate description (Cargo.toml):** Yazi task scheduler

## Dependencies (workspace)

`yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-runner`, `yazi-shared`, `yazi-term`, `yazi-vfs`

## Module map

Public/internal modules exported from the crate root:

- `fetch`
- `file`
- `hook`
- `plugin`
- `preload`
- `process`
- `size`
- `behavior`
- `cleanup`
- `ongoing`
- `op`
- `out`
- `progress`
- `proxy`
- `r#in`
- `scheduler`
- `snap`
- `summary`
- `task`
- `worker`

## Main files

- `src/lib.rs` — entry/core
- `src/behavior.rs` (file)
- `src/cleanup.rs` (file)
- `src/fetch` (dir)
- `src/file` (dir)
- `src/hook` (dir)
- `src/in.rs` (file)
- `src/lib.rs` (file)
- `src/macros.rs` (file)
- `src/ongoing.rs` (file)
- `src/op.rs` (file)
- `src/out.rs` (file)
- `src/plugin` (dir)
- `src/preload` (dir)
- `src/process` (dir)
- `src/progress.rs` (file)
- `src/proxy.rs` (file)
- `src/scheduler.rs` (file)
- `src/size` (dir)
- `src/snap.rs` (file)
- `src/summary.rs` (file)
- `src/task.rs` (file)
- `src/worker.rs` (file)

## Key public items

- **src/behavior.rs**: `struct Behavior`
- **src/cleanup.rs**: `enum CleanupState`
- **src/fetch/fetch.rs**: `struct Fetch`
- **src/fetch/progress.rs**: `struct FetchProg`
- **src/file/in.rs**: `struct FileInCut`
- **src/file/progress.rs**: `struct FileProgCopy`, `struct FileProgCut`, `struct FileProgLink`, `struct FileProgHardlink`, `struct FileProgDelete`, `struct FileProgTrash`, `struct FileProgDownload`, `struct FileProgUpload`
- **src/in.rs**: `trait TaskIn`
- **src/ongoing.rs**: `struct Ongoing`
- **src/op.rs**: `struct TaskOps`
- **src/plugin/in.rs**: `struct PluginInEntry`
- **src/plugin/progress.rs**: `struct PluginProgEntry`
- **src/preload/preload.rs**: `struct Preload`
- **src/preload/progress.rs**: `struct PreloadProg`
- **src/process/option.rs**: `struct ProcessOpt`
- **src/process/progress.rs**: `struct ProcessProgBlock`, `struct ProcessProgOrphan`, `struct ProcessProgBg`
- **src/progress.rs**: `trait Progress`, `enum TaskProg`
- **src/proxy.rs**: `struct AppProxy`, `struct TasksProxy`, `struct NotifyProxy`
- **src/scheduler.rs**: `struct Scheduler`
- **src/size/progress.rs**: `struct SizeProg`
- **src/size/size.rs**: `struct Size`
- **src/snap.rs**: `struct TaskSnap`
- **src/summary.rs**: `struct TaskSummary`
- **src/task.rs**: `struct Task`
- **src/worker.rs**: `struct Worker`

## Source layout (partial)

```
src/behavior.rs
src/cleanup.rs
src/fetch/fetch.rs
src/fetch/in.rs
src/fetch/mod.rs
src/fetch/out.rs
src/fetch/progress.rs
src/file/file.rs
src/file/in.rs
src/file/macros.rs
src/file/mod.rs
src/file/out.rs
src/file/progress.rs
src/file/transaction.rs
src/file/traverse.rs
src/hook/hook.rs
src/hook/in.rs
src/hook/macros.rs
src/hook/mod.rs
src/in.rs
src/lib.rs
src/macros.rs
src/ongoing.rs
src/op.rs
src/out.rs
src/plugin/in.rs
src/plugin/macros.rs
src/plugin/mod.rs
src/plugin/out.rs
src/plugin/plugin.rs
src/plugin/progress.rs
src/preload/in.rs
src/preload/mod.rs
src/preload/out.rs
src/preload/preload.rs
src/preload/progress.rs
src/process/in.rs
src/process/macros.rs
src/process/mod.rs
src/process/option.rs
src/process/out.rs
src/process/process.rs
src/process/progress.rs
src/process/shell.rs
src/progress.rs
src/proxy.rs
src/scheduler.rs
src/size/in.rs
src/size/mod.rs
src/size/out.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
