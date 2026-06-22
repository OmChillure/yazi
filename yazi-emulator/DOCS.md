# yazi-emulator

## Purpose

Terminal emulator capability database and detection. Identifies the host terminal brand (Kitty, WezTerm, iTerm2, etc.), probes dimensions, and handles mux/unknown terminals so image protocols and CSI sequences can be chosen safely.

## Dependencies

- `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`
- External: `anyhow`, `either`, `ratatui`, `scopeguard`, `tokio`, `tracing`

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | Module exports |
| `src/brand.rs` | Known terminal brands / feature flags |
| `src/dimension.rs` | Cell/pixel size probing |
| `src/emulator.rs` | Main `Emulator` type and detection flow |
| `src/mux.rs` | Terminal multiplexers (tmux, etc.) handling |
| `src/unknown.rs` | Fallback when brand cannot be detected |

## Key types / functions

| Item | Description |
|------|-------------|
| `Emulator` | Detected emulator state (brand, capabilities, sizes) |
| `Brand` | Enum/catalog of supported terminals |
| Dimension helpers | Rows/cols and pixel dimensions for image layout |
| Mux helpers | Adjust behavior when running under a multiplexer |

## Notes

Critical for `yazi-adapter` image protocol selection and correct TUI layout.
