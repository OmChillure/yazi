# yazi-term

## Purpose

Terminal/UI geometry and cursor helpers (positions, sizes) for layout.

**Crate description (Cargo.toml):** Cross-platform virtual terminal

## Dependencies (workspace)

`yazi-macro`, `yazi-shim`, `yazi-tty`

## Module map

Public/internal modules exported from the crate root:

- `event`
- `parser`
- `restorer`
- `sequence`
- `source`
- `stream`
- `terminal`
- `waker`
- `dimension`
- `error`
- `semaphore`
- `style`
- `term`
- `timeout`

## Main files

- `src/lib.rs` — entry/core
- `src/dimension.rs` (file)
- `src/error.rs` (file)
- `src/event` (dir)
- `src/lib.rs` (file)
- `src/macros.rs` (file)
- `src/parser` (dir)
- `src/restorer` (dir)
- `src/semaphore.rs` (file)
- `src/sequence` (dir)
- `src/source` (dir)
- `src/stream` (dir)
- `src/style.rs` (file)
- `src/term.rs` (file)
- `src/terminal` (dir)
- `src/timeout.rs` (file)
- `src/waker` (dir)

## Key public items

- **src/dimension.rs**: `struct Dimension`
- **src/error.rs**: `type Result`, `enum ParseError`
- **src/event/dnd.rs**: `enum DndEvent`, `struct DndDragOffer`, `struct DndDragAccept`, `struct DndDragChange`, `struct DndDragEnd`, `struct DndDragSend`, `struct DndDragError`, `struct DndDropEnter`
- **src/event/event.rs**: `enum Event`
- **src/event/keyboard.rs**: `struct KeyEvent`, `enum KeyEventKind`, `enum KeyCode`, `enum ModifierKeyCode`, `enum MediaKeyCode`
- **src/event/mouse.rs**: `struct MouseEvent`, `enum MouseEventKind`, `enum MouseButton`
- **src/lib.rs**: `fn init`
- **src/parser/parser.rs**: `struct Parser`
- **src/restorer/unix.rs**: `struct Restorer`
- **src/restorer/windows.rs**: `struct Restorer`
- **src/semaphore.rs**: `static YIELD_TO_SUBPROCESS`
- **src/sequence/clipboard.rs**: `struct SetClipboard`
- **src/sequence/csi_u.rs**: `struct PopKeyboardFlags`
- **src/sequence/cursor.rs**: `struct MoveTo`, `struct ShowCursor`, `struct HideCursor`, `struct SaveCursorPos`, `struct RestoreCursorPos`, `struct SetTitle`, `struct SetCursorStyle`, `struct RestoreCursorStyle`
- **src/sequence/dnd.rs**: `struct EnableDrag`, `struct EnableDrop`, `struct DisableDrag`, `struct DisableDrop`, `enum AgreeDrag`, `enum AgreeDrop`, `struct StartDrag`, `struct StartDrop`

## Source layout (partial)

```
src/dimension.rs
src/error.rs
src/event/dnd.rs
src/event/event.rs
src/event/keyboard.rs
src/event/mod.rs
src/event/modifiers.rs
src/event/mouse.rs
src/lib.rs
src/macros.rs
src/parser/csi.rs
src/parser/ground.rs
src/parser/mod.rs
src/parser/osc.rs
src/parser/parser.rs
src/parser/state.rs
src/parser/windows.rs
src/restorer/mod.rs
src/restorer/unix.rs
src/restorer/windows.rs
src/semaphore.rs
src/sequence/clipboard.rs
src/sequence/csi_u.rs
src/sequence/cursor.rs
src/sequence/dnd.rs
src/sequence/erase.rs
src/sequence/if.rs
src/sequence/mod.rs
src/sequence/mode.rs
src/sequence/query.rs
src/sequence/style.rs
src/sequence/sync.rs
src/sequence/traits.rs
src/source/common.rs
src/source/mod.rs
src/source/unix.rs
src/source/windows.rs
src/stream/mod.rs
src/stream/stream.rs
src/style.rs
src/term.rs
src/terminal/mod.rs
src/terminal/unix.rs
src/terminal/windows.rs
src/timeout.rs
src/waker/mod.rs
src/waker/unix.rs
src/waker/windows.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
