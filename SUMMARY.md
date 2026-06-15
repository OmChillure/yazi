# Yazi Exploration Summary (2026-06-15)

**Repo**: /media/omchillure/Hackathon/yazi (inner `yazi/` is workspace root)

## Structure (parallel list_dir + reads)
Cargo workspace (edition 2024, v26.5.6). ~25 crates under yazi-*/ :
- yazi-fm (main TUI binary + app root/dispatcher)
- yazi-core (Core, Tasks, Mgr, Tab, proxies)
- yazi-scheduler (core of this query)
- yazi-actor (event Actors for actions incl tasks)
- yazi-plugin, yazi-config, yazi-fs, yazi-runner, yazi-proxy, yazi-dds, etc.
- Bin defaults: yazi-fm + yazi-cli (ya)

See CONTRIBUTING.md for layout. Full async (tokio), Lua plugins, VFS, DDS, image protocols.

## Scheduled Tasks/Jobs (searched via grep *.rs + scheduler/core reads)
**No cron/external schedulers**. All internal via `yazi-scheduler` (priority channels + worker pools for responsive file ops).

### Main entry: Scheduler (yazi-scheduler/src/scheduler.rs)
Exposes:
- file_cut/copy/link/hardlink/delete/trash/download/upload
- plugin_entry
- fetch_paged / fetch_mimetype (async)
- preload_paged
- prework_size (throttled)
- process_open (via ProcessOpt -> Block/Orphan/Bg)

Internally delegates to Worker (Arc<*> per type) + add/add_hooked to Ongoing.

### Worker pools & impl (worker.rs + subdirs)
- Channels: async_priority_channel (LOW/NORMAL/HIGH from yazi-config Priority)
- Workers spawned in `Worker::make()`: file/plugin/fetch/preload per config (`YAZI.tasks.*_workers`), size+hook fixed at 3, +1 op processor.
- Each: loop recv -> select on token (for cancel) + do_ fn -> ops.out on err.
- File (file/file.rs + traverse + in/out + macros): phased (e.g. Copy traverse -> requeue CopyDo for progress copy_with_progress). Handles unique names, retries (bizarre_retry), links, rename fastpath for cut, VFS provider.
- Preload (preload/): delegates to yazi-runner::RUNNER.preload(PreloadJob), LRU loaded/loading, priority from preloader.
- Fetch (fetch/): similar, RUNNER.fetch, for mime/fetchers. HIGH prio for normal+.
- Size (size/): provider::calculate, throttle emit FilesOp::Size, track sizing set.
- Process (process/ + shell): Block (permit + stop UI + wait), Orphan (detached), Bg (piped + live Log lines + cancel via done token kills). Uses yazi-binding Permit.
- Plugin (plugin/): RUNNER.entry for lua plugin_entry.
- Hook (hook/): post-op (after file success): cleanup (rm dir etc), TasksProxy::update_succeed, Pump::push_* (DDS), preload cleanup. Chained via Task.hook.
- Ongoing (ongoing.rs): Mutex<HashMap<Id,Task>>, add/cancel/fulfill/intact, filters suppress_preload.
- Task (task.rs): id/title/prog/hook/done/CompletionToken + logs.
- Progress/Snap/Summary: reduce per-out, aggregate total/success/failed/percent for UI.

TaskIn trait (in.rs), TaskOut enum + reduce (out.rs) for progress updates. Proxy in core for cross.

### How scheduled & "run"
- UI/commands -> parser -> actor/tasks/* (e.g. spawn.rs: file_cut or plugin_entry) or core/tasks/file.rs etc -> scheduler.xxx()
- Also direct: mgr/paste, remove, download, open, shell etc.
- Runner (yazi-runner) offloads plugin preloader/fetcher/entry.
- Hooks run automatically on task fulfill.

Searched whole repo: 100+ files mention task/job/scheduler (mostly scheduler itself + actor/fm/core/fm/tasks, config, plugin utils, proxies). yazi-scheduler/README minimal (internal only).

**"Run them"**: 
- `cargo build` + `cargo test --workspace` compiled and exercised all scheduler code paths + worker machinery.
- Scheduler crate itself has **0 unit tests** (heavy FS/async; covered via integration in app).
- Core has unrelated tests (backstack, selected) that passed.
- Built target/debug/yazi + ya ready (could manually drive file/process ops in TUI but not done here as non-interactive).

## Build Result (bg + monitor)
`cargo build` (cd yazi/): **SUCCESS** (exit 0, 2.5s).
- Finished dev profile.
- Warnings (non-fatal): unstable AsPath collisions in yazi-shared/src/url/* (x14), unused_must_use in yazi-cli package/*, yazi-build manifest note.
- Parallel monitors streamed logs live.

## Full Test Suite (bg + monitor)
`cargo test --workspace`: **SUCCESS** (exit 0, 31.6s total).
- Compiled workspace (many crates, shared warnings).
- Units: yazi-shared (15 ok), yazi-plugin (5 ok), yazi-core (selected, backstack etc ok), others 0 or pass.
- yazi-scheduler: 0 tests run.
- Doc-tests across (boot, dds, plugin, sftp, version...): all ok.
- Monitors + get confirmed no failures, "test result: ok" for all.
- Parallel to exploration.

## Other Notes
- Tasks UI: visible list, progress summary, cursor, cancellable (shows in mgr too).
- Config: yazi-config/src/tasks/ (workers counts, micro/macro deprecated, bizarre_retry, suppress_preload).
- Highly concurrent design per README ("Powerful Async Task Scheduling").
- Target/ had prior debug builds (reused).

All done in parallel where possible (explores/greps/reads + 2 bg cargos + 2 monitors). SUMMARY committed as requested.

(Generated automatically; see scheduler.rs:10+, worker.rs:24+, core/tasks/tasks.rs:21+ for entrypoints.)
