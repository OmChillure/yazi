# yazi-config

## Purpose

Loads and validates user configuration (yazi.toml, keymap.toml, theme.toml) and exposes typed config structs.

**Crate description (Cargo.toml):** Yazi configuration file parser

## Dependencies (workspace)

`yazi-codegen`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`

## Module map

Public/internal modules exported from the crate root:

- `keymap`
- `mgr`
- `open`
- `opener`
- `plugin`
- `popup`
- `preview`
- `tasks`
- `theme`
- `vfs`
- `which`
- `icon`
- `layout`
- `mixing`
- `pattern`
- `platform`
- `preset`
- `priority`
- `selectable`
- `selector`
- `style`
- `utils`
- `yazi`

## Main files

- `src/lib.rs` — entry/core
- `src/icon.rs` (file)
- `src/keymap` (dir)
- `src/layout.rs` (file)
- `src/lib.rs` (file)
- `src/mgr` (dir)
- `src/mixing.rs` (file)
- `src/open` (dir)
- `src/opener` (dir)
- `src/pattern.rs` (file)
- `src/platform.rs` (file)
- `src/plugin` (dir)
- `src/popup` (dir)
- `src/preset.rs` (file)
- `src/preview` (dir)
- `src/priority.rs` (file)
- `src/selectable.rs` (file)
- `src/selector.rs` (file)
- `src/style.rs` (file)
- `src/tasks` (dir)
- `src/theme` (dir)
- `src/utils.rs` (file)
- `src/vfs` (dir)
- `src/which` (dir)
- `src/yazi.rs` (file)

## Key public items

- **src/icon.rs**: `struct Icon`
- **src/keymap/chord.rs**: `struct Chord`, `struct ChordMatcher`, `struct ChordIter`
- **src/keymap/chords.rs**: `struct Chords`
- **src/keymap/cow.rs**: `enum ChordCow`
- **src/keymap/ids.rs**: `fn chord_id`
- **src/keymap/key.rs**: `struct Key`
- **src/keymap/keymap.rs**: `struct Keymap`
- **src/keymap/section.rs**: `struct KeymapSection`
- **src/layout.rs**: `struct Layout`
- **src/lib.rs**: `static YAZI`, `static KEYMAP`, `static THEME`, `static LAYOUT`, `fn init`, `fn init_flavor`, `fn build_flavor`
- **src/mgr/mgr.rs**: `struct Mgr`
- **src/mgr/ratio.rs**: `struct MgrRatio`
- **src/open/open.rs**: `struct Open`
- **src/open/rule.rs**: `struct OpenRule`
- **src/open/rules.rs**: `struct OpenRules`, `struct OpenRuleMatcher`
- **src/opener/opener.rs**: `struct Opener`
- **src/opener/rule.rs**: `struct OpenerRule`, `struct OpenerRuleMatcher`
- **src/opener/rules.rs**: `struct OpenerRules`, `struct OpenerRulesMatcher`
- **src/pattern.rs**: `struct Pattern`
- **src/platform.rs**: `enum Platform`
- **src/plugin/fetcher.rs**: `struct Fetcher`, `struct FetcherMatcher`
- **src/plugin/fetchers.rs**: `struct Fetchers`
- **src/plugin/ids.rs**: `fn fetcher_id`, `fn preloader_id`, `fn previewer_id`, `fn spotter_id`, `fn open_rule_id`, `fn opener_rule_id`
- **src/plugin/mod.rs**: `const MAX_FETCHERS`, `const MAX_PRELOADERS`
- **src/plugin/plugin.rs**: `struct Plugin`

## Source layout (partial)

```
src/icon.rs
src/keymap/chord.rs
src/keymap/chords.rs
src/keymap/cow.rs
src/keymap/ids.rs
src/keymap/key.rs
src/keymap/keymap.rs
src/keymap/mod.rs
src/keymap/section.rs
src/layout.rs
src/lib.rs
src/mgr/mgr.rs
src/mgr/mod.rs
src/mgr/mouse.rs
src/mgr/ratio.rs
src/mixing.rs
src/open/mod.rs
src/open/open.rs
src/open/rule.rs
src/open/rules.rs
src/opener/mod.rs
src/opener/opener.rs
src/opener/rule.rs
src/opener/rules.rs
src/pattern.rs
src/platform.rs
src/plugin/fetcher.rs
src/plugin/fetchers.rs
src/plugin/ids.rs
src/plugin/mod.rs
src/plugin/plugin.rs
src/plugin/preloader.rs
src/plugin/preloaders.rs
src/plugin/previewer.rs
src/plugin/previewers.rs
src/plugin/spotter.rs
src/plugin/spotters.rs
src/popup/confirm.rs
src/popup/input.rs
src/popup/mod.rs
src/popup/offset.rs
src/popup/options.rs
src/popup/origin.rs
src/popup/pick.rs
src/popup/position.rs
src/preset.rs
src/preview/mod.rs
src/preview/preview.rs
src/preview/wrap.rs
src/priority.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
