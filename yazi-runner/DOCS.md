# yazi-runner

## Purpose

Executes external commands/openers with environment, waiting, and output capture.

**Crate description (Cargo.toml):** Yazi Lua runner

## Dependencies (workspace)

`yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`

## Module map

Public/internal modules exported from the crate root:

- `entry`
- `fetcher`
- `loader`
- `preloader`
- `previewer`
- `runner`
- `spot`

## Main files

- `src/lib.rs` — entry/core
- `src/entry` (dir)
- `src/fetcher` (dir)
- `src/lib.rs` (file)
- `src/loader` (dir)
- `src/preloader` (dir)
- `src/previewer` (dir)
- `src/runner.rs` (file)
- `src/spot.rs` (file)

## Key public items

- **src/entry/job.rs**: `struct EntryJob`
- **src/fetcher/job.rs**: `struct FetchJob`
- **src/fetcher/state.rs**: `enum FetchState`
- **src/lib.rs**: `static RUNNER`, `fn init`
- **src/loader/chunk.rs**: `struct Chunk`
- **src/loader/loader.rs**: `static LOADER`, `struct Loader`
- **src/loader/mod.rs**: `fn install`
- **src/preloader/error.rs**: `enum PreloadError`
- **src/preloader/job.rs**: `struct PreloadJob`
- **src/preloader/state.rs**: `struct PreloadState`
- **src/previewer/error.rs**: `enum PeekError`
- **src/previewer/job.rs**: `struct PeekJob`, `struct SeekJob`
- **src/runner.rs**: `struct Runner`

## Source layout (partial)

```
src/entry/entry.rs
src/entry/job.rs
src/entry/mod.rs
src/fetcher/fetcher.rs
src/fetcher/job.rs
src/fetcher/mod.rs
src/fetcher/state.rs
src/lib.rs
src/loader/chunk.rs
src/loader/loader.rs
src/loader/mod.rs
src/loader/require.rs
src/preloader/error.rs
src/preloader/job.rs
src/preloader/mod.rs
src/preloader/preloader.rs
src/preloader/state.rs
src/previewer/error.rs
src/previewer/job.rs
src/previewer/mod.rs
src/previewer/previewer.rs
src/runner.rs
src/spot.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
