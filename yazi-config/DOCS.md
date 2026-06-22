# yazi-config

## Purpose

Loads, merges, and exposes all Yazi configuration: `yazi.toml`, `keymap.toml`, `theme.toml`, `vfs.toml`, plugin rules, openers, preview, tasks, and layout. Ships presets under `preset/` and overlays user config via `yazi-codegen` deserialize-over derives.

## Dependencies

- `yazi-codegen`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, plus theme/keymap support crates as in Cargo.toml
- External: `serde`, `toml`, `regex`, `globset`, `indexmap`, etc.

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Config init/load entry |
| `src/yazi.rs` | Root `Yazi` config struct |
| `src/preset.rs` | Embed/load defaults |
| `keymap/` | Keymap layers/bindings |
| `theme/` | Light/dark themes, styles |
| `mgr/` | Manager/layout options |
| `open/` / `opener/` | Open rules & opener commands |
| `plugin/` | Plugin fetch/preload/preview rules |
| `preview/` | Preview settings |
| `popup/` | Popup/input/confirm theming |
| `tasks/` | Task manager config |
| `vfs/` | VFS mounts/backends |
| `which/` | Which-key config |
| Flat | `icon`, `layout`, `mixing`, `pattern`, `platform`, `priority`, `selectable`, `selector`, `style`, `utils` |
| `preset/*.toml` | Default configs |

## Key functions / items

| Item | Description |
|------|-------------|
| `init()` | Load presets + user overrides into globals |
| Global config cells | Access theme/keymap/yazi/vfs singletons |
| `Priority` | Task priority enum used by scheduler |
| Pattern/selectors | Glob/mime matching for openers & plugins |

## Notes

Presets live in-crate (`preset/`) and are the source of truth for defaults documented on the website.
