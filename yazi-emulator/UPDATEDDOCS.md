# yazi-emulator — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Terminal emulator detection and protocol quirks (image protocols, keyboard, clipboard capabilities).

> Cargo description: *Yazi terminal emulator database*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-emulator`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 6 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-tty`

### External (sample)

`anyhow`, `either`, `ratatui`, `scopeguard`, `tokio`, `tracing`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/brand` |
| module/file | `src/dimension` |
| module/file | `src/emulator` |
| module/file | `src/lib.rs` |
| module/file | `src/mux` |
| module/file | `src/unknown` |

### Notable source files

- `src/brand.rs`
- `src/dimension.rs`
- `src/emulator.rs`
- `src/lib.rs`
- `src/mux.rs`
- `src/unknown.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `enum` | `Brand` | `src/brand.rs` |
| `fn` | `from_csi` | `src/brand.rs` |
| `fn` | `from_env` | `src/brand.rs` |
| `struct` | `Dimension` | `src/dimension.rs` |
| `fn` | `cell_size` | `src/dimension.rs` |
| `static` | `EMULATOR` | `src/emulator.rs` |
| `struct` | `Emulator` | `src/emulator.rs` |
| `fn` | `detect` | `src/emulator.rs` |
| `fn` | `move_lock` | `src/emulator.rs` |
| `fn` | `read_until_da1` | `src/emulator.rs` |
| `fn` | `read_until_dsr` | `src/emulator.rs` |
| `static` | `TMUX` | `src/mux.rs` |
| `static` | `ESCAPE` | `src/mux.rs` |
| `static` | `START` | `src/mux.rs` |
| `static` | `CLOSE` | `src/mux.rs` |
| `struct` | `Mux` | `src/mux.rs` |
| `fn` | `wrap` | `src/mux.rs` |
| `fn` | `tmux_passthrough` | `src/mux.rs` |
| `fn` | `tmux_drain` | `src/mux.rs` |
| `fn` | `tmux_sixel_flag` | `src/mux.rs` |
| `fn` | `term_program` | `src/mux.rs` |
| `struct` | `Unknown` | `src/unknown.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_flat!(brand dimension emulator mux unknown);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

**Depended on by (workspace scan)**: `yazi-tui`, `yazi-adapter`, `yazi-plugin`, `yazi-actor`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-emulator`.*
