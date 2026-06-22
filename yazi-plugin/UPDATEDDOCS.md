# yazi-plugin — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Lua plugin host: runtime, builtins, loaders, hooks, and the bridge from Lua into proxy/core/DDS.

> Cargo description: *Yazi plugin system*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-plugin`
- **go_to ok**: `True`
- **Top-level entries**: `preset`, `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 43 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-adapter`
- `yazi-binding`
- `yazi-boot`
- `yazi-codegen`
- `yazi-config`
- `yazi-core`
- `yazi-dds`
- `yazi-emulator`
- `yazi-fs`
- `yazi-macro`
- `yazi-proxy`
- `yazi-runner`
- `yazi-scheduler`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-vfs`
- `yazi-widgets`

### External (sample)

`ansi-to-tui`, `anyhow`, `default`, `futures`, `inventory`, `libc`, `mlua`, `percent-encoding`, `ratatui`, `serde_json`, `tokio`, `tokio-stream`, `tracing`, `twox-hash`, `unicode-width`, `uzers`, `vendored-lua`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/elements` |
| module/file | `src/external` |
| module/file | `src/fs` |
| module/file | `src/keymap` |
| module/file | `src/lib.rs` |
| module/file | `src/pubsub` |
| module/file | `src/runtime` |
| module/file | `src/slim` |
| module/file | `src/standard` |
| module/file | `src/tasks` |
| module/file | `src/theme` |
| module/file | `src/utils` |

### Notable source files

- `src/elements/elements.rs`
- `src/elements/mod.rs`
- `src/external/fd.rs`
- `src/external/mod.rs`
- `src/external/rg.rs`
- `src/external/rga.rs`
- `src/fs/fs.rs`
- `src/fs/mod.rs`
- `src/fs/op.rs`
- `src/keymap/keymap.rs`
- `src/keymap/mod.rs`
- `src/lib.rs`
- `src/pubsub/mod.rs`
- `src/pubsub/pubsub.rs`
- `src/runtime/mod.rs`
- `src/runtime/plugin.rs`
- `src/runtime/runtime.rs`
- `src/runtime/term.rs`
- `src/slim.rs`
- `src/standard.rs`
- `src/tasks/mod.rs`
- `src/tasks/option.rs`
- `src/tasks/task.rs`
- `src/theme/mod.rs`
- `src/theme/theme.rs`
- `src/utils/app.rs`
- `src/utils/cache.rs`
- `src/utils/call.rs`
- `src/utils/image.rs`
- `src/utils/json.rs`
- _…and 13 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `fn` | `compose` | `src/elements/elements.rs` |
| `fn` | `area` | `src/elements/elements.rs` |
| `fn` | `hide` | `src/elements/elements.rs` |
| `fn` | `lines` | `src/elements/elements.rs` |
| `fn` | `printable` | `src/elements/elements.rs` |
| `fn` | `redraw` | `src/elements/elements.rs` |
| `fn` | `render` | `src/elements/elements.rs` |
| `fn` | `truncate` | `src/elements/elements.rs` |
| `fn` | `width` | `src/elements/elements.rs` |
| `struct` | `FdOpt` | `src/external/fd.rs` |
| `fn` | `fd` | `src/external/fd.rs` |
| `struct` | `RgOpt` | `src/external/rg.rs` |
| `fn` | `rg` | `src/external/rg.rs` |
| `struct` | `RgaOpt` | `src/external/rga.rs` |
| `fn` | `rga` | `src/external/rga.rs` |
| `struct` | `FilesOp` | `src/fs/op.rs` |
| `fn` | `part` | `src/fs/op.rs` |
| `fn` | `done` | `src/fs/op.rs` |
| `fn` | `size` | `src/fs/op.rs` |
| `fn` | `init` | `src/lib.rs` |
| `struct` | `Pubsub` | `src/pubsub/pubsub.rs` |
| `fn` | `r` | `src/pubsub/pubsub.rs` |
| `fn` | `pub_to` | `src/pubsub/pubsub.rs` |
| `fn` | `sub` | `src/pubsub/pubsub.rs` |
| `fn` | `sub_remote` | `src/pubsub/pubsub.rs` |
| `fn` | `unsub` | `src/pubsub/pubsub.rs` |
| `fn` | `unsub_remote` | `src/pubsub/pubsub.rs` |
| `fn` | `plugin` | `src/runtime/plugin.rs` |
| `fn` | `term` | `src/runtime/term.rs` |
| `fn` | `slim_lua` | `src/slim.rs` |
| `static` | `LUA` | `src/standard.rs` |
| `fn` | `standard_lua` | `src/standard.rs` |
| `struct` | `TaskOpt` | `src/tasks/option.rs` |
| `struct` | `Task` | `src/tasks/task.rs` |
| `fn` | `reset` | `src/theme/theme.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(elements external fs keymap pubsub runtime tasks theme utils);

yazi_macro::mod_flat!(slim standard);

pub fn init() -> anyhow::Result<()> {
	LUA.init(crate::standard_lua()?);

	Ok(())
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-adapter`, `yazi-binding`, `yazi-boot`, `yazi-codegen`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-proxy`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-vfs`, `yazi-widgets`

**Depended on by (workspace scan)**: `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-plugin`.*
