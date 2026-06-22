# yazi-macro

## Purpose

Declarative macros shared across the Yazi workspace. Centralizes boilerplate for module inclusion, actor/event helpers, platform gates, rendering, logging, and Lua/FFI ergonomics so crates stay consistent.

## Dependencies

None (macro-only crate, no external deps).

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | Module declarations |
| `src/actor.rs` | Actor-related macros |
| `src/asset.rs` | Embedded asset helpers |
| `src/confirm.rs` | Confirm dialog macros |
| `src/context.rs` | Context/accessor macros |
| `src/data.rs` | Data/event payload macros |
| `src/event.rs` | Event emission macros |
| `src/fmt.rs` | Formatting helpers (`outln!`, `errln!`, etc.) |
| `src/fs.rs` | Filesystem convenience macros |
| `src/input.rs` | Input widget macros |
| `src/log.rs` | Logging macros |
| `src/module.rs` | `mod_pub!` / `mod_flat!` for consistent module layout |
| `src/platform.rs` | Unix/Windows/macOS feature gates |
| `src/render.rs` | TUI render macros |
| `src/stdio.rs` | Stdio/TTY macros |

## Key macros

| Macro | Description |
|-------|-------------|
| `mod_pub!(a b c)` | Declare and re-export public submodules |
| `mod_flat!(a b c)` | Flat-include modules at crate root |
| `outln!` / `errln!` | stdout/stderr printing used by CLI |
| Platform macros | Conditionally compile per OS |

## Notes

Nearly every Yazi crate depends on this for module structure (`mod_flat!`, `mod_pub!`).
