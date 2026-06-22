# yazi-config — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

TOML/config loading, validation, defaults, and typed settings for keymap, manager, opener, plugin, etc.

> Cargo description: *Yazi configuration file parser*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-config`
- **go_to ok**: `True`
- **Top-level entries**: `preset`, `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 81 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-codegen`
- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-shim`
- `yazi-term`
- `yazi-tty`

### External (sample)

`anyhow`, `arc-swap`, `bitflags`, `globset`, `hashbrown`, `indexmap`, `mlua`, `ratatui`, `regex`, `serde`, `serde_with`, `strum`, `tokio`, `toml`, `tracing`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/icon` |
| module/file | `src/keymap` |
| module/file | `src/layout` |
| module/file | `src/lib.rs` |
| module/file | `src/mgr` |
| module/file | `src/mixing` |
| module/file | `src/open` |
| module/file | `src/opener` |
| module/file | `src/pattern` |
| module/file | `src/platform` |
| module/file | `src/plugin` |
| module/file | `src/popup` |
| module/file | `src/preset` |
| module/file | `src/preview` |
| module/file | `src/priority` |
| module/file | `src/selectable` |
| module/file | `src/selector` |
| module/file | `src/style` |
| module/file | `src/tasks` |
| module/file | `src/theme` |
| module/file | `src/utils` |
| module/file | `src/vfs` |
| module/file | `src/which` |
| module/file | `src/yazi` |

### Notable source files

- `src/icon.rs`
- `src/keymap/chord.rs`
- `src/keymap/chords.rs`
- `src/keymap/cow.rs`
- `src/keymap/ids.rs`
- `src/keymap/key.rs`
- `src/keymap/keymap.rs`
- `src/keymap/mod.rs`
- `src/keymap/section.rs`
- `src/layout.rs`
- `src/lib.rs`
- `src/mgr/mgr.rs`
- `src/mgr/mod.rs`
- `src/mgr/mouse.rs`
- `src/mgr/ratio.rs`
- `src/mixing.rs`
- `src/open/mod.rs`
- `src/open/open.rs`
- `src/open/rule.rs`
- `src/open/rules.rs`
- `src/opener/mod.rs`
- `src/opener/opener.rs`
- `src/opener/rule.rs`
- `src/opener/rules.rs`
- `src/pattern.rs`
- `src/platform.rs`
- `src/plugin/fetcher.rs`
- `src/plugin/fetchers.rs`
- `src/plugin/ids.rs`
- `src/plugin/mod.rs`
- _…and 51 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Icon` | `src/icon.rs` |
| `struct` | `Chord` | `src/keymap/chord.rs` |
| `fn` | `as_erased` | `src/keymap/chord.rs` |
| `fn` | `on` | `src/keymap/chord.rs` |
| `fn` | `run` | `src/keymap/chord.rs` |
| `fn` | `desc` | `src/keymap/chord.rs` |
| `fn` | `desc_or_run` | `src/keymap/chord.rs` |
| `fn` | `contains` | `src/keymap/chord.rs` |
| `fn` | `noop` | `src/keymap/chord.rs` |
| `struct` | `ChordMatcher` | `src/keymap/chord.rs` |
| `fn` | `matches` | `src/keymap/chord.rs` |
| `struct` | `ChordIter` | `src/keymap/chord.rs` |
| `struct` | `Chords` | `src/keymap/chords.rs` |
| `fn` | `insert` | `src/keymap/chords.rs` |
| `fn` | `remove` | `src/keymap/chords.rs` |
| `fn` | `unwrap_unchecked` | `src/keymap/chords.rs` |
| `enum` | `ChordCow` | `src/keymap/cow.rs` |
| `fn` | `into_seq` | `src/keymap/cow.rs` |
| `fn` | `chord_id` | `src/keymap/ids.rs` |
| `struct` | `Key` | `src/keymap/key.rs` |
| `fn` | `plain` | `src/keymap/key.rs` |
| `struct` | `Keymap` | `src/keymap/keymap.rs` |
| `fn` | `get` | `src/keymap/keymap.rs` |
| `fn` | `read` | `src/keymap/keymap.rs` |
| `struct` | `KeymapSection` | `src/keymap/section.rs` |
| `struct` | `Layout` | `src/layout.rs` |
| `const` | `fn` | `src/layout.rs` |
| `static` | `YAZI` | `src/lib.rs` |
| `static` | `KEYMAP` | `src/lib.rs` |
| `static` | `THEME` | `src/lib.rs` |
| `static` | `LAYOUT` | `src/lib.rs` |
| `fn` | `init` | `src/lib.rs` |
| `fn` | `init_flavor` | `src/lib.rs` |
| `fn` | `build_flavor` | `src/lib.rs` |
| `fn` | `error_with_input` | `src/lib.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_pub!(keymap mgr open opener plugin popup preview tasks theme vfs which);

yazi_macro::mod_flat!(icon layout mixing pattern platform preset priority selectable selector style utils yazi);

use std::io::{Read, Write};

use yazi_shim::{cell::{RoCell, SyncCell}, toml::{DeserializeOver, DeserializeOverWith}};
use yazi_term::sequence::SetSgr;
use yazi_tty::TTY;

pub static YAZI: RoCell<yazi::Yazi> = RoCell::new();
pub static KEYMAP: RoCell<keymap::Keymap> = RoCell::new();
pub static THEME: RoCell<theme::Theme> = RoCell::new();
pub static LAYOUT: SyncCell<Layout> = SyncCell::new(Layout::default());

pub fn init() -> anyhow::Result<()> {
	if let Err(e) = try_init(true) {
		wait_for_key(e)?;
		try_init(false)?;
	}
	Ok(())
}

fn try_init(merge: bool) -> anyhow::Result<()> {
	let mut yazi = Preset::yazi()?;
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-codegen`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

**Depended on by (workspace scan)**: `yazi-tui`, `yazi-vfs`, `yazi-adapter`, `yazi-proxy`, `yazi-parser`, `yazi-binding`, `yazi-widgets`, `yazi-core`, `yazi-plugin`, `yazi-scheduler`, `yazi-runner`, `yazi-actor`, `yazi-fm`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-config`.*
