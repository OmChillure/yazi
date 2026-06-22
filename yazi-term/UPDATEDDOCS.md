# yazi-term — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Terminal capability detection and term-related utilities (colors, sizes, feature probes) without owning the full TUI.

> Cargo description: *Cross-platform virtual terminal*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-term`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `LICENSE`, `README.md`
- **Rust sources under `src/`**: 48 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-macro`
- `yazi-shim`
- `yazi-tty`

### External (sample)

`anyhow`, `base64`, `bitflags`, `futures`, `parking_lot`, `ratatui`, `rustix`, `serde`, `signal-hook`, `strum`, `thiserror`, `tokio`, `windows-sys`, `workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `macros` | — |

### Notable source files

- `src/dimension.rs`
- `src/error.rs`
- `src/event/dnd.rs`
- `src/event/event.rs`
- `src/event/keyboard.rs`
- `src/event/mod.rs`
- `src/event/modifiers.rs`
- `src/event/mouse.rs`
- `src/lib.rs`
- `src/macros.rs`
- `src/parser/csi.rs`
- `src/parser/ground.rs`
- `src/parser/mod.rs`
- `src/parser/osc.rs`
- `src/parser/parser.rs`
- `src/parser/state.rs`
- `src/parser/windows.rs`
- `src/restorer/mod.rs`
- `src/restorer/unix.rs`
- `src/restorer/windows.rs`
- `src/semaphore.rs`
- `src/sequence/clipboard.rs`
- `src/sequence/csi_u.rs`
- `src/sequence/cursor.rs`
- `src/sequence/dnd.rs`
- `src/sequence/erase.rs`
- `src/sequence/if.rs`
- `src/sequence/mod.rs`
- `src/sequence/mode.rs`
- `src/sequence/query.rs`
- _…and 18 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Dimension` | `src/dimension.rs` |
| `fn` | `checked` | `src/dimension.rs` |
| `fn` | `ratio` | `src/dimension.rs` |
| `type` | `Result` | `src/error.rs` |
| `enum` | `ParseError` | `src/error.rs` |
| `enum` | `DndEvent` | `src/event/dnd.rs` |
| `struct` | `DndDragOffer` | `src/event/dnd.rs` |
| `struct` | `DndDragAccept` | `src/event/dnd.rs` |
| `struct` | `DndDragChange` | `src/event/dnd.rs` |
| `struct` | `DndDragEnd` | `src/event/dnd.rs` |
| `struct` | `DndDragSend` | `src/event/dnd.rs` |
| `struct` | `DndDragError` | `src/event/dnd.rs` |
| `struct` | `DndDropEnter` | `src/event/dnd.rs` |
| `struct` | `DndDropReady` | `src/event/dnd.rs` |
| `struct` | `DndDropArrive` | `src/event/dnd.rs` |
| `struct` | `DndDropError` | `src/event/dnd.rs` |
| `fn` | `r` | `src/event/dnd.rs` |
| `fn` | `x` | `src/event/dnd.rs` |
| `fn` | `y` | `src/event/dnd.rs` |
| `fn` | `idx` | `src/event/dnd.rs` |
| `fn` | `op` | `src/event/dnd.rs` |
| `fn` | `mimes` | `src/event/dnd.rs` |
| `fn` | `is_drag` | `src/event/dnd.rs` |
| `fn` | `from_state` | `src/event/dnd.rs` |
| `enum` | `DndOp` | `src/event/dnd.rs` |
| `struct` | `DndMimeList` | `src/event/dnd.rs` |
| `fn` | `new` | `src/event/dnd.rs` |
| `fn` | `iter` | `src/event/dnd.rs` |
| `enum` | `Event` | `src/event/event.rs` |
| `struct` | `KeyEvent` | `src/event/keyboard.rs` |
| `const` | `fn` | `src/event/keyboard.rs` |
| `enum` | `KeyEventKind` | `src/event/keyboard.rs` |
| `fn` | `from_vt_code` | `src/event/keyboard.rs` |
| `struct` | `KeyEventState` | `src/event/keyboard.rs` |
| `fn` | `from_vt_mask` | `src/event/keyboard.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
mod macros;

yazi_macro::mod_flat!(dimension error semaphore style term timeout);

yazi_macro::mod_pub!(event parser restorer sequence source stream terminal waker);

pub fn init() -> anyhow::Result<()> {
	YIELD_TO_SUBPROCESS.init(tokio::sync::Semaphore::new(1));

	TERM.init(terminal::Terminal::new(&yazi_tty::TTY)?);

	Ok(())
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-macro`, `yazi-shim`, `yazi-tty`

**Depended on by (workspace scan)**: `yazi-tui`, `yazi-shared`, `yazi-config`, `yazi-emulator`, `yazi-adapter`, `yazi-parser`, `yazi-binding`, `yazi-widgets`, `yazi-core`, `yazi-plugin`, `yazi-scheduler`, `yazi-actor`, `yazi-fm`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-term`.*
