# yazi-widgets — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Reusable UI widgets (confirm, input, select, which, progress, etc.) composed by yazi-fm.

> Cargo description: *Yazi user interface widgets*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-widgets`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 46 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-adapter`
- `yazi-config`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-tty`

### External (sample)

`anyhow`, `clipboard-win`, `default`, `futures`, `mlua`, `parking_lot`, `ratatui`, `serde`, `tokio`, `unicode-width`, `vendored-lua`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/clear` |
| module/file | `src/clipboard` |
| module/file | `src/input/actor` |
| module/file | `src/input` |
| module/file | `src/input/parser` |
| module/file | `src/lib.rs` |
| module/file | `src/scrollable` |
| module/file | `src/step` |

### Notable source files

- `src/clear.rs`
- `src/clipboard.rs`
- `src/input/actor/actor.rs`
- `src/input/actor/backspace.rs`
- `src/input/actor/backward.rs`
- `src/input/actor/casefy.rs`
- `src/input/actor/complete.rs`
- `src/input/actor/delete.rs`
- `src/input/actor/escape.rs`
- `src/input/actor/forward.rs`
- `src/input/actor/insert.rs`
- `src/input/actor/kill.rs`
- `src/input/actor/mod.rs`
- `src/input/actor/move.rs`
- `src/input/actor/paste.rs`
- `src/input/actor/redo.rs`
- `src/input/actor/replace.rs`
- `src/input/actor/type.rs`
- `src/input/actor/undo.rs`
- `src/input/actor/visual.rs`
- `src/input/actor/yank.rs`
- `src/input/chars.rs`
- `src/input/event.rs`
- `src/input/gait.rs`
- `src/input/input.rs`
- `src/input/mod.rs`
- `src/input/mode.rs`
- `src/input/op.rs`
- `src/input/option.rs`
- `src/input/parser/backspace.rs`
- _…and 16 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `static` | `COLLISION` | `src/clear.rs` |
| `struct` | `Clear` | `src/clear.rs` |
| `static` | `CLIPBOARD` | `src/clipboard.rs` |
| `struct` | `Clipboard` | `src/clipboard.rs` |
| `fn` | `get` | `src/clipboard.rs` |
| `fn` | `set` | `src/clipboard.rs` |
| `fn` | `execute` | `src/input/actor/actor.rs` |
| `fn` | `backspace` | `src/input/actor/backspace.rs` |
| `fn` | `backward` | `src/input/actor/backward.rs` |
| `fn` | `casefy` | `src/input/actor/casefy.rs` |
| `fn` | `complete` | `src/input/actor/complete.rs` |
| `fn` | `delete` | `src/input/actor/delete.rs` |
| `fn` | `escape` | `src/input/actor/escape.rs` |
| `fn` | `forward` | `src/input/actor/forward.rs` |
| `fn` | `insert` | `src/input/actor/insert.rs` |
| `fn` | `kill` | `src/input/actor/kill.rs` |
| `fn` | `r` | `src/input/actor/move.rs` |
| `fn` | `paste` | `src/input/actor/paste.rs` |
| `fn` | `redo` | `src/input/actor/redo.rs` |
| `fn` | `replace` | `src/input/actor/replace.rs` |
| `fn` | `replace_str` | `src/input/actor/replace.rs` |
| `fn` | `type_str` | `src/input/actor/type.rs` |
| `fn` | `undo` | `src/input/actor/undo.rs` |
| `fn` | `visual` | `src/input/actor/visual.rs` |
| `fn` | `yank` | `src/input/actor/yank.rs` |
| `enum` | `CharKind` | `src/input/chars.rs` |
| `fn` | `new` | `src/input/chars.rs` |
| `fn` | `vary` | `src/input/chars.rs` |
| `enum` | `InputEvent` | `src/input/event.rs` |
| `fn` | `is_submit` | `src/input/event.rs` |
| `enum` | `Gait` | `src/input/gait.rs` |
| `struct` | `Input` | `src/input/input.rs` |
| `fn` | `handle_op` | `src/input/input.rs` |
| `fn` | `flush_type` | `src/input/input.rs` |
| `fn` | `flush_trigger` | `src/input/input.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(input);

yazi_macro::mod_flat!(clear clipboard scrollable step);

pub fn init() { CLIPBOARD.with(<_>::default); }
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-adapter`, `yazi-config`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

**Depended on by (workspace scan)**: `yazi-proxy`, `yazi-parser`, `yazi-binding`, `yazi-core`, `yazi-plugin`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-widgets`.*
