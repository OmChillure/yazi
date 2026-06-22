# yazi-binding — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Lua (mlua) type bindings exposing Rust types/APIs safely to the plugin runtime.

> Cargo description: *Yazi Lua bindings*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-binding`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 87 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-adapter`
- `yazi-codegen`
- `yazi-config`
- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-tty`
- `yazi-vfs`
- `yazi-widgets`

### External (sample)

`ansi-to-tui`, `anyhow`, `default`, `futures`, `hashbrown`, `libc`, `mlua`, `paste`, `ratatui`, `serde_json`, `tokio`, `tokio-stream`, `tracing`, `unicode-width`, `vendored-lua`, `windows-sys`, `workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `macros` | — |

### Notable source files

- `src/access.rs`
- `src/calculator.rs`
- `src/cha.rs`
- `src/chan.rs`
- `src/composer.rs`
- `src/config/fetcher.rs`
- `src/config/fetchers.rs`
- `src/config/mod.rs`
- `src/config/open_rule.rs`
- `src/config/open_rules.rs`
- `src/config/opener.rs`
- `src/config/opener_rule.rs`
- `src/config/opener_rules.rs`
- `src/config/preloader.rs`
- `src/config/preloaders.rs`
- `src/config/previewer.rs`
- `src/config/previewers.rs`
- `src/config/spotter.rs`
- `src/config/spotters.rs`
- `src/dnd.rs`
- `src/elements/align.rs`
- `src/elements/area.rs`
- `src/elements/bar.rs`
- `src/elements/border.rs`
- `src/elements/cell.rs`
- `src/elements/clear.rs`
- `src/elements/color.rs`
- `src/elements/constraint.rs`
- `src/elements/edge.rs`
- `src/elements/elements.rs`
- _…and 57 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Access` | `src/access.rs` |
| `enum` | `SizeCalculator` | `src/calculator.rs` |
| `struct` | `Cha` | `src/cha.rs` |
| `fn` | `install` | `src/cha.rs` |
| `struct` | `MpscTx` | `src/chan.rs` |
| `struct` | `MpscRx` | `src/chan.rs` |
| `struct` | `MpscUnboundedTx` | `src/chan.rs` |
| `struct` | `MpscUnboundedRx` | `src/chan.rs` |
| `struct` | `OneshotTx` | `src/chan.rs` |
| `struct` | `OneshotRx` | `src/chan.rs` |
| `type` | `ComposerGet` | `src/composer.rs` |
| `type` | `ComposerSet` | `src/composer.rs` |
| `struct` | `Composer` | `src/composer.rs` |
| `fn` | `new` | `src/composer.rs` |
| `fn` | `with_parent` | `src/composer.rs` |
| `struct` | `Fetcher` | `src/config/fetcher.rs` |
| `struct` | `FetcherMatcher` | `src/config/fetcher.rs` |
| `struct` | `Fetchers` | `src/config/fetchers.rs` |
| `struct` | `OpenRule` | `src/config/open_rule.rs` |
| `struct` | `OpenRuleMatcher` | `src/config/open_rule.rs` |
| `struct` | `OpenRules` | `src/config/open_rules.rs` |
| `struct` | `Opener` | `src/config/opener.rs` |
| `struct` | `OpenerRule` | `src/config/opener_rule.rs` |
| `struct` | `OpenerRuleMatcher` | `src/config/opener_rule.rs` |
| `struct` | `OpenerRules` | `src/config/opener_rules.rs` |
| `struct` | `Preloader` | `src/config/preloader.rs` |
| `struct` | `PreloaderMatcher` | `src/config/preloader.rs` |
| `struct` | `Preloaders` | `src/config/preloaders.rs` |
| `struct` | `Previewer` | `src/config/previewer.rs` |
| `struct` | `PreviewerMatcher` | `src/config/previewer.rs` |
| `struct` | `Previewers` | `src/config/previewers.rs` |
| `struct` | `Spotter` | `src/config/spotter.rs` |
| `struct` | `SpotterMatcher` | `src/config/spotter.rs` |
| `struct` | `Spotters` | `src/config/spotters.rs` |
| `struct` | `DndEvent` | `src/dnd.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
mod macros;

yazi_macro::mod_pub!(config elements event keymap process theme);

yazi_macro::mod_flat!(access calculator cha chan composer dnd error fd file handle icon id image input iter layer mouse path permit range runtime scheme selector stage style tty url utils);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-adapter`, `yazi-codegen`, `yazi-config`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-vfs`, `yazi-widgets`

**Depended on by (workspace scan)**: `yazi-dds`, `yazi-parser`, `yazi-core`, `yazi-plugin`, `yazi-scheduler`, `yazi-runner`, `yazi-actor`, `yazi-fm`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-binding`.*
