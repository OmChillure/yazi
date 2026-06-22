# yazi-fs — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Local filesystem abstraction: directory reads, file ops, mounts, and provider traits for the manager.

> Cargo description: *Yazi file system*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-fs`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 48 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-ffi`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`

### External (sample)

`anyhow`, `arc-swap`, `bitflags`, `core-foundation-sys`, `dirs`, `either`, `foldhash`, `hashbrown`, `libc`, `mlua`, `objc2`, `parking_lot`, `percent-encoding`, `rand`, `regex`, `scopeguard`, `serde`, `strum`, `tokio`, `tracing`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/cha` |
| module/file | `src/cwd` |
| module/file | `src/error` |
| module/file | `src/file` |
| module/file | `src/files` |
| module/file | `src/filter` |
| module/file | `src/fns` |
| module/file | `src/hash` |
| module/file | `src/lib.rs` |
| module/file | `src/mounts` |
| module/file | `src/op` |
| module/file | `src/path` |
| module/file | `src/provider/local` |
| module/file | `src/provider` |
| module/file | `src/scheme` |
| module/file | `src/sorter` |
| module/file | `src/sorting` |
| module/file | `src/splatter` |
| module/file | `src/stage` |
| module/file | `src/url` |
| module/file | `src/xdg` |

### Notable source files

- `src/cha/cha.rs`
- `src/cha/kind.rs`
- `src/cha/mod.rs`
- `src/cha/mode.rs`
- `src/cha/type.rs`
- `src/cwd.rs`
- `src/error/error.rs`
- `src/error/mod.rs`
- `src/error/serde.rs`
- `src/file.rs`
- `src/files.rs`
- `src/filter.rs`
- `src/fns.rs`
- `src/hash.rs`
- `src/lib.rs`
- `src/mounts/linux.rs`
- `src/mounts/macos.rs`
- `src/mounts/mod.rs`
- `src/mounts/partition.rs`
- `src/mounts/partitions.rs`
- `src/op.rs`
- `src/path/clean.rs`
- `src/path/expand.rs`
- `src/path/mod.rs`
- `src/path/path.rs`
- `src/path/percent.rs`
- `src/path/relative.rs`
- `src/provider/attrs.rs`
- `src/provider/capabilities.rs`
- `src/provider/local/absolute.rs`
- _…and 18 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Cha` | `src/cha/cha.rs` |
| `fn` | `new` | `src/cha/cha.rs` |
| `fn` | `from_dummy` | `src/cha/cha.rs` |
| `fn` | `hits` | `src/cha/cha.rs` |
| `fn` | `attach` | `src/cha/cha.rs` |
| `fn` | `is_link` | `src/cha/cha.rs` |
| `fn` | `is_orphan` | `src/cha/cha.rs` |
| `const` | `fn` | `src/cha/cha.rs` |
| `fn` | `atime_dur` | `src/cha/cha.rs` |
| `fn` | `btime_dur` | `src/cha/cha.rs` |
| `fn` | `ctime_dur` | `src/cha/cha.rs` |
| `fn` | `mtime_dur` | `src/cha/cha.rs` |
| `struct` | `ChaKind` | `src/cha/kind.rs` |
| `fn` | `hidden` | `src/cha/kind.rs` |
| `struct` | `ChaMode` | `src/cha/mode.rs` |
| `fn` | `permissions` | `src/cha/mode.rs` |
| `fn` | `from_bare` | `src/cha/mode.rs` |
| `enum` | `ChaType` | `src/cha/type.rs` |
| `fn` | `is_file` | `src/cha/type.rs` |
| `fn` | `is_dir` | `src/cha/type.rs` |
| `fn` | `is_block` | `src/cha/type.rs` |
| `fn` | `is_char` | `src/cha/type.rs` |
| `fn` | `is_sock` | `src/cha/type.rs` |
| `fn` | `is_fifo` | `src/cha/type.rs` |
| `static` | `CWD` | `src/cwd.rs` |
| `struct` | `Cwd` | `src/cwd.rs` |
| `fn` | `path` | `src/cwd.rs` |
| `fn` | `set` | `src/cwd.rs` |
| `fn` | `ensure` | `src/cwd.rs` |
| `enum` | `Error` | `src/error/error.rs` |
| `fn` | `custom` | `src/error/error.rs` |
| `fn` | `kind` | `src/error/error.rs` |
| `fn` | `kind_str` | `src/error/error.rs` |
| `fn` | `raw_os_error` | `src/error/error.rs` |
| `fn` | `kind_to_str` | `src/error/serde.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(cha error mounts path provider);

yazi_macro::mod_flat!(cwd file files filter fns hash op scheme sorter sorting splatter stage url xdg);

pub fn init() {
	CWD.init(<_>::default());

	mounts::init();

	Xdg::load();
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-ffi`, `yazi-macro`, `yazi-shared`, `yazi-shim`

**Depended on by (workspace scan)**: `yazi-vfs`, `yazi-watcher`, `yazi-config`, `yazi-boot`, `yazi-adapter`, `yazi-dds`, `yazi-parser`, `yazi-binding`, `yazi-core`, `yazi-plugin`, `yazi-scheduler`, `yazi-runner`, `yazi-actor`, `yazi-fm`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-fs`.*
