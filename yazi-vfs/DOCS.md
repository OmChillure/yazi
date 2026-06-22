# yazi-vfs

## Purpose

Virtual filesystem layer unifying local + SFTP providers for list/read/write/copy operations.

**Crate description (Cargo.toml):** Yazi virtual file system

## Dependencies (workspace)

`yazi-config`, `yazi-fs`, `yazi-macro`, `yazi-sftp`, `yazi-shared`, `yazi-shim`

## Module map

Public/internal modules exported from the crate root:

- `provider`
- `cha`
- `file`
- `files`
- `fns`
- `op`

## Main files

- `src/lib.rs` — entry/core
- `src/cha.rs` (file)
- `src/file.rs` (file)
- `src/files.rs` (file)
- `src/fns.rs` (file)
- `src/lib.rs` (file)
- `src/op.rs` (file)
- `src/provider` (dir)

## Key public items

- **src/cha.rs**: `trait VfsCha`
- **src/file.rs**: `trait VfsFile`
- **src/files.rs**: `trait VfsFiles`
- **src/fns.rs**: `fn maybe_exists`, `fn unique_file`
- **src/lib.rs**: `fn init`
- **src/op.rs**: `trait VfsFilesOp`
- **src/provider/calculator.rs**: `enum SizeCalculator`
- **src/provider/dir_entry.rs**: `enum DirEntry`
- **src/provider/gate.rs**: `struct Gate`
- **src/provider/provider.rs**: `fn absolute`, `fn calculate`, `fn canonicalize`, `fn capabilities`, `fn casefold`, `fn copy`, `fn copy_with_progress`, `fn create`
- **src/provider/read_dir.rs**: `enum ReadDir`
- **src/provider/rw_file.rs**: `enum RwFile`
- **src/provider/sftp/absolute.rs**: `fn try_absolute`
- **src/provider/sftp/gate.rs**: `struct Gate`
- **src/provider/sftp/read_dir.rs**: `struct ReadDir`, `struct DirEntry`
- **src/provider/sftp/sftp.rs**: `struct Sftp`

## Source layout (partial)

```
src/cha.rs
src/file.rs
src/files.rs
src/fns.rs
src/lib.rs
src/op.rs
src/provider/calculator.rs
src/provider/copier.rs
src/provider/dir_entry.rs
src/provider/gate.rs
src/provider/mod.rs
src/provider/provider.rs
src/provider/providers.rs
src/provider/read_dir.rs
src/provider/rw_file.rs
src/provider/sftp/absolute.rs
src/provider/sftp/conn.rs
src/provider/sftp/gate.rs
src/provider/sftp/metadata.rs
src/provider/sftp/mod.rs
src/provider/sftp/read_dir.rs
src/provider/sftp/sftp.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
