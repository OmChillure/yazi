# yazi-tui — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Ratatui-oriented TUI primitives and widgets support shared by the file manager UI.

> Cargo description: *Yazi terminal user interface*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-tui`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 5 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-config`
- `yazi-emulator`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-tty`

### External (sample)

`anyhow`, `ratatui`, `tokio`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/backend` |
| module/file | `src/lib.rs` |
| module/file | `src/option` |
| module/file | `src/raterm` |
| module/file | `src/state` |

### Notable source files

- `src/backend.rs`
- `src/lib.rs`
- `src/option.rs`
- `src/raterm.rs`
- `src/state.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `RatermBackend` | `src/backend.rs` |
| `fn` | `new` | `src/backend.rs` |
| `struct` | `RatermOption` | `src/option.rs` |
| `static` | `STATE` | `src/raterm.rs` |
| `struct` | `Raterm` | `src/raterm.rs` |
| `fn` | `start` | `src/raterm.rs` |
| `fn` | `stop` | `src/raterm.rs` |
| `fn` | `draw` | `src/raterm.rs` |
| `fn` | `draw_partial` | `src/raterm.rs` |
| `fn` | `can_partial` | `src/raterm.rs` |
| `struct` | `RatermState` | `src/state.rs` |
| `const` | `fn` | `src/state.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_flat!(backend option raterm state);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-config`, `yazi-emulator`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

**Depended on by (workspace scan)**: `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-tui`.*
