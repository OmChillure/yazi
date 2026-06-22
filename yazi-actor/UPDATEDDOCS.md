# yazi-actor — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Actor/command implementations: each manager action as a small unit invoked by the executor/router.

> Cargo description: *Yazi actor model*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-actor`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 149 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-binding`
- `yazi-boot`
- `yazi-config`
- `yazi-core`
- `yazi-dds`
- `yazi-emulator`
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

`anyhow`, `default`, `either`, `futures`, `hashbrown`, `indexmap`, `libc`, `mlua`, `paste`, `ratatui`, `scopeguard`, `tokio`, `tokio-stream`, `tracing`, `vendored-lua`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/actor` |
| module/file | `src/app` |
| module/file | `src/cmp` |
| module/file | `src/confirm` |
| module/file | `src/context` |
| module/file | `src/core` |
| module/file | `src/help` |
| module/file | `src/input` |
| module/file | `src/lib.rs` |
| module/file | `src/lives` |
| module/file | `src/mgr` |
| module/file | `src/notify` |
| module/file | `src/pick` |
| module/file | `src/spot` |
| module/file | `src/tasks` |
| module/file | `src/which` |

### Notable source files

- `src/actor.rs`
- `src/app/accept_payload.rs`
- `src/app/bootstrap.rs`
- `src/app/deprecate.rs`
- `src/app/dnd.rs`
- `src/app/focus.rs`
- `src/app/lua.rs`
- `src/app/mod.rs`
- `src/app/mouse.rs`
- `src/app/plugin.rs`
- `src/app/plugin_do.rs`
- `src/app/quit.rs`
- `src/app/reflow.rs`
- `src/app/resize.rs`
- `src/app/resume.rs`
- `src/app/stop.rs`
- `src/app/theme.rs`
- `src/app/title.rs`
- `src/app/update_progress.rs`
- `src/cmp/arrow.rs`
- `src/cmp/close.rs`
- `src/cmp/mod.rs`
- `src/cmp/show.rs`
- `src/cmp/trigger.rs`
- `src/confirm/arrow.rs`
- `src/confirm/close.rs`
- `src/confirm/mod.rs`
- `src/confirm/show.rs`
- `src/context.rs`
- `src/core/mod.rs`
- _…and 119 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `trait` | `Actor` | `src/actor.rs` |
| `struct` | `AcceptPayload` | `src/app/accept_payload.rs` |
| `struct` | `Bootstrap` | `src/app/bootstrap.rs` |
| `struct` | `Deprecate` | `src/app/deprecate.rs` |
| `struct` | `Dnd` | `src/app/dnd.rs` |
| `struct` | `Focus` | `src/app/focus.rs` |
| `struct` | `Lua` | `src/app/lua.rs` |
| `struct` | `Mouse` | `src/app/mouse.rs` |
| `struct` | `Plugin` | `src/app/plugin.rs` |
| `struct` | `PluginDo` | `src/app/plugin_do.rs` |
| `struct` | `Quit` | `src/app/quit.rs` |
| `struct` | `Reflow` | `src/app/reflow.rs` |
| `struct` | `Resize` | `src/app/resize.rs` |
| `struct` | `Resume` | `src/app/resume.rs` |
| `struct` | `Stop` | `src/app/stop.rs` |
| `struct` | `Theme` | `src/app/theme.rs` |
| `struct` | `Title` | `src/app/title.rs` |
| `struct` | `UpdateProgress` | `src/app/update_progress.rs` |
| `struct` | `Arrow` | `src/cmp/arrow.rs` |
| `struct` | `Close` | `src/cmp/close.rs` |
| `struct` | `Show` | `src/cmp/show.rs` |
| `struct` | `Trigger` | `src/cmp/trigger.rs` |
| `struct` | `Ctx` | `src/context.rs` |
| `fn` | `new` | `src/context.rs` |
| `fn` | `renew` | `src/context.rs` |
| `fn` | `active` | `src/context.rs` |
| `fn` | `tabs` | `src/context.rs` |
| `fn` | `tabs_mut` | `src/context.rs` |
| `fn` | `tab` | `src/context.rs` |
| `fn` | `tab_mut` | `src/context.rs` |
| `fn` | `cwd` | `src/context.rs` |
| `fn` | `parent` | `src/context.rs` |
| `fn` | `parent_mut` | `src/context.rs` |
| `fn` | `current` | `src/context.rs` |
| `fn` | `current_mut` | `src/context.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
extern crate self as yazi_actor;

yazi_macro::mod_pub!(app cmp confirm core help input lives mgr notify pick spot tasks which);

yazi_macro::mod_flat!(actor context);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-binding`, `yazi-boot`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-parser`, `yazi-plugin`, `yazi-proxy`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-tui`, `yazi-vfs`, `yazi-watcher`, `yazi-widgets`

**Depended on by (workspace scan)**: `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-actor`.*
