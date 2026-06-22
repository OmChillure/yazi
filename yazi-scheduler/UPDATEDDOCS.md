# yazi-scheduler — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Async task scheduler for copy/move/delete/download/preview jobs with progress reporting.

> Cargo description: *Yazi task scheduler*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-scheduler`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 56 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-binding`
- `yazi-config`
- `yazi-dds`
- `yazi-fs`
- `yazi-macro`
- `yazi-runner`
- `yazi-shared`
- `yazi-term`
- `yazi-vfs`

### External (sample)

`anyhow`, `async-priority-channel`, `default`, `foldhash`, `hashbrown`, `libc`, `lru`, `mlua`, `ordered-float`, `parking_lot`, `serde`, `strum`, `tokio`, `tracing`, `vendored-lua`, `workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `macros` | — |

### Notable source files

- `src/behavior.rs`
- `src/cleanup.rs`
- `src/fetch/fetch.rs`
- `src/fetch/in.rs`
- `src/fetch/mod.rs`
- `src/fetch/out.rs`
- `src/fetch/progress.rs`
- `src/file/file.rs`
- `src/file/in.rs`
- `src/file/macros.rs`
- `src/file/mod.rs`
- `src/file/out.rs`
- `src/file/progress.rs`
- `src/file/transaction.rs`
- `src/file/traverse.rs`
- `src/hook/hook.rs`
- `src/hook/in.rs`
- `src/hook/macros.rs`
- `src/hook/mod.rs`
- `src/in.rs`
- `src/lib.rs`
- `src/macros.rs`
- `src/ongoing.rs`
- `src/op.rs`
- `src/out.rs`
- `src/plugin/in.rs`
- `src/plugin/macros.rs`
- `src/plugin/mod.rs`
- `src/plugin/out.rs`
- `src/plugin/plugin.rs`
- _…and 26 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Behavior` | `src/behavior.rs` |
| `fn` | `new` | `src/behavior.rs` |
| `fn` | `update` | `src/behavior.rs` |
| `fn` | `reset` | `src/behavior.rs` |
| `fn` | `first_id` | `src/behavior.rs` |
| `enum` | `CleanupState` | `src/cleanup.rs` |
| `struct` | `Fetch` | `src/fetch/fetch.rs` |
| `fn` | `fetch` | `src/fetch/fetch.rs` |
| `fn` | `submit` | `src/fetch/fetch.rs` |
| `struct` | `FetchIn` | `src/fetch/in.rs` |
| `enum` | `FetchOutFetch` | `src/fetch/out.rs` |
| `fn` | `reduce` | `src/fetch/out.rs` |
| `struct` | `FetchProg` | `src/fetch/progress.rs` |
| `struct` | `File` | `src/file/file.rs` |
| `fn` | `copy` | `src/file/file.rs` |
| `fn` | `copy_do` | `src/file/file.rs` |
| `fn` | `cut` | `src/file/file.rs` |
| `fn` | `cut_do` | `src/file/file.rs` |
| `fn` | `link` | `src/file/file.rs` |
| `fn` | `link_do` | `src/file/file.rs` |
| `fn` | `hardlink` | `src/file/file.rs` |
| `fn` | `hardlink_do` | `src/file/file.rs` |
| `fn` | `delete` | `src/file/file.rs` |
| `fn` | `delete_do` | `src/file/file.rs` |
| `fn` | `trash` | `src/file/file.rs` |
| `fn` | `trash_do` | `src/file/file.rs` |
| `fn` | `download` | `src/file/file.rs` |
| `fn` | `download_do` | `src/file/file.rs` |
| `fn` | `upload` | `src/file/file.rs` |
| `fn` | `upload_do` | `src/file/file.rs` |
| `fn` | `cha` | `src/file/file.rs` |
| `enum` | `FileIn` | `src/file/in.rs` |
| `fn` | `into_doable` | `src/file/in.rs` |
| `struct` | `FileInCopy` | `src/file/in.rs` |
| `fn` | `into_link` | `src/file/in.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
mod macros;

yazi_macro::mod_pub!(fetch file hook plugin preload process size);

yazi_macro::mod_flat!(behavior cleanup ongoing op out progress proxy r#in scheduler snap summary task worker);

const LOW: u8 = yazi_config::Priority::Low as u8;
const NORMAL: u8 = yazi_config::Priority::Normal as u8;
const HIGH: u8 = yazi_config::Priority::High as u8;
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-runner`, `yazi-shared`, `yazi-term`, `yazi-vfs`

**Depended on by (workspace scan)**: `yazi-proxy`, `yazi-parser`, `yazi-core`, `yazi-plugin`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-scheduler`.*
