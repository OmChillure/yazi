# yazi-shim

## Purpose

Compatibility shims and small wrappers (cells, sync types) isolating third-party or unstable APIs.

**Crate description (Cargo.toml):** Yazi crate shims

## Dependencies (workspace)

`yazi-macro`

## Module map

Public/internal modules exported from the crate root:

- `arc_swap`
- `cell`
- `mlua`
- `path`
- `ratatui`
- `serde`
- `strum`
- `toml`
- `vec`
- `base64`
- `percent_encoding`
- `twox`
- `utf8`
- `win32`

## Main files

- `src/lib.rs` — entry/core
- `src/arc_swap` (dir)
- `src/base64.rs` (file)
- `src/cell` (dir)
- `src/lib.rs` (file)
- `src/mlua` (dir)
- `src/path` (dir)
- `src/percent_encoding.rs` (file)
- `src/ratatui` (dir)
- `src/serde` (dir)
- `src/strum` (dir)
- `src/toml` (dir)
- `src/twox.rs` (file)
- `src/utf8.rs` (file)
- `src/vec` (dir)
- `src/win32.rs` (file)

## Key public items

- **src/arc_swap/traits.rs**: `trait IntoPointee`, `trait ArcSwapExt`
- **src/base64.rs**: `const BASE64_SANE`
- **src/cell/ro_cell.rs**: `struct RoCell`
- **src/cell/sync_cell.rs**: `struct SyncCell`
- **src/mlua/sequence.rs**: `struct SequenceIter`
- **src/mlua/string.rs**: `struct ByteString`
- **src/mlua/traits.rs**: `trait DeserializeOverLua`, `trait LuaTableExt`
- **src/path/separator.rs**: `const CROSS_SEPARATOR`, `const CROSS_SEPARATOR`
- **src/percent_encoding.rs**: `const RFC_3986`
- **src/ratatui/line.rs**: `struct LineIter`
- **src/ratatui/span.rs**: `enum SpanIter`
- **src/ratatui/wrapper.rs**: `trait LineComposer`, `struct WrappedLine`, `struct WordWrapper`
- **src/serde/map.rs**: `fn single_map_entry`
- **src/serde/traits.rs**: `trait Overlay`
- **src/strum/traits.rs**: `trait IntoStr`
- **src/toml/toml.rs**: `fn deserialize_spanned`
- **src/toml/traits.rs**: `trait DeserializeOver`, `trait DeserializeOverWith`, `trait DeserializeOverHook`, `struct DeserializeOverSeed`
- **src/twox.rs**: `struct Twox128`
- **src/utf8.rs**: `const fn`
- **src/vec/error.rs**: `struct IndexAtError`
- **src/vec/traits.rs**: `trait VecExt`
- **src/win32.rs**: `fn bool_ok`, `fn nz_ok`

## Source layout (partial)

```
src/arc_swap/mod.rs
src/arc_swap/traits.rs
src/base64.rs
src/cell/mod.rs
src/cell/ro_cell.rs
src/cell/sync_cell.rs
src/lib.rs
src/mlua/mod.rs
src/mlua/sequence.rs
src/mlua/string.rs
src/mlua/traits.rs
src/path/mod.rs
src/path/separator.rs
src/percent_encoding.rs
src/ratatui/line.rs
src/ratatui/mod.rs
src/ratatui/span.rs
src/ratatui/wrapper.rs
src/serde/map.rs
src/serde/mod.rs
src/serde/traits.rs
src/strum/mod.rs
src/strum/traits.rs
src/toml/mod.rs
src/toml/toml.rs
src/toml/traits.rs
src/twox.rs
src/utf8.rs
src/vec/error.rs
src/vec/mod.rs
src/vec/traits.rs
src/win32.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
