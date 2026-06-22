# yazi-watcher

## Purpose

Filesystem and remote watch integration: observes local directories (`local/`) and coordinates remote/instance-aware updates (`remote/`) so manager listings and previews refresh when files change outside Yazi.

## Dependencies

- `yazi-adapter`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-shared`, and related crates per Cargo.toml
- External: notify/async I/O as configured in the crate

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `init()` and watcher entrypoints |
| `src/local/` | Local OS file-watch backend |
| `src/remote/` | Remote/DDS-linked watch coordination |

## Key concepts

| Concept | Description |
|---------|-------------|
| `init()` | Start watcher service during FM boot |
| Local watches | Track cwd/preview/parent dirs |
| Remote watches | Multi-instance / VFS-aware updates |
| Event coalesce | Debounce bursts of FS events into refreshes |
| Adapter invalidation | Drop/rebuild image previews on change |

## Notes

Complements user `reload` actions; keeps UI in sync with external editors and tools.
