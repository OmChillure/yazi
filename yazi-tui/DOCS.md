# yazi-tui

## Purpose

Ratatui-backed terminal UI backend for Yazi: connects the emulator/TTY/term stack to ratatui's `Backend` trait, manages draw options and terminal state transitions (alternate screen, cursor, etc.).

## Dependencies

- `yazi-config`, `yazi-emulator`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`
- External: `anyhow`, `ratatui`, `tokio`

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | Module exports |
| `src/backend.rs` | Ratatui backend implementation over Yazi term/TTY |
| `src/option.rs` | Draw/render option types |
| `src/raterm.rs` | Ratatui + terminal integration helpers |
| `src/state.rs` | TUI state (enter/leave alternate screen, restore) |

## Key concepts

| Concept | Description |
|---------|-------------|
| Backend | Bridges Yazi's custom terminal layer to ratatui widgets |
| State | Lifecycle: setup, draw loop support, teardown/restore |
| Options | Configurable rendering behavior tied to `yazi-config` |

## Notes

Used by the file manager UI path (`yazi-fm` / `yazi-actor`) rather than lower-level adapters.
