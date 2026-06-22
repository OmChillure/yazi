# yazi-term

## Purpose

Cross-platform virtual terminal abstraction above `yazi-tty`: terminal modes, event parsing, sequences, style, wakers, and subprocess yield coordination. Implements Yazi's own terminal control rather than relying solely on ratatui/crossterm.

## Dependencies

- `yazi-macro`, `yazi-shim`, `yazi-tty`
- External: `anyhow`, `base64`, `bitflags`, `futures`, `parking_lot`, `ratatui`, `serde`, `strum`, `thiserror`, `tokio`
- **Unix:** `signal-hook`, `rustix`
- **Windows:** `windows-sys`

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `init()`, exports |
| `terminal/` | `Terminal` struct and lifecycle |
| `event/` | Terminal event types |
| `parser/` | Input byte stream → events |
| `sequence/` | CSI/OSC sequences |
| `source/` | Event sources |
| `stream/` | Async terminal streams |
| `waker/` | Async wake/integration |
| `restorer/` | Restore terminal state on exit/panic |
| Flat | `dimension`, `error`, `semaphore`, `style`, `term`, `timeout` |

## Key functions / items

| Item | Description |
|------|-------------|
| `init()` | Init subprocess semaphore + `TERM` global from `yazi_tty::TTY` |
| `TERM` | Global terminal instance |
| `Terminal` | High-level terminal ops |
| `YIELD_TO_SUBPROCESS` | Semaphore coordinating external process vs TUI |
| Restorer | Ensures terminal modes reset |

## Notes

Depends on `yazi-tty` being initialized first. Used by emulator, tui, adapters, and the FM event loop.
