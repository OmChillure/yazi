# yazi-runner — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Process/command runner abstractions for openers, shell, and external tool invocation.

> Cargo description: *Yazi Lua runner*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-runner`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 23 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-binding`
- `yazi-config`
- `yazi-dds`
- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-version`

### External (sample)

`anyhow`, `default`, `hashbrown`, `mlua`, `parking_lot`, `thiserror`, `tokio`, `tokio-util`, `tracing`, `vendored-lua`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/entry` |
| module/file | `src/fetcher` |
| module/file | `src/lib.rs` |
| module/file | `src/loader` |
| module/file | `src/preloader` |
| module/file | `src/previewer` |
| module/file | `src/runner` |
| module/file | `src/spot` |

### Notable source files

- `src/entry/entry.rs`
- `src/entry/job.rs`
- `src/entry/mod.rs`
- `src/fetcher/fetcher.rs`
- `src/fetcher/job.rs`
- `src/fetcher/mod.rs`
- `src/fetcher/state.rs`
- `src/lib.rs`
- `src/loader/chunk.rs`
- `src/loader/loader.rs`
- `src/loader/mod.rs`
- `src/loader/require.rs`
- `src/preloader/error.rs`
- `src/preloader/job.rs`
- `src/preloader/mod.rs`
- `src/preloader/preloader.rs`
- `src/preloader/state.rs`
- `src/previewer/error.rs`
- `src/previewer/job.rs`
- `src/previewer/mod.rs`
- `src/previewer/previewer.rs`
- `src/runner.rs`
- `src/spot.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `fn` | `entry` | `src/entry/entry.rs` |
| `struct` | `EntryJob` | `src/entry/job.rs` |
| `fn` | `fetch` | `src/fetcher/fetcher.rs` |
| `struct` | `FetchJob` | `src/fetcher/job.rs` |
| `enum` | `FetchState` | `src/fetcher/state.rs` |
| `fn` | `get` | `src/fetcher/state.rs` |
| `static` | `RUNNER` | `src/lib.rs` |
| `fn` | `init` | `src/lib.rs` |
| `struct` | `Chunk` | `src/loader/chunk.rs` |
| `fn` | `compatible` | `src/loader/chunk.rs` |
| `static` | `LOADER` | `src/loader/loader.rs` |
| `struct` | `Loader` | `src/loader/loader.rs` |
| `fn` | `ensure` | `src/loader/loader.rs` |
| `fn` | `load` | `src/loader/loader.rs` |
| `fn` | `load_chunk` | `src/loader/loader.rs` |
| `fn` | `try_load` | `src/loader/loader.rs` |
| `fn` | `compatible_or_error` | `src/loader/loader.rs` |
| `fn` | `install` | `src/loader/mod.rs` |
| `struct` | `Require` | `src/loader/require.rs` |
| `enum` | `PreloadError` | `src/preloader/error.rs` |
| `struct` | `PreloadJob` | `src/preloader/job.rs` |
| `fn` | `preload` | `src/preloader/preloader.rs` |
| `struct` | `PreloadState` | `src/preloader/state.rs` |
| `enum` | `PeekError` | `src/previewer/error.rs` |
| `struct` | `PeekJob` | `src/previewer/job.rs` |
| `struct` | `SeekJob` | `src/previewer/job.rs` |
| `fn` | `peek` | `src/previewer/previewer.rs` |
| `struct` | `Runner` | `src/runner.rs` |
| `fn` | `spawn` | `src/runner.rs` |
| `fn` | `spot` | `src/spot.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(entry fetcher loader preloader previewer);

yazi_macro::mod_flat!(runner spot);

pub static RUNNER: yazi_shim::cell::RoCell<Runner> = yazi_shim::cell::RoCell::new();

pub fn init(setter: fn(&mlua::Lua) -> mlua::Result<()>) {
	crate::loader::init();

	RUNNER.init(Runner { setter });
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`

**Depended on by (workspace scan)**: `yazi-core`, `yazi-plugin`, `yazi-scheduler`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-runner`.*
