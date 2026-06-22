# yazi-vfs — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Virtual filesystem layer unifying local, archive, SFTP, and other schemes behind one API.

> Cargo description: *Yazi virtual file system*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-vfs`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 22 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-config`
- `yazi-fs`
- `yazi-macro`
- `yazi-sftp`
- `yazi-shared`
- `yazi-shim`

### External (sample)

`anyhow`, `chrono`, `deadpool`, `either`, `futures`, `hashbrown`, `parking_lot`, `russh`, `tokio`, `tracing`, `typed-path`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/cha` |
| module/file | `src/file` |
| module/file | `src/files` |
| module/file | `src/fns` |
| module/file | `src/lib.rs` |
| module/file | `src/op` |
| module/file | `src/provider` |
| module/file | `src/provider/sftp` |

### Notable source files

- `src/cha.rs`
- `src/file.rs`
- `src/files.rs`
- `src/fns.rs`
- `src/lib.rs`
- `src/op.rs`
- `src/provider/calculator.rs`
- `src/provider/copier.rs`
- `src/provider/dir_entry.rs`
- `src/provider/gate.rs`
- `src/provider/mod.rs`
- `src/provider/provider.rs`
- `src/provider/providers.rs`
- `src/provider/read_dir.rs`
- `src/provider/rw_file.rs`
- `src/provider/sftp/absolute.rs`
- `src/provider/sftp/conn.rs`
- `src/provider/sftp/gate.rs`
- `src/provider/sftp/metadata.rs`
- `src/provider/sftp/mod.rs`
- `src/provider/sftp/read_dir.rs`
- `src/provider/sftp/sftp.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `trait` | `VfsCha` | `src/cha.rs` |
| `trait` | `VfsFile` | `src/file.rs` |
| `trait` | `VfsFiles` | `src/files.rs` |
| `fn` | `maybe_exists` | `src/fns.rs` |
| `fn` | `unique_file` | `src/fns.rs` |
| `fn` | `init` | `src/lib.rs` |
| `trait` | `VfsFilesOp` | `src/op.rs` |
| `enum` | `SizeCalculator` | `src/provider/calculator.rs` |
| `fn` | `new` | `src/provider/calculator.rs` |
| `fn` | `cha` | `src/provider/calculator.rs` |
| `fn` | `total` | `src/provider/calculator.rs` |
| `fn` | `next` | `src/provider/calculator.rs` |
| `fn` | `copy_impl` | `src/provider/copier.rs` |
| `fn` | `copy_with_progress_impl` | `src/provider/copier.rs` |
| `enum` | `DirEntry` | `src/provider/dir_entry.rs` |
| `struct` | `Gate` | `src/provider/gate.rs` |
| `fn` | `absolute` | `src/provider/provider.rs` |
| `fn` | `calculate` | `src/provider/provider.rs` |
| `fn` | `canonicalize` | `src/provider/provider.rs` |
| `fn` | `capabilities` | `src/provider/provider.rs` |
| `fn` | `casefold` | `src/provider/provider.rs` |
| `fn` | `copy` | `src/provider/provider.rs` |
| `fn` | `copy_with_progress` | `src/provider/provider.rs` |
| `fn` | `create` | `src/provider/provider.rs` |
| `fn` | `create_dir` | `src/provider/provider.rs` |
| `fn` | `create_dir_all` | `src/provider/provider.rs` |
| `fn` | `create_new` | `src/provider/provider.rs` |
| `fn` | `hard_link` | `src/provider/provider.rs` |
| `fn` | `identical` | `src/provider/provider.rs` |
| `fn` | `metadata` | `src/provider/provider.rs` |
| `fn` | `must_identical` | `src/provider/provider.rs` |
| `fn` | `open` | `src/provider/provider.rs` |
| `fn` | `read_dir` | `src/provider/provider.rs` |
| `fn` | `read_link` | `src/provider/provider.rs` |
| `fn` | `remove_dir` | `src/provider/provider.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(provider);

yazi_macro::mod_flat!(cha file files fns op);

pub fn init() { provider::init(); }
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-config`, `yazi-fs`, `yazi-macro`, `yazi-sftp`, `yazi-shared`, `yazi-shim`

**Depended on by (workspace scan)**: `yazi-watcher`, `yazi-boot`, `yazi-parser`, `yazi-binding`, `yazi-core`, `yazi-plugin`, `yazi-scheduler`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-vfs`.*
