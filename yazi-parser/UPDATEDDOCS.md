# yazi-parser — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Parsing for actions, keymaps, shell fragments, and other structured input feeding the executor.

> Cargo description: *Yazi form parser*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-parser`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 88 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-binding`
- `yazi-boot`
- `yazi-config`
- `yazi-core`
- `yazi-dds`
- `yazi-fs`
- `yazi-macro`
- `yazi-scheduler`
- `yazi-shared`
- `yazi-term`
- `yazi-vfs`
- `yazi-widgets`

### External (sample)

`anyhow`, `bitflags`, `default`, `hashbrown`, `mlua`, `paste`, `ratatui`, `serde`, `serde_with`, `strum`, `tokio`, `vendored-lua`, `workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `macros` | — |

### Notable source files

- `src/app/deprecate.rs`
- `src/app/dnd.rs`
- `src/app/lua.rs`
- `src/app/mod.rs`
- `src/app/mouse.rs`
- `src/app/plugin.rs`
- `src/app/quit.rs`
- `src/app/reflow.rs`
- `src/app/title.rs`
- `src/app/update_progress.rs`
- `src/arrow.rs`
- `src/cmp/close.rs`
- `src/cmp/mod.rs`
- `src/cmp/show.rs`
- `src/cmp/trigger.rs`
- `src/confirm/close.rs`
- `src/confirm/mod.rs`
- `src/confirm/show.rs`
- `src/help/mod.rs`
- `src/help/toggle.rs`
- `src/input/close.rs`
- `src/input/mod.rs`
- `src/lib.rs`
- `src/macros.rs`
- `src/mgr/bulk_exit.rs`
- `src/mgr/cd.rs`
- `src/mgr/close.rs`
- `src/mgr/copy.rs`
- `src/mgr/create.rs`
- `src/mgr/displace_do.rs`
- _…and 58 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `DeprecateForm` | `src/app/deprecate.rs` |
| `struct` | `DndForm` | `src/app/dnd.rs` |
| `struct` | `LuaForm` | `src/app/lua.rs` |
| `struct` | `MouseForm` | `src/app/mouse.rs` |
| `struct` | `PluginForm` | `src/app/plugin.rs` |
| `struct` | `QuitForm` | `src/app/quit.rs` |
| `struct` | `ReflowForm` | `src/app/reflow.rs` |
| `struct` | `TitleForm` | `src/app/title.rs` |
| `struct` | `UpdateProgressForm` | `src/app/update_progress.rs` |
| `struct` | `ArrowForm` | `src/arrow.rs` |
| `struct` | `CloseForm` | `src/cmp/close.rs` |
| `struct` | `ShowForm` | `src/cmp/show.rs` |
| `struct` | `TriggerForm` | `src/cmp/trigger.rs` |
| `struct` | `ToggleForm` | `src/help/toggle.rs` |
| `struct` | `BulkExitForm` | `src/mgr/bulk_exit.rs` |
| `struct` | `CdForm` | `src/mgr/cd.rs` |
| `struct` | `CopyForm` | `src/mgr/copy.rs` |
| `enum` | `CopySeparator` | `src/mgr/copy.rs` |
| `fn` | `transform` | `src/mgr/copy.rs` |
| `struct` | `CreateForm` | `src/mgr/create.rs` |
| `struct` | `DisplaceDoForm` | `src/mgr/displace_do.rs` |
| `struct` | `DownloadForm` | `src/mgr/download.rs` |
| `struct` | `EscapeForm` | `src/mgr/escape.rs` |
| `struct` | `FilterForm` | `src/mgr/filter.rs` |
| `struct` | `FindForm` | `src/mgr/find.rs` |
| `struct` | `FindArrowForm` | `src/mgr/find_arrow.rs` |
| `struct` | `FindDoForm` | `src/mgr/find_do.rs` |
| `struct` | `HardlinkForm` | `src/mgr/hardlink.rs` |
| `struct` | `HiddenForm` | `src/mgr/hidden.rs` |
| `enum` | `HiddenFormState` | `src/mgr/hidden.rs` |
| `fn` | `bool` | `src/mgr/hidden.rs` |
| `struct` | `HoverForm` | `src/mgr/hover.rs` |
| `struct` | `LinemodeForm` | `src/mgr/linemode.rs` |
| `struct` | `LinkForm` | `src/mgr/link.rs` |
| `struct` | `OpenForm` | `src/mgr/open.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
mod macros;

yazi_macro::mod_pub!(app cmp confirm help input mgr notify pick spark spot tasks which);

yazi_macro::mod_flat!(arrow void);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-binding`, `yazi-boot`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-scheduler`, `yazi-shared`, `yazi-term`, `yazi-vfs`, `yazi-widgets`

**Depended on by (workspace scan)**: `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-parser`.*
