# yazi-dds

## Purpose

Data Distribution Service: local IPC/server for events between `yazi` and `ya`, plugins, and remote clients.

**Crate description (Cargo.toml):** Yazi data distribution service

## Dependencies (workspace)

`yazi-binding`, `yazi-boot`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`

## Module map

Public/internal modules exported from the crate root:

- `ember`
- `client`
- `payload`
- `pubsub`
- `pump`
- `sendable`
- `server`
- `state`
- `stream`

## Main files

- `src/lib.rs` — entry/core
- `src/client.rs` (file)
- `src/ember` (dir)
- `src/lib.rs` (file)
- `src/payload.rs` (file)
- `src/pubsub.rs` (file)
- `src/pump.rs` (file)
- `src/sendable.rs` (file)
- `src/server.rs` (file)
- `src/state.rs` (file)
- `src/stream.rs` (file)

## Key public items

- **src/client.rs**: `static ID`, `struct Client`, `struct Peer`
- **src/ember/bulk_rename.rs**: `struct EmberBulkRename`
- **src/ember/bye.rs**: `struct EmberBye`
- **src/ember/cd.rs**: `struct EmberCd`
- **src/ember/custom.rs**: `struct EmberCustom`
- **src/ember/delete.rs**: `struct EmberDelete`
- **src/ember/download.rs**: `struct EmberDownload`
- **src/ember/duplicate.rs**: `struct EmberDuplicate`, `struct EmberDuplicateItem`
- **src/ember/ember.rs**: `enum Ember`
- **src/ember/hey.rs**: `struct EmberHey`
- **src/ember/hi.rs**: `struct EmberHi`
- **src/ember/hover.rs**: `struct EmberHover`
- **src/ember/load.rs**: `struct EmberLoad`
- **src/ember/mount.rs**: `struct EmberMount`
- **src/ember/move.rs**: `struct EmberMove`, `struct EmberMoveItem`
- **src/ember/rename.rs**: `struct EmberRename`
- **src/ember/tab.rs**: `struct EmberTab`
- **src/ember/trash.rs**: `struct EmberTrash`
- **src/ember/yank.rs**: `struct EmberYank`, `struct EmberYankIter`
- **src/lib.rs**: `fn init`, `fn serve`, `fn shutdown`
- **src/payload.rs**: `struct Payload`
- **src/pubsub.rs**: `static LOCAL`, `static REMOTE`, `struct Pubsub`
- **src/pump.rs**: `struct Pump`
- **src/sendable.rs**: `struct Sendable`
- **src/state.rs**: `static STATE`, `struct State`

## Source layout (partial)

```
src/client.rs
src/ember/bulk_rename.rs
src/ember/bye.rs
src/ember/cd.rs
src/ember/custom.rs
src/ember/delete.rs
src/ember/download.rs
src/ember/duplicate.rs
src/ember/ember.rs
src/ember/hey.rs
src/ember/hi.rs
src/ember/hover.rs
src/ember/load.rs
src/ember/mod.rs
src/ember/mount.rs
src/ember/move.rs
src/ember/rename.rs
src/ember/tab.rs
src/ember/trash.rs
src/ember/yank.rs
src/lib.rs
src/payload.rs
src/pubsub.rs
src/pump.rs
src/sendable.rs
src/server.rs
src/state.rs
src/stream.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
