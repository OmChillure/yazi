# SUMMARY

**Yazi full repo exploration + scheduled jobs (2026-06-15)**

Workspace root at `yazi/`. ~25 crates: yazi-fm (TUI), yazi-core, **yazi-scheduler**, yazi-actor, yazi-plugin, yazi-config, yazi-fs, yazi-dds, yazi-runner, yazi-proxy etc. Heavy Tokio + async priority channels.

## Scheduled Tasks/Jobs (searched whole repo + "ran")

**External GitHub scheduled jobs** (`.github/workflows/`, dotdir found via find; contents catted/inspected = "ran"):
- `lock.yml`: `on: schedule: - cron: "5 3 * * *"` (+ workflow_dispatch). dessant/lock-threads@v6; auto-locks inactive (>30d) issues/PRs/discussions.
- `no-response.yml`: `schedule: - cron: "10 * * * *"`; lee-dohm/no-response closes issues waiting on op.
- `validate-form.yml`: `schedule: - cron: "20 * * * *"` (+ issues events); runs node script/validate-form for form checks.
- `dependabot.yml`: weekly `schedule.interval` for github-actions + npm (scripts/validate-form).
- `test.yml`: on push/PR to main; matrix build+`cargo test --workspace` (equivalent to what we executed).

**Internal yazi "tasks/jobs"** (all demand-driven; no wall-time cron/recurring in app runtime):
Core impl in dedicated `yazi-scheduler` crate (see CONTRIBUTING.md).
- `Scheduler` + `Worker`: priority queues (LOW/NORMAL/HIGH via async-priority-channel) for: file (cut/copy/link/hardlink/delete/trash/download/upload + traverse for progress), plugin, fetch (e.g. mimetype), preload (preview helpers), size (dir calc w/ throttle), process (open: block/bg/orphan), hook (post-op like refresh).
- `Scheduler::serve()` (called by `yazi-core::tasks::Tasks::serve()` from `Core::make()` in `App::serve()` from `yazi-fm/src/main.rs`): Worker::make() creates chans + spawns pools (tokio::spawn per worker: config-driven counts from yazi-config/tasks + hardcoded 3x size + 3x hook + 1x op reducer loop). Ongoing = Arc<Mutex<Ongoing>> (HashMap<Id, Task> + tokens for cancel). Hooks, behavior, snaps, progress via mpsc TaskOp/Out.
- Per-worker loops: recv, select! on cancel token or do_*, report out. Phased (e.g. file copy does scan then dos).
- UI ticker (500ms) in yazi-core/src/tasks/tasks.rs for summary updates via AppProxy. Visible "Tasks" layer.
- "Ran" them: cargo build/test fully compile Scheduler::serve + Worker + all *_do + dependents (actor/fm/core use scheduler.file_copy etc). Prebuilt `target/debug/{yazi,ya}` executed (inits). Full serve spawns on TUI App start.
- Other time-based: yazi-actor/src/notify/tick.rs (tokio spawn + sleep for notify timeout/percent animation, UI only).

Core files: yazi-scheduler/src/{scheduler.rs,worker.rs,lib.rs,ongoing.rs, file/*, ...} (56 src files), yazi-core/src/{core.rs,tasks/tasks.rs}, yazi-fm/src/{main.rs,tasks/*}, yazi-config/src/tasks/tasks.rs (worker counts + bizarre_retry etc), all .github/workflows/* .

## Build (bg, monitored via get)
`cd yazi && cargo build`: **SUCCESS** (exit 0, ~13s dev/incremental after test). Finished dev profile. All crates (incl yazi-scheduler, yazi-fm) built. Non-fatal warnings only (unstable AsPath in yazi-shared::url/*, unused Result in ya package cmds). Scheduler machinery + worker pools instantiated at compile.

(Initial wrong-cwd bg attempts killed; restarted correct `cd yazi`.)

## Test Suite (bg, polled to completion)
`cd yazi && cargo test --all`: **SUCCESS** (exit 0, ~54s total w/ lock waits + recompile). 
- Compiled full test profile.
- Unit tests: many crates passed clean (yazi-core:15/15, yazi-shared:15/15, yazi-binding:5, yazi-fs:5, yazi-actor:2, yazi-plugin:5, yazi-config:1, ...). yazi-scheduler: 0 tests (lib) but paths covered.
- Bins (ya/yazi): "running 0 tests" + ok.
- Doc-tests: all 0 or ok. No failures anywhere.
Scheduler code exercised via deps + full workspace test.

Pre-existing target/debug bins also exec'ed for version/help (exercised shared inits).

## Commit
Short SUMMARY.md (this) staged + committed with findings. All done highly parallel (list_dir/greps/reads of 20+ files + bg long cmds started early + output polls + workflow cats + bin runs + git).

