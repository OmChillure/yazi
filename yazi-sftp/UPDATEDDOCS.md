# yazi-sftp — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

SFTP client integration used by the VFS for remote browsing and transfers.

> Cargo description: *Yazi SFTP client*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-sftp`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `LICENSE`, `README.md`
- **Rust sources under `src/`**: 45 files

## 3. Dependencies

### Workspace / Yazi crates

- _(none or only indirect)_

### External (sample)

`bitflags`, `parking_lot`, `russh`, `serde`, `tokio`, `typed-path`, `workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `fs` | — |
| `requests` | — |
| `responses` | — |
| `de` | — |
| `error` | — |
| `id` | — |
| `macros` | — |
| `operator` | — |
| `packet` | — |
| `path` | — |
| `receiver` | — |
| `ser` | — |
| `session` | — |

### Notable source files

- `src/de.rs`
- `src/error.rs`
- `src/fs/attrs.rs`
- `src/fs/dir_entry.rs`
- `src/fs/file.rs`
- `src/fs/flags.rs`
- `src/fs/mod.rs`
- `src/fs/read_dir.rs`
- `src/id.rs`
- `src/lib.rs`
- `src/macros.rs`
- `src/operator.rs`
- `src/packet.rs`
- `src/path.rs`
- `src/receiver.rs`
- `src/requests/close.rs`
- `src/requests/extended.rs`
- `src/requests/fstat.rs`
- `src/requests/init.rs`
- `src/requests/lstat.rs`
- `src/requests/mkdir.rs`
- `src/requests/mod.rs`
- `src/requests/open.rs`
- `src/requests/open_dir.rs`
- `src/requests/read.rs`
- `src/requests/read_dir.rs`
- `src/requests/readlink.rs`
- `src/requests/realpath.rs`
- `src/requests/remove.rs`
- `src/requests/rename.rs`
- _…and 15 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Deserializer` | `src/de.rs` |
| `fn` | `once` | `src/de.rs` |
| `enum` | `Error` | `src/error.rs` |
| `fn` | `serde` | `src/error.rs` |
| `fn` | `custom` | `src/error.rs` |
| `struct` | `Attrs` | `src/fs/attrs.rs` |
| `fn` | `is_empty` | `src/fs/attrs.rs` |
| `fn` | `len` | `src/fs/attrs.rs` |
| `struct` | `DirEntry` | `src/fs/dir_entry.rs` |
| `fn` | `path` | `src/fs/dir_entry.rs` |
| `fn` | `name` | `src/fs/dir_entry.rs` |
| `fn` | `long_name` | `src/fs/dir_entry.rs` |
| `fn` | `attrs` | `src/fs/dir_entry.rs` |
| `fn` | `nlink` | `src/fs/dir_entry.rs` |
| `fn` | `user` | `src/fs/dir_entry.rs` |
| `fn` | `group` | `src/fs/dir_entry.rs` |
| `struct` | `File` | `src/fs/file.rs` |
| `fn` | `new` | `src/fs/file.rs` |
| `fn` | `fstat` | `src/fs/file.rs` |
| `fn` | `fsetstat` | `src/fs/file.rs` |
| `struct` | `Flags` | `src/fs/flags.rs` |
| `struct` | `ReadDir` | `src/fs/read_dir.rs` |
| `fn` | `next` | `src/fs/read_dir.rs` |
| `struct` | `Id` | `src/id.rs` |
| `mod` | `fs` | `src/lib.rs` |
| `mod` | `requests` | `src/lib.rs` |
| `mod` | `responses` | `src/lib.rs` |
| `struct` | `Operator` | `src/operator.rs` |
| `fn` | `make` | `src/operator.rs` |
| `fn` | `init` | `src/operator.rs` |
| `fn` | `open` | `src/operator.rs` |
| `fn` | `close` | `src/operator.rs` |
| `fn` | `read` | `src/operator.rs` |
| `fn` | `write` | `src/operator.rs` |
| `fn` | `lstat` | `src/operator.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
pub mod fs;
pub mod requests;
pub mod responses;

mod de;
mod error;
mod id;
mod macros;
mod operator;
mod packet;
mod path;
mod receiver;
mod ser;
mod session;

pub(crate) use de::*;
pub use error::*;
pub(crate) use id::*;
pub use operator::*;
pub use packet::*;
pub use path::*;
pub use receiver::*;
pub(crate) use ser::*;
pub use session::*;
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: _none_

**Depended on by (workspace scan)**: `yazi-vfs`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-sftp`.*
