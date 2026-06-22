# yazi-adapter

## Purpose

Terminal image/graphics protocol adapters. Detects which image protocol the terminal supports (Kitty, iTerm2, Sixel, Überzug++, etc.) and renders/clears previews accordingly.

## Dependencies

- `yazi-config`, `yazi-emulator`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, plus image libs per Cargo.toml

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `init()`, exports |
| `src/adapter.rs` | Adapter trait/selection |
| `src/adapters.rs` | Adapter enum/registry |
| `src/drivers/` | Per-protocol drivers |
| `src/image.rs` | Image load/scale helpers |
| `src/icc.rs` | Color profile handling |
| `src/info.rs` | Adapter/capability info |

## Key functions / items

| Item | Description |
|------|-------------|
| `init()` | Probe emulator + select best adapter |
| Adapter drivers | Protocol-specific show/hide/clear |
| Image pipeline | Decode, resize, transmit to terminal |

## Notes

Depends on `yazi-emulator` detection. Preview plugins ultimately display through this stack.
