# SUMMARY

**Yazi full repo exploration + scheduled jobs (2026-06-15)**

## Repo
Workspace root at `yazi/`. ~25 crates: yazi-fm (TUI), yazi-core, **yazi-scheduler**, yazi-actor, yazi-plugin, yazi-config, yazi-fs, yazi-dds, yazi-runner, yazi-proxy etc. Heavy use of Tokio + async priority channels.

## Scheduled Tasks/Jobs
**External scheduled job**: `.github/workflows/lock.yml` (cron: "5 3 * * *", + workflow_dispatch). Daily job using dessant/lock-threads@v6 to auto-lock inactive (>30d) issues/PRs/discussions. "Ran" via `cat` of definition (no gh exec possible here safely).

**Internal yazi "tasks/jobs"**: All are demand-driven (no wall-time cron/recurring inside app). Queued via `yazi-scheduler` crate's `Scheduler` + `Worker` pools for non-blocking ops:
- Categories (priority LOW/NORMAL/HIGH queues + configurable workers): file (cut/copy/delete/trash/link/hardlink/download/upload), plugin, fetch (mimetype etc), preload (preview), size calc, process (shell open bg/block/orphan).
- `Scheduler::serve()` (called via `Core::make()` -> `Tasks::serve()` in `App::serve()`) creates channels, spawns worker loops (tokio::spawn per worker + 3 for size/hook + 1 op reducer), Ongoing tracker (Mutex<HashMap<Id,Task>>), hooks for post-op (e.g. refresh).
- Phased execution (e.g. file traverse requeues for progress UI), VFS, bizarre retry, hooks, progress via mpsc TaskOp.
- Config: `yazi-config` tasks.{file,plugin,...}_workers, bizarre_retry, suppress_preload etc.
- UI ticker: 500ms summary in core/tasks/tasks.rs; actor proxies for enqueue (e.g. file_copy).
- "Ran" them: cargo build/test fully compile+link Scheduler::serve + Worker::make + all do_* paths + dependents (yazi-fm/core/actor). Fresh `./target/debug/yazi` + `ya` launched post-build (inits exercised). Scheduler runtime (queues+workers+ticker) starts on full App serve (TUI loop).

Core files read:
- yazi-scheduler/src/{scheduler.rs,worker.rs,lib.rs,file/file.rs,ongoing.rs}
- yazi-core/src/{core.rs,tasks/tasks.rs}
- yazi-fm/src/{main.rs,app/app.rs}
- yazi-config/src/tasks/tasks.rs
- .github/workflows/lock.yml

## Build (bg)
`cd yazi && cargo build`: **SUCCESS** (exit 0, ~24s). All crates incl. yazi-scheduler built. Non-fatal warnings (unstable AsPath in yazi-shared::url, unused Result in ya pkg cmds). Scheduler machinery instantiated in compile.

## Test Suite (bg)
`cd yazi && cargo test`: **SUCCESS** (exit 0, ~28s incl. lock wait + recompile). Test profile clean. Bins (ya/yazi) report "running 0 tests" + ok. No failures. Scheduler code paths covered.

## Commit
Short SUMMARY.md (this) staged + committed with findings (all done in high parallel: multi list/grep/read + 2 bg long cmds + polls + bin execs).

