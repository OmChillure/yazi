# yazi-fs

## Purpose

Local filesystem abstraction for Yazi: file/dir models (`File`, `Files`), characteristics (`Cha`), filters/sorting, mounts, XDG paths, providers for local FS ops, and the global current-working-directory cell.

## Dependencies

- `yazi-ffi`, `yazi-macro`, `yazi-shared`, `yazi-shim`
- External: `anyhow`, `arc-swap`, `bitflags`, `dirs`, `either`, `foldhash`, `hashbrown`, `libc`, `mlua`, `parking_lot`, `percent-encoding`, `rand`, `regex`, `scopeguard`, `serde`, `strum`, plus more platform deps

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `init()`, module exports |
| `cha/` | File characteristics (mode, size, mtime, kind…) |
| `error/` | FS error types |
| `mounts/` | Mount table / volume listing (uses `yazi-ffi` on macOS) |
| `path/` | Path helpers |
| `provider/` | Local FS provider implementations |
| Flat | `cwd`, `file`, `files`, `filter`, `fns`, `hash`, `op`, `scheme`, `sorter`, `sorting`, `splatter`, `stage`, `url`, `xdg` |

## Key functions / items

| Item | Description |
|------|-------------|
| `init()` | Init `CWD`, mounts, XDG dirs |
| `CWD` | Global current directory (arc-swap style) |
| `File` / `Files` | Single file and directory listing models |
| `Cha` | Metadata/characteristics |
| `Filter` / `Sorter` | Display filtering and sort modes |
| `Xdg` | Config/cache/state dirs |
| `provider` | Abstracted read/write/list ops |
| `Stage` | Loading stage for async dir reads |

## Notes

Local FS only; remote/archive access goes through `yazi-vfs` providers layered on top of these types.
