# yazi-core — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Core manager domain: tabs, files, folders, yank, spot, find, and manager state machines.

> Cargo description: *Yazi core logic*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-core`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 60 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-adapter`
- `yazi-binding`
- `yazi-config`
- `yazi-dds`
- `yazi-fs`
- `yazi-macro`
- `yazi-prebuilt`
- `yazi-runner`
- `yazi-scheduler`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-vfs`
- `yazi-watcher`
- `yazi-widgets`

### External (sample)

`anyhow`, `default`, `dyn-clone`, `hashbrown`, `indexmap`, `mlua`, `parking_lot`, `ratatui`, `serde`, `serde_with`, `strum`, `syntect`, `tokio`, `tokio-stream`, `tokio-util`, `tracing`, `unicode-width`, `vendored-lua`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/app` |
| module/file | `src/cmp` |
| module/file | `src/confirm` |
| module/file | `src/core` |
| module/file | `src/help` |
| module/file | `src/highlighter` |
| module/file | `src/input` |
| module/file | `src/lib.rs` |
| module/file | `src/mgr` |
| module/file | `src/notify` |
| module/file | `src/pick` |
| module/file | `src/proxy` |
| module/file | `src/spot` |
| module/file | `src/tab` |
| module/file | `src/tasks` |
| module/file | `src/which` |

### Notable source files

- `src/app/mod.rs`
- `src/app/plugin.rs`
- `src/app/quit.rs`
- `src/cmp/cmp.rs`
- `src/cmp/item.rs`
- `src/cmp/mod.rs`
- `src/cmp/option.rs`
- `src/confirm/confirm.rs`
- `src/confirm/mod.rs`
- `src/core.rs`
- `src/help/help.rs`
- `src/help/mod.rs`
- `src/highlighter.rs`
- `src/input/input.rs`
- `src/input/mod.rs`
- `src/lib.rs`
- `src/mgr/batcher.rs`
- `src/mgr/cd.rs`
- `src/mgr/displace.rs`
- `src/mgr/filter.rs`
- `src/mgr/find.rs`
- `src/mgr/mgr.rs`
- `src/mgr/mimetype.rs`
- `src/mgr/mod.rs`
- `src/mgr/open.rs`
- `src/mgr/search.rs`
- `src/mgr/tabs.rs`
- `src/mgr/yanked.rs`
- `src/notify/level.rs`
- `src/notify/message.rs`
- _…and 30 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `PluginOpt` | `src/app/plugin.rs` |
| `fn` | `new_callback` | `src/app/plugin.rs` |
| `enum` | `PluginMode` | `src/app/plugin.rs` |
| `fn` | `auto_then` | `src/app/plugin.rs` |
| `trait` | `PluginCallback` | `src/app/plugin.rs` |
| `struct` | `QuitOpt` | `src/app/quit.rs` |
| `struct` | `Cmp` | `src/cmp/cmp.rs` |
| `fn` | `window` | `src/cmp/cmp.rs` |
| `fn` | `selected` | `src/cmp/cmp.rs` |
| `fn` | `rel_cursor` | `src/cmp/cmp.rs` |
| `struct` | `CmpItem` | `src/cmp/item.rs` |
| `struct` | `CmpOpt` | `src/cmp/option.rs` |
| `struct` | `Confirm` | `src/confirm/confirm.rs` |
| `struct` | `Core` | `src/core.rs` |
| `fn` | `make` | `src/core.rs` |
| `fn` | `cursor` | `src/core.rs` |
| `fn` | `layer` | `src/core.rs` |
| `fn` | `active` | `src/core.rs` |
| `fn` | `active_mut` | `src/core.rs` |
| `fn` | `current_mut` | `src/core.rs` |
| `fn` | `parent_mut` | `src/core.rs` |
| `struct` | `Help` | `src/help/help.rs` |
| `fn` | `r` | `src/help/help.rs` |
| `fn` | `filter_apply` | `src/help/help.rs` |
| `fn` | `keyword` | `src/help/help.rs` |
| `fn` | `cursor_shape` | `src/help/help.rs` |
| `struct` | `Highlighter` | `src/highlighter.rs` |
| `fn` | `oneshot` | `src/highlighter.rs` |
| `fn` | `abort` | `src/highlighter.rs` |
| `struct` | `Input` | `src/input/input.rs` |
| `struct` | `Batcher` | `src/mgr/batcher.rs` |
| `fn` | `prime` | `src/mgr/batcher.rs` |
| `fn` | `drain` | `src/mgr/batcher.rs` |
| `fn` | `decide` | `src/mgr/batcher.rs` |
| `enum` | `CdSource` | `src/mgr/cd.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(app cmp confirm help input mgr notify pick spot tab tasks which);

yazi_macro::mod_flat!(core highlighter proxy);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-adapter`, `yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-prebuilt`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-vfs`, `yazi-watcher`, `yazi-widgets`

**Depended on by (workspace scan)**: `yazi-proxy`, `yazi-parser`, `yazi-plugin`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-core`.*
