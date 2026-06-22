# yazi-widgets

## Purpose

Reusable widgets: vim-style input line, clipboard, scrollable/step helpers, clear region.

**Crate description (Cargo.toml):** Yazi user interface widgets

## Dependencies (workspace)

`yazi-adapter`, `yazi-config`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

## Module map

Public/internal modules exported from the crate root:

- `input`
- `clear`
- `clipboard`
- `scrollable`
- `step`

## Main files

- `src/lib.rs` — entry/core
- `src/clear.rs` (file)
- `src/clipboard.rs` (file)
- `src/input` (dir)
- `src/lib.rs` (file)
- `src/scrollable.rs` (file)
- `src/step.rs` (file)

## Key public items

- **src/clear.rs**: `static COLLISION`, `struct Clear`
- **src/clipboard.rs**: `static CLIPBOARD`, `struct Clipboard`
- **src/input/event.rs**: `enum InputEvent`
- **src/input/gait.rs**: `enum Gait`
- **src/input/input.rs**: `struct Input`
- **src/input/mode.rs**: `enum InputMode`
- **src/input/op.rs**: `enum InputOp`
- **src/input/option.rs**: `struct InputOpt`
- **src/input/parser/backspace.rs**: `struct BackspaceOpt`
- **src/input/parser/backward.rs**: `struct BackwardOpt`
- **src/input/parser/casefy.rs**: `struct CasefyOpt`
- **src/input/parser/complete.rs**: `struct CompleteOpt`
- **src/input/parser/delete.rs**: `struct DeleteOpt`
- **src/input/parser/forward.rs**: `struct ForwardOpt`
- **src/input/parser/insert.rs**: `struct InsertOpt`
- **src/input/parser/kill.rs**: `struct KillOpt`
- **src/input/parser/move.rs**: `struct MoveOpt`, `enum MoveOptStep`
- **src/input/parser/paste.rs**: `struct PasteOpt`
- **src/input/snap.rs**: `struct InputSnap`
- **src/input/snaps.rs**: `struct InputSnaps`
- **src/lib.rs**: `fn init`
- **src/scrollable.rs**: `trait Scrollable`
- **src/step.rs**: `enum Step`

## Source layout (partial)

```
src/clear.rs
src/clipboard.rs
src/input/actor/actor.rs
src/input/actor/backspace.rs
src/input/actor/backward.rs
src/input/actor/casefy.rs
src/input/actor/complete.rs
src/input/actor/delete.rs
src/input/actor/escape.rs
src/input/actor/forward.rs
src/input/actor/insert.rs
src/input/actor/kill.rs
src/input/actor/mod.rs
src/input/actor/move.rs
src/input/actor/paste.rs
src/input/actor/redo.rs
src/input/actor/replace.rs
src/input/actor/type.rs
src/input/actor/undo.rs
src/input/actor/visual.rs
src/input/actor/yank.rs
src/input/chars.rs
src/input/event.rs
src/input/gait.rs
src/input/input.rs
src/input/mod.rs
src/input/mode.rs
src/input/op.rs
src/input/option.rs
src/input/parser/backspace.rs
src/input/parser/backward.rs
src/input/parser/casefy.rs
src/input/parser/complete.rs
src/input/parser/delete.rs
src/input/parser/forward.rs
src/input/parser/insert.rs
src/input/parser/kill.rs
src/input/parser/mod.rs
src/input/parser/move.rs
src/input/parser/paste.rs
src/input/snap.rs
src/input/snaps.rs
src/input/widget.rs
src/lib.rs
src/scrollable.rs
src/step.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
