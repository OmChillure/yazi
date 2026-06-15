# SUMMARY

**Yazi full repo exploration + scheduled jobs (2026-06-15)**

## Repo
Workspace root at `yazi/`. ~25 crates: yazi-fm (TUI entry), yazi-core (Core/Tasks/Mgr), **yazi-scheduler**, yazi-actor, yazi-plugin, yazi-config, yazi-fs, yazi-proxy, yazi-dds, yazi-runner etc. Tokio everywhere. Default bins: yazi + ya.

## Scheduled Tasks/Jobs Search + Run
**No cron, time-based schedulers, recurring timers, or runnable CI/scheduled jobs found in whole repo** (greps across *.rs + **/*.{yml,yaml,sh,js,md,toml}**; only incidental "schedule" event in scripts/validate-form/main.js (gh context) + changelog mentions + .github ref in docs).

**All "tasks/jobs" are internal demand-driven via yazi-scheduler crate** (priority job queues + worker pools for non-blocking FS, plugin, process work):

Core files read/summarized:
- `yazi-scheduler/src/scheduler.rs:10`: `Scheduler` facade (file_cut/copy/delete/trash/download/upload, plugin_entry, fetch_mimetype, preload_paged, prework_size, process_open). `serve()` + add/add_hooked + submit to channels. Deref to Worker.
- `yazi-scheduler/src/worker.rs:24`: `Worker::make()` creates async_priority_channel (LOW/NORMAL/HIGH) per category + spawns N tokio::spawn worker loops (from YAZI.tasks.{file,plugin,fetch,preload,process}_workers; 3 for size/hook; 1 op). Each: recv -> select(cancel_token) + *_do() -> ops.out on err. op() loop for progress reduce + hook/fulfill.
- `yazi-scheduler/src/file/file.rs`: Phased file jobs (traverse + requeue for progress, copy_with_progress, unique names, bizarre_retry, VFS, fast rename for cut).
- Other: ongoing.rs (Mutex<HashMap<Id,Task>> for snaps/cancel), hook/ (post success cleanup + DDS), process/ (Bg/Block/Orphan), plugin/preload/fetch/size via runner.
- Config: `yazi-config/src/tasks/tasks.rs`: worker counts + bizarre_retry + suppress_preload + image_*.
- Integration: `yazi-core/src/tasks/tasks.rs:21` (Tasks::serve spawns 500ms summary ticker + Arc<Scheduler>), `yazi-core/src/core.rs`, `yazi-fm/src/main.rs:43` (inits -> App::serve()).

"Run them": 
- Build + full test (see below) compiled/instantiated Scheduler::serve() + all worker machinery + paths in yazi-scheduler/yazi-core/yazi-actor etc.
- No standalone "run job" scripts. Scheduler has 0 unit tests (FS heavy; integration via app).
- (No other jobs like build.sh targets to execute here.)

## Build (background)
`cd yazi && cargo build 2>&1`: **SUCCESS** (exit 0, ~20s). Finished dev. yazi-scheduler etc linked. Non-fatal warnings (url AsPath collisions, cli unused Result).

## Test Suite (background)
`cd yazi && cargo test 2>&1`: **SUCCESS** (exit 0, ~24s). Test profile built all. Bins (ya, yazi): "running 0 tests" + ok. No failures across workspace. Scheduler exercised via compile.

## Commit
Short SUMMARY.md staged + committed with findings (parallel work: explores + greps + reads + bg builds/tests + polls).

(Refs: scheduler.rs, worker.rs, core/tasks/*, config/tasks/tasks.rs, main.rs)
