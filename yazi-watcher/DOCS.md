# yazi-watcher

## Purpose

Filesystem watching (notify + remote) to refresh folders when disk content changes.

**Crate description (Cargo.toml):** Yazi file watcher

## Dependencies (workspace)

`yazi-adapter`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-vfs`

## Module map

Public/internal modules exported from the crate root:

- `local`
- `remote`
- `backend`
- `proxy`
- `reporter`
- `watched`
- `watchee`
- `watcher`

## Main files

- `src/lib.rs` — entry/core
- `src/backend.rs` (file)
- `src/lib.rs` (file)
- `src/local` (dir)
- `src/proxy.rs` (file)
- `src/remote` (dir)
- `src/reporter.rs` (file)
- `src/watched.rs` (file)
- `src/watchee.rs` (file)
- `src/watcher.rs` (file)

## Key public items

- **src/lib.rs**: `static WATCHED`, `static WATCHER`, `fn init`
- **src/local/linked.rs**: `struct Linked`
- **src/local/mod.rs**: `static LINKED`
- **src/proxy.rs**: `struct MgrProxy`
- **src/watched.rs**: `struct Watched`
- **src/watchee.rs**: `enum Watchee`
- **src/watcher.rs**: `struct Watcher`

## Source layout (partial)

```
src/backend.rs
src/lib.rs
src/local/linked.rs
src/local/local.rs
src/local/mod.rs
src/proxy.rs
src/remote/mod.rs
src/remote/remote.rs
src/reporter.rs
src/watched.rs
src/watchee.rs
src/watcher.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
