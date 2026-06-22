# yazi-binding

## Purpose

Rust types and helpers exposed to Lua and shared between plugin/runner/scheduler layers. Provides the “binding surface”: files, URLs, channels, UI elements, config views, keymaps, process handles, themes, and runtime/isolate context for Lua sandboxes.

## Dependencies

- `yazi-config`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, plus others per Cargo.toml
- External: `mlua`, `anyhow`, `serde`, `tokio`, etc.

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Public/flat modules |
| `config/` | Lua-facing config accessors |
| `elements/` | UI element bindings for plugins |
| `event/` | Event types for Lua |
| `keymap/` | Keymap inspection/helpers |
| `process/` | Process spawn/control from Lua |
| `theme/` | Theme/style access |
| Flat | `access`, `calculator`, `cha`, `chan`, `composer`, `dnd`, `error`, `fd`, `file`, `handle`, `icon`, `id`, `image`, `input`, `iter`, `layer`, `mouse`, `path`, `permit`, `range`, `runtime`, `scheme`, `selector`, `stage`, `style`, `tty`, `url`, `utils` |
| `macros.rs` | Binding macros |

## Key types

| Type | Description |
|------|-------------|
| `Runtime` | Per-Lua-state runtime/isolate (`new_isolate`) |
| `File` / `Cha` / `Url` | FS objects mirrored into Lua |
| `Chan` | Async channels to/from Lua |
| Elements | Renderable fragments for preview/UI plugins |
| `Permit` / access | Capability gating for sandboxed ops |

## Notes

Used by `yazi-runner` when spawning Lua isolates and by `yazi-plugin` for the full plugin API.
