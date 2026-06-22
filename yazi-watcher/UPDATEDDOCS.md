# yazi-watcher — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Filesystem watch/notify integration so the manager can refresh when the disk changes.

> Cargo description: *Yazi file watcher*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-watcher`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 12 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-adapter`
- `yazi-dds`
- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-vfs`

### External (sample)

`futures`, `hashbrown`, `notify`, `parking_lot`, `percent-encoding`, `tokio`, `tokio-stream`, `tracing`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/backend` |
| module/file | `src/lib.rs` |
| module/file | `src/local` |
| module/file | `src/proxy` |
| module/file | `src/remote` |
| module/file | `src/reporter` |
| module/file | `src/watched` |
| module/file | `src/watchee` |
| module/file | `src/watcher` |

### Notable source files

- `src/backend.rs`
- `src/lib.rs`
- `src/local/linked.rs`
- `src/local/local.rs`
- `src/local/mod.rs`
- `src/proxy.rs`
- `src/remote/mod.rs`
- `src/remote/remote.rs`
- `src/reporter.rs`
- `src/watched.rs`
- `src/watchee.rs`
- `src/watcher.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Backend` | `src/backend.rs` |
| `fn` | `serve` | `src/backend.rs` |
| `fn` | `watch` | `src/backend.rs` |
| `fn` | `unwatch` | `src/backend.rs` |
| `fn` | `sync` | `src/backend.rs` |
| `static` | `WATCHED` | `src/lib.rs` |
| `static` | `WATCHER` | `src/lib.rs` |
| `fn` | `init` | `src/lib.rs` |
| `struct` | `Linked` | `src/local/linked.rs` |
| `fn` | `from_dir` | `src/local/linked.rs` |
| `fn` | `from_file` | `src/local/linked.rs` |
| `struct` | `Local` | `src/local/local.rs` |
| `fn` | `soundless` | `src/local/local.rs` |
| `static` | `LINKED` | `src/local/mod.rs` |
| `struct` | `MgrProxy` | `src/proxy.rs` |
| `fn` | `refresh` | `src/proxy.rs` |
| `fn` | `upload` | `src/proxy.rs` |
| `struct` | `Remote` | `src/remote/remote.rs` |
| `struct` | `Reporter` | `src/reporter.rs` |
| `fn` | `report` | `src/reporter.rs` |
| `struct` | `Watched` | `src/watched.rs` |
| `fn` | `contains_url` | `src/watched.rs` |
| `fn` | `contains_path` | `src/watched.rs` |
| `fn` | `paths` | `src/watched.rs` |
| `fn` | `find_by_cache` | `src/watched.rs` |
| `enum` | `Watchee` | `src/watchee.rs` |
| `fn` | `as_local` | `src/watchee.rs` |
| `fn` | `as_local_mut` | `src/watchee.rs` |
| `fn` | `new` | `src/watchee.rs` |
| `fn` | `to_static` | `src/watchee.rs` |
| `struct` | `Watcher` | `src/watcher.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(local remote);

yazi_macro::mod_flat!(backend proxy reporter watched watchee watcher);

pub static WATCHED: yazi_shim::cell::RoCell<parking_lot::RwLock<Watched>> =
	yazi_shim::cell::RoCell::new();
pub static WATCHER: yazi_shim::cell::RoCell<tokio::sync::Semaphore> =
	yazi_shim::cell::RoCell::new();

pub fn init() {
	WATCHED.with(<_>::default);
	WATCHER.init(tokio::sync::Semaphore::new(1));

	local::init();
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-adapter`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-vfs`

**Depended on by (workspace scan)**: `yazi-core`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-watcher`.*
