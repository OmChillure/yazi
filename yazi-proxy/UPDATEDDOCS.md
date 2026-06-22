# yazi-proxy — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Proxied command/event surfaces so plugins and actors can request manager actions without tight coupling.

> Cargo description: *Yazi event proxy*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-proxy`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 11 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-config`
- `yazi-core`
- `yazi-macro`
- `yazi-scheduler`
- `yazi-shared`
- `yazi-shim`
- `yazi-widgets`

### External (sample)

`anyhow`, `tokio`, `workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `macros` | — |

### Notable source files

- `src/app.rs`
- `src/cmp.rs`
- `src/confirm.rs`
- `src/input.rs`
- `src/lib.rs`
- `src/macros.rs`
- `src/mgr.rs`
- `src/notify.rs`
- `src/pick.rs`
- `src/tasks.rs`
- `src/which.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `AppProxy` | `src/app.rs` |
| `fn` | `quit` | `src/app.rs` |
| `fn` | `plugin_do` | `src/app.rs` |
| `struct` | `CmpProxy` | `src/cmp.rs` |
| `fn` | `show` | `src/cmp.rs` |
| `fn` | `trigger` | `src/cmp.rs` |
| `struct` | `ConfirmProxy` | `src/confirm.rs` |
| `fn` | `show_sync` | `src/confirm.rs` |
| `struct` | `InputProxy` | `src/input.rs` |
| `struct` | `MgrProxy` | `src/mgr.rs` |
| `fn` | `arrow` | `src/mgr.rs` |
| `fn` | `cd` | `src/mgr.rs` |
| `fn` | `displace_do` | `src/mgr.rs` |
| `fn` | `filter_do` | `src/mgr.rs` |
| `fn` | `find_do` | `src/mgr.rs` |
| `fn` | `open` | `src/mgr.rs` |
| `fn` | `open_do` | `src/mgr.rs` |
| `fn` | `remove_do` | `src/mgr.rs` |
| `fn` | `reveal` | `src/mgr.rs` |
| `fn` | `search_do` | `src/mgr.rs` |
| `fn` | `tab_rename` | `src/mgr.rs` |
| `fn` | `update_spotted` | `src/mgr.rs` |
| `struct` | `NotifyProxy` | `src/notify.rs` |
| `fn` | `push` | `src/notify.rs` |
| `fn` | `tick` | `src/notify.rs` |
| `struct` | `PickProxy` | `src/pick.rs` |
| `struct` | `TasksProxy` | `src/tasks.rs` |
| `fn` | `spawn` | `src/tasks.rs` |
| `fn` | `open_shell_compat` | `src/tasks.rs` |
| `fn` | `process_exec` | `src/tasks.rs` |
| `struct` | `WhichProxy` | `src/which.rs` |
| `fn` | `activate` | `src/which.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
mod macros;

yazi_macro::mod_flat!(app cmp confirm input mgr notify pick tasks which);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-config`, `yazi-core`, `yazi-macro`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-widgets`

**Depended on by (workspace scan)**: `yazi-plugin`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-proxy`.*
