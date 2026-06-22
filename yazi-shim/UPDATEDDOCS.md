# yazi-shim — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Thin compatibility/shims layer bridging third-party APIs or feature differences for the rest of the workspace.

> Cargo description: *Yazi crate shims*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-shim`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 32 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-macro`

### External (sample)

`arc-swap`, `base64`, `default`, `hashbrown`, `mlua`, `percent-encoding`, `ratatui`, `serde`, `thiserror`, `toml`, `twox-hash`, `unicode-width`, `vendored-lua`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/arc_swap` |
| module/file | `src/base64` |
| module/file | `src/cell` |
| module/file | `src/lib.rs` |
| module/file | `src/mlua` |
| module/file | `src/path` |
| module/file | `src/percent_encoding` |
| module/file | `src/ratatui` |
| module/file | `src/serde` |
| module/file | `src/strum` |
| module/file | `src/toml` |
| module/file | `src/twox` |
| module/file | `src/utf8` |
| module/file | `src/vec` |
| module/file | `src/win32` |

### Notable source files

- `src/arc_swap/mod.rs`
- `src/arc_swap/traits.rs`
- `src/base64.rs`
- `src/cell/mod.rs`
- `src/cell/ro_cell.rs`
- `src/cell/sync_cell.rs`
- `src/lib.rs`
- `src/mlua/mod.rs`
- `src/mlua/sequence.rs`
- `src/mlua/string.rs`
- `src/mlua/traits.rs`
- `src/path/mod.rs`
- `src/path/separator.rs`
- `src/percent_encoding.rs`
- `src/ratatui/line.rs`
- `src/ratatui/mod.rs`
- `src/ratatui/span.rs`
- `src/ratatui/wrapper.rs`
- `src/serde/map.rs`
- `src/serde/mod.rs`
- `src/serde/traits.rs`
- `src/strum/mod.rs`
- `src/strum/traits.rs`
- `src/toml/mod.rs`
- `src/toml/toml.rs`
- `src/toml/traits.rs`
- `src/twox.rs`
- `src/utf8.rs`
- `src/vec/error.rs`
- `src/vec/mod.rs`
- _…and 2 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `trait` | `IntoPointee` | `src/arc_swap/traits.rs` |
| `trait` | `ArcSwapExt` | `src/arc_swap/traits.rs` |
| `const` | `BASE64_SANE` | `src/base64.rs` |
| `struct` | `RoCell` | `src/cell/ro_cell.rs` |
| `const` | `fn` | `src/cell/ro_cell.rs` |
| `fn` | `init` | `src/cell/ro_cell.rs` |
| `fn` | `with` | `src/cell/ro_cell.rs` |
| `fn` | `drop` | `src/cell/ro_cell.rs` |
| `struct` | `SyncCell` | `src/cell/sync_cell.rs` |
| `struct` | `SequenceIter` | `src/mlua/sequence.rs` |
| `struct` | `ByteString` | `src/mlua/string.rs` |
| `trait` | `DeserializeOverLua` | `src/mlua/traits.rs` |
| `trait` | `LuaTableExt` | `src/mlua/traits.rs` |
| `const` | `CROSS_SEPARATOR` | `src/path/separator.rs` |
| `const` | `RFC_3986` | `src/percent_encoding.rs` |
| `struct` | `LineIter` | `src/ratatui/line.rs` |
| `fn` | `source` | `src/ratatui/line.rs` |
| `fn` | `parsed` | `src/ratatui/line.rs` |
| `fn` | `wrapped` | `src/ratatui/line.rs` |
| `fn` | `next` | `src/ratatui/line.rs` |
| `enum` | `SpanIter` | `src/ratatui/span.rs` |
| `fn` | `from_span` | `src/ratatui/span.rs` |
| `fn` | `from_line` | `src/ratatui/span.rs` |
| `fn` | `into_static_line` | `src/ratatui/span.rs` |
| `trait` | `LineComposer` | `src/ratatui/wrapper.rs` |
| `struct` | `WrappedLine` | `src/ratatui/wrapper.rs` |
| `struct` | `WordWrapper` | `src/ratatui/wrapper.rs` |
| `fn` | `single_map_entry` | `src/serde/map.rs` |
| `trait` | `Overlay` | `src/serde/traits.rs` |
| `trait` | `IntoStr` | `src/strum/traits.rs` |
| `fn` | `deserialize_spanned` | `src/toml/toml.rs` |
| `trait` | `DeserializeOver` | `src/toml/traits.rs` |
| `trait` | `DeserializeOverWith` | `src/toml/traits.rs` |
| `trait` | `DeserializeOverHook` | `src/toml/traits.rs` |
| `struct` | `DeserializeOverSeed` | `src/toml/traits.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(arc_swap cell mlua path ratatui serde strum toml vec);

yazi_macro::mod_flat!(base64 percent_encoding twox utf8);

#[cfg(windows)]
yazi_macro::mod_flat!(win32);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-macro`

**Depended on by (workspace scan)**: `yazi-term`, `yazi-tty`, `yazi-tui`, `yazi-shared`, `yazi-fs`, `yazi-vfs`, `yazi-watcher`, `yazi-config`, `yazi-boot`, `yazi-emulator`, `yazi-adapter`, `yazi-dds`, `yazi-proxy`, `yazi-binding`, `yazi-widgets`
  _(and 5 more)_

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-shim`.*
