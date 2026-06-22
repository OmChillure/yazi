# yazi-vfs

## Purpose

Virtual filesystem layer unifying local, archive, and remote (SFTP/SSH) access behind provider traits. Higher-level file operations used by scheduler/preview/plugins without caring which backend owns a URL.

## Dependencies

- `yazi-config`, `yazi-fs`, `yazi-macro`, `yazi-sftp`, `yazi-shared`, `yazi-shim`
- External: `anyhow`, `chrono`, `deadpool` (SSH connection pooling), `either`, `futures`, `hashbrown`, `parking_lot`, `russh`, `tokio`, `tracing`, `typed-path`

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `init()` → provider init |
| `provider/` | Provider registry and backends (local, sftp, archive…) |
| Flat | `cha`, `file`, `files`, `fns`, `op` — VFS-level counterparts to `yazi-fs` types |

## Key functions / items

| Item | Description |
|------|-------------|
| `init()` | Registers/configures VFS providers |
| Providers | Map schemes/URLs to concrete backends |
| `File`/`Files`/`Cha`/`Op` | VFS-normalized operations across backends |
| SSH pool | `deadpool` + `russh` for SFTP sessions |

## Notes

Depends on `yazi-config` for VFS mount/config (`vfs-default.toml` presets). Initialized in `yazi-fm` after `yazi_fs::init()`.
