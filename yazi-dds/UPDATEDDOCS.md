# yazi-dds — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Data Distribution Service / IPC bus: pub-sub between `yazi` and `ya` CLI, plugins, and external clients.

> Cargo description: *Yazi data distribution service*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-dds`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 28 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-binding`
- `yazi-boot`
- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-version`

### External (sample)

`anyhow`, `default`, `hashbrown`, `indexmap`, `inventory`, `mlua`, `ordered-float`, `parking_lot`, `paste`, `serde`, `serde_json`, `tokio`, `tokio-stream`, `tracing`, `uds_windows`, `vendored-lua`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/client` |
| module/file | `src/ember` |
| module/file | `src/lib.rs` |
| module/file | `src/payload` |
| module/file | `src/pubsub` |
| module/file | `src/pump` |
| module/file | `src/sendable` |
| module/file | `src/server` |
| module/file | `src/state` |
| module/file | `src/stream` |

### Notable source files

- `src/client.rs`
- `src/ember/bulk_rename.rs`
- `src/ember/bye.rs`
- `src/ember/cd.rs`
- `src/ember/custom.rs`
- `src/ember/delete.rs`
- `src/ember/download.rs`
- `src/ember/duplicate.rs`
- `src/ember/ember.rs`
- `src/ember/hey.rs`
- `src/ember/hi.rs`
- `src/ember/hover.rs`
- `src/ember/load.rs`
- `src/ember/mod.rs`
- `src/ember/mount.rs`
- `src/ember/move.rs`
- `src/ember/rename.rs`
- `src/ember/tab.rs`
- `src/ember/trash.rs`
- `src/ember/yank.rs`
- `src/lib.rs`
- `src/payload.rs`
- `src/pubsub.rs`
- `src/pump.rs`
- `src/sendable.rs`
- `src/server.rs`
- `src/state.rs`
- `src/stream.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `static` | `ID` | `src/client.rs` |
| `static` | `PEERS` | `src/client.rs` |
| `static` | `QUEUE_TX` | `src/client.rs` |
| `static` | `QUEUE_RX` | `src/client.rs` |
| `struct` | `Client` | `src/client.rs` |
| `struct` | `Peer` | `src/client.rs` |
| `fn` | `serve` | `src/client.rs` |
| `fn` | `push` | `src/client.rs` |
| `fn` | `able` | `src/client.rs` |
| `fn` | `new` | `src/client.rs` |
| `struct` | `EmberBulkRename` | `src/ember/bulk_rename.rs` |
| `fn` | `borrowed` | `src/ember/bulk_rename.rs` |
| `fn` | `owned` | `src/ember/bulk_rename.rs` |
| `struct` | `EmberBye` | `src/ember/bye.rs` |
| `struct` | `EmberCd` | `src/ember/cd.rs` |
| `struct` | `EmberCustom` | `src/ember/custom.rs` |
| `fn` | `from_str` | `src/ember/custom.rs` |
| `fn` | `from_lua` | `src/ember/custom.rs` |
| `struct` | `EmberDelete` | `src/ember/delete.rs` |
| `struct` | `EmberDownload` | `src/ember/download.rs` |
| `struct` | `EmberDuplicate` | `src/ember/duplicate.rs` |
| `struct` | `EmberDuplicateItem` | `src/ember/duplicate.rs` |
| `enum` | `Ember` | `src/ember/ember.rs` |
| `fn` | `validate` | `src/ember/ember.rs` |
| `fn` | `kind` | `src/ember/ember.rs` |
| `fn` | `with_receiver` | `src/ember/ember.rs` |
| `struct` | `EmberHey` | `src/ember/hey.rs` |
| `struct` | `EmberHi` | `src/ember/hi.rs` |
| `struct` | `EmberHover` | `src/ember/hover.rs` |
| `struct` | `EmberLoad` | `src/ember/load.rs` |
| `struct` | `EmberMount` | `src/ember/mount.rs` |
| `struct` | `EmberMove` | `src/ember/move.rs` |
| `struct` | `EmberMoveItem` | `src/ember/move.rs` |
| `struct` | `EmberRename` | `src/ember/rename.rs` |
| `struct` | `EmberTab` | `src/ember/tab.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(ember);

yazi_macro::mod_flat!(client payload pubsub pump sendable server state stream);

pub fn init() {
	let (tx, rx) = tokio::sync::mpsc::unbounded_channel();

	// Client
	ID.init(yazi_boot::ARGS.client_id.unwrap_or(yazi_shared::Id::unique()));
	PEERS.with(<_>::default);
	QUEUE_TX.init(tx);
	QUEUE_RX.init(rx);

	// Server
	CLIENTS.with(<_>::default);
	STATE.with(<_>::default);

	// Pubsub
	LOCAL.with(<_>::default);
	REMOTE.with(<_>::default);

	// Env
	unsafe {
		if let Some(s) = std::env::var("YAZI_ID").ok().filter(|s| !s.is_empty()) {
			std::env::set_var("YAZI_PID", s);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-binding`, `yazi-boot`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`

**Depended on by (workspace scan)**: `yazi-watcher`, `yazi-parser`, `yazi-core`, `yazi-plugin`, `yazi-scheduler`, `yazi-runner`, `yazi-actor`, `yazi-fm`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-dds`.*
