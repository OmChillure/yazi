# yazi-sftp

## Purpose

SFTP protocol client types and operations backing remote VFS providers.

**Crate description (Cargo.toml):** Yazi SFTP client

## Dependencies (workspace)

_none (leaf or external-only)_

## Module map

Public/internal modules exported from the crate root:

_See `src/lib.rs` or `src/main.rs`._

## Main files

- `src/lib.rs` — entry/core
- `src/de.rs` (file)
- `src/error.rs` (file)
- `src/fs` (dir)
- `src/id.rs` (file)
- `src/lib.rs` (file)
- `src/macros.rs` (file)
- `src/operator.rs` (file)
- `src/packet.rs` (file)
- `src/path.rs` (file)
- `src/receiver.rs` (file)
- `src/requests` (dir)
- `src/responses` (dir)
- `src/ser.rs` (file)
- `src/session.rs` (file)

## Key public items

- **src/error.rs**: `enum Error`
- **src/fs/attrs.rs**: `struct Attrs`
- **src/fs/dir_entry.rs**: `struct DirEntry`
- **src/fs/file.rs**: `struct File`
- **src/fs/flags.rs**: `struct Flags`
- **src/fs/read_dir.rs**: `struct ReadDir`
- **src/operator.rs**: `struct Operator`
- **src/packet.rs**: `enum Packet`, `fn to_bytes`, `fn from_bytes`
- **src/path.rs**: `enum SftpPath`, `trait AsSftpPath`
- **src/receiver.rs**: `struct Receiver`
- **src/requests/close.rs**: `struct Close`
- **src/requests/extended.rs**: `struct Extended`, `trait ExtendedData`, `struct ExtendedRename`, `struct ExtendedFsync`, `struct ExtendedHardlink`, `struct ExtendedLimits`
- **src/requests/fstat.rs**: `struct Fstat`
- **src/requests/init.rs**: `struct Init`
- **src/requests/lstat.rs**: `struct Lstat`
- **src/requests/mkdir.rs**: `struct Mkdir`
- **src/requests/open.rs**: `struct Open`
- **src/requests/open_dir.rs**: `struct OpenDir`
- **src/requests/read.rs**: `struct Read`
- **src/requests/read_dir.rs**: `struct ReadDir`
- **src/requests/readlink.rs**: `struct Readlink`
- **src/requests/realpath.rs**: `struct Realpath`
- **src/requests/remove.rs**: `struct Remove`
- **src/requests/rename.rs**: `struct Rename`
- **src/requests/rmdir.rs**: `struct Rmdir`

## Source layout (partial)

```
src/de.rs
src/error.rs
src/fs/attrs.rs
src/fs/dir_entry.rs
src/fs/file.rs
src/fs/flags.rs
src/fs/mod.rs
src/fs/read_dir.rs
src/id.rs
src/lib.rs
src/macros.rs
src/operator.rs
src/packet.rs
src/path.rs
src/receiver.rs
src/requests/close.rs
src/requests/extended.rs
src/requests/fstat.rs
src/requests/init.rs
src/requests/lstat.rs
src/requests/mkdir.rs
src/requests/mod.rs
src/requests/open.rs
src/requests/open_dir.rs
src/requests/read.rs
src/requests/read_dir.rs
src/requests/readlink.rs
src/requests/realpath.rs
src/requests/remove.rs
src/requests/rename.rs
src/requests/rmdir.rs
src/requests/set_stat.rs
src/requests/stat.rs
src/requests/symlink.rs
src/requests/write.rs
src/responses/attrs.rs
src/responses/data.rs
src/responses/extended.rs
src/responses/handle.rs
src/responses/mod.rs
src/responses/name.rs
src/responses/status.rs
src/responses/version.rs
src/ser.rs
src/session.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
