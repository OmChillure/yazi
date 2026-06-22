# yazi-tty

## Purpose

Low-level TTY access: open/read/write the controlling terminal with Unix and Windows backends. Provides the global `TTY` cell other crates (`yazi-term`, `yazi-tui`, `yazi-emulator`) use for direct terminal I/O.

## Dependencies

- `yazi-macro`, `yazi-shim`, `parking_lot`, `tracing`
- **Unix:** `libc`
- **Windows:** `windows-sys` (console, I/O, threading)

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | Exports modules; defines `TTY` RoCell and `init()` |
| `src/tty.rs` | `Tty` struct orchestrating reader/writer/handles |
| `src/handle.rs` | OS terminal handle acquisition |
| `src/reader.rs` | Non-blocking/async terminal input |
| `src/writer.rs` | Terminal output writer |

## Key items

| Item | Description |
|------|-------------|
| `TTY` | Process-wide `RoCell<Tty>` singleton |
| `init()` | Initializes `TTY` with default `Tty` |
| `Tty` | Owns handles + reader/writer pair |
| Handle/Reader/Writer | Platform-specific terminal primitives |

## Notes

Version may diverge slightly from workspace (`26.5.9`). Initialize early in `yazi-fm` / `yazi-cli` before terminal setup.
