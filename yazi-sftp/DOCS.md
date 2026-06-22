# yazi-sftp

## Purpose

Standalone SFTP client implementation over SSH (`russh`). Implements packet codec, session/operator API, request/response types, and FS-like helpers so `yazi-vfs` can treat remote paths like local ones.

## Dependencies

- External: `bitflags`, `parking_lot`, `russh`, `serde`, `tokio`, `typed-path`
- No other Yazi crates (reusable/isolated)

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Public exports |
| `src/session.rs` | SFTP session lifecycle |
| `src/operator.rs` | High-level SFTP operations |
| `src/packet.rs` | SFTP packet types |
| `src/receiver.rs` | Async response receiver |
| `src/path.rs` | Remote path handling |
| `src/error.rs` | Errors |
| `src/id.rs` | Request IDs |
| `src/de.rs` / `ser.rs` | Packet serialize/deserialize |
| `src/fs/` | Filesystem-oriented helpers |
| `src/requests/` | SFTP request variants |
| `src/responses/` | SFTP response variants |

## Key types

| Type | Description |
|------|-------------|
| `Session` | Active SFTP channel/session |
| `Operator` | Issue ops (open, read, write, stat, readdir…) |
| Packet/Request/Response | Wire protocol types |
| `fs` module | Ergonomic FS API on top of operator |

## Notes

Licensed separately (`LICENSE` in crate). Authors include AspectUnk + sxyazi.
