# yazi-fm — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Primary `yazi` binary: app loop, rendering, signals, dispatcher/executor/router wiring everything together.

> Cargo description: *Yazi file manager*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-fm`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `build.rs`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 40 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-actor`
- `yazi-adapter`
- `yazi-binding`
- `yazi-boot`
- `yazi-config`
- `yazi-core`
- `yazi-dds`
- `yazi-fs`
- `yazi-macro`
- `yazi-parser`
- `yazi-plugin`
- `yazi-proxy`
- `yazi-runner`
- `yazi-scheduler`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-tty`
- `yazi-tui`
- `yazi-vfs`
- `yazi-watcher`
- `yazi-widgets`

### External (sample)

`anyhow`, `better-panic`, `bin-dir`, `default`, `fdlimit`, `libc`, `mlua`, `paste`, `path`, `pkg-url`, `ratatui`, `scopeguard`, `signal-hook-tokio`, `tikv-jemallocator`, `tokio`, `tokio-stream`, `tracing`, `tracing-appender`, `tracing-subscriber`, `vendored-lua`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/app` |
| module/file | `src/cmp` |
| module/file | `src/confirm` |
| module/file | `src/dispatcher` |
| module/file | `src/executor` |
| module/file | `src/help` |
| module/file | `src/input` |
| module/file | `src/logs` |
| module/file | `src/main.rs` |
| module/file | `src/mgr` |
| module/file | `src/notify` |
| module/file | `src/panic` |
| module/file | `src/pick` |
| module/file | `src/root` |
| module/file | `src/router` |
| module/file | `src/signals` |
| module/file | `src/spot` |
| module/file | `src/tasks` |
| module/file | `src/which` |

### Notable source files

- `src/app/app.rs`
- `src/app/mod.rs`
- `src/app/render.rs`
- `src/cmp/cmp.rs`
- `src/cmp/mod.rs`
- `src/confirm/body.rs`
- `src/confirm/buttons.rs`
- `src/confirm/confirm.rs`
- `src/confirm/list.rs`
- `src/confirm/mod.rs`
- `src/dispatcher.rs`
- `src/executor.rs`
- `src/help/bindings.rs`
- `src/help/help.rs`
- `src/help/mod.rs`
- `src/input/input.rs`
- `src/input/mod.rs`
- `src/logs.rs`
- `src/main.rs`
- `src/mgr/mod.rs`
- `src/mgr/modal.rs`
- `src/mgr/preview.rs`
- `src/notify/mod.rs`
- `src/notify/notify.rs`
- `src/panic.rs`
- `src/pick/list.rs`
- `src/pick/mod.rs`
- `src/pick/pick.rs`
- `src/root.rs`
- `src/router.rs`
- _…and 10 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `App` | `src/app/app.rs` |
| `fn` | `serve` | `src/app/app.rs` |
| `fn` | `render` | `src/app/render.rs` |
| `fn` | `render_partially` | `src/app/render.rs` |
| `struct` | `Cmp` | `src/cmp/cmp.rs` |
| `fn` | `new` | `src/cmp/cmp.rs` |
| `struct` | `Body` | `src/confirm/body.rs` |
| `struct` | `Buttons` | `src/confirm/buttons.rs` |
| `struct` | `Confirm` | `src/confirm/confirm.rs` |
| `struct` | `List` | `src/confirm/list.rs` |
| `struct` | `Dispatcher` | `src/dispatcher.rs` |
| `fn` | `dispatch` | `src/dispatcher.rs` |
| `fn` | `dispatch_seq` | `src/dispatcher.rs` |
| `struct` | `Executor` | `src/executor.rs` |
| `fn` | `execute` | `src/executor.rs` |
| `struct` | `Bindings` | `src/help/bindings.rs` |
| `struct` | `Help` | `src/help/help.rs` |
| `struct` | `Input` | `src/input/input.rs` |
| `struct` | `Logs` | `src/logs.rs` |
| `fn` | `start` | `src/logs.rs` |
| `struct` | `Modal` | `src/mgr/modal.rs` |
| `struct` | `Preview` | `src/mgr/preview.rs` |
| `struct` | `Notify` | `src/notify/notify.rs` |
| `struct` | `Panic` | `src/panic.rs` |
| `fn` | `install` | `src/panic.rs` |
| `struct` | `Pick` | `src/pick/pick.rs` |
| `struct` | `Root` | `src/root.rs` |
| `fn` | `reflow` | `src/root.rs` |
| `struct` | `Router` | `src/router.rs` |
| `fn` | `route` | `src/router.rs` |
| `struct` | `Signals` | `src/signals.rs` |
| `struct` | `Spot` | `src/spot/spot.rs` |
| `struct` | `Progress` | `src/tasks/progress.rs` |
| `struct` | `Tasks` | `src/tasks/tasks.rs` |
| `fn` | `area` | `src/tasks/tasks.rs` |

## 6. Entry / init surface

Primary entry file: **`src/main.rs`**

```rust
#[cfg(all(not(target_os = "macos"), not(target_os = "windows")))]
#[global_allocator]
static GLOBAL: tikv_jemallocator::Jemalloc = tikv_jemallocator::Jemalloc;

yazi_macro::mod_pub!(app cmp confirm help input mgr notify pick spot tasks which);

yazi_macro::mod_flat!(dispatcher executor logs panic root router signals);

#[tokio::main]
async fn main() -> anyhow::Result<()> {
	Panic::install();
	yazi_shared::init();

	Logs::start()?;
	_ = fdlimit::raise_fd_limit();

	yazi_fs::init();

	yazi_vfs::init();

	yazi_tty::init();

	yazi_config::init()?;

	yazi_boot::init();
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-actor`, `yazi-adapter`, `yazi-binding`, `yazi-boot`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-parser`, `yazi-plugin`, `yazi-proxy`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-tui`, `yazi-vfs`, `yazi-watcher`, `yazi-widgets`

**Depended on by (workspace scan)**: _leaf or only indirect_

## 8. Maintainer tips

- Start reading at `src/main.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-fm`.*
