# yazi-plugin

## Purpose

Lua plugin host: builds standard and slim Lua environments, registers APIs (fs, elements, keymap, pubsub, tasks, theme, utils, external tools), and ships preset Lua plugins under `preset/` (previews, fetchers, UI fragments).

## Dependencies

- `yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`, …
- External: `mlua`, `anyhow`, `tokio`, …

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `init()`, `LUA` global |
| `standard` / `slim` | Full vs reduced Lua setup (`standard_lua`, `slim_lua`) |
| `elements/` | Element/render API |
| `external/` | External command helpers |
| `fs/` | Filesystem API for plugins |
| `keymap/` | Keymap API |
| `pubsub/` | DDS/pubsub from Lua |
| `runtime/` | Plugin runtime helpers |
| `tasks/` | Task submission from Lua |
| `theme/` | Theme API |
| `utils/` | Misc utilities |
| `preset/**/*.lua` | Built-in plugins |

## Key functions

| Function | Description |
|----------|-------------|
| `init()` | Creates main `LUA` via `standard_lua()` |
| `standard_lua()` | Full plugin environment |
| `slim_lua` | Minimal setter passed to `yazi_runner::init` for isolates |
| `LUA` | Global main Lua state for interactive plugins |

## Notes

`yazi-fm` initializes runner with `slim_lua`, then `yazi_plugin::init()` for the main state. Presets implement default preview/fetch/preload behavior.
