# yazi-macro — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Compile-time macros used across the workspace (event/render/config helpers, platform gates, and boilerplate reduction).

> Cargo description: *Yazi macros*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-macro`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 15 files

## 3. Dependencies

### Workspace / Yazi crates

- _(none or only indirect)_

### External (sample)

`workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `actor` | — |
| `asset` | — |
| `confirm` | — |
| `context` | — |
| `data` | — |
| `event` | — |
| `fmt` | — |
| `fs` | — |
| `input` | — |
| `log` | — |
| `module` | — |
| `platform` | — |
| `render` | — |
| `stdio` | — |

### Notable source files

- `src/actor.rs`
- `src/asset.rs`
- `src/confirm.rs`
- `src/context.rs`
- `src/data.rs`
- `src/event.rs`
- `src/fmt.rs`
- `src/fs.rs`
- `src/input.rs`
- `src/lib.rs`
- `src/log.rs`
- `src/module.rs`
- `src/platform.rs`
- `src/render.rs`
- `src/stdio.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

_No straightforward top-level `pub` items parsed (crate may be macros-only, re-exports, or heavily gated)._

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
mod actor;
mod asset;
mod confirm;
mod context;
mod data;
mod event;
mod fmt;
mod fs;
mod input;
mod log;
mod module;
mod platform;
mod render;
mod stdio;
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: _none_

**Depended on by (workspace scan)**: `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-tui`, `yazi-shared`, `yazi-ffi`, `yazi-fs`, `yazi-vfs`, `yazi-watcher`, `yazi-config`, `yazi-boot`, `yazi-emulator`, `yazi-adapter`, `yazi-dds`, `yazi-proxy`
  _(and 10 more)_

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-macro`.*
