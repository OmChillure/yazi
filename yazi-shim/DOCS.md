# yazi-shim

## Purpose

Thin compatibility/shim layer over third-party crates Yazi depends on heavily (`mlua`, `ratatui`, `toml`, `serde`, `arc_swap`, paths, etc.). Centralizes extensions, feature flags (e.g. vendored Lua), and Windows helpers so the rest of the codebase imports one consistent surface.

## Dependencies

- `yazi-macro`
- External: `arc-swap`, `base64`, `hashbrown`, `mlua`, `percent-encoding`, `ratatui`, `serde`, `thiserror`, `toml`, `twox-hash`, `unicode-width`
- Optional: `parking_lot` via feature; Windows `win32` module on Windows
- Feature `vendored-lua` (default) vendors Lua via `mlua`

## Main files

| File / module | Role |
|---------------|------|
| `src/lib.rs` | Re-exports shim modules |
| `src/arc_swap/` | ArcSwap helpers |
| `src/cell/` | `RoCell` and once-init cells used workspace-wide |
| `src/mlua/` | Lua extensions/utilities |
| `src/path/` | Path normalization helpers |
| `src/ratatui/` | Ratatui style/layout shims |
| `src/serde/` | Serde utilities (`single_map_entry`, etc.) |
| `src/strum/` | Strum helpers |
| `src/toml/` | TOML deserialize-over traits/seeds (config overlay) |
| `src/vec/` | Small vector utilities |
| `src/base64.rs`, `percent_encoding.rs`, `twox.rs`, `utf8.rs` | Encoding/hash/utf8 shims |
| `src/win32.rs` | Windows-only helpers |

## Key items

| Item | Description |
|------|-------------|
| `RoCell<T>` | Read-only once-initialized global cell |
| TOML overlay traits | `DeserializeOverWith`, seeds/hooks for config merge |
| `mlua` extensions | Shared Lua ergonomics |
| `init` patterns | Consistent global init across crates |

## Notes

Foundational — almost every Yazi crate imports `yazi-shim` for `RoCell` and/or TOML/Lua shims.
