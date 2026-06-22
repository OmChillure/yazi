# yazi-binding

## Purpose

Lua userdata/bindings exposing Yazi types (Cha, Color, Url, etc.) to the mlua plugin runtime.

**Crate description (Cargo.toml):** Yazi Lua bindings

## Dependencies (workspace)

`yazi-adapter`, `yazi-codegen`, `yazi-config`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-vfs`, `yazi-widgets`

## Module map

Public/internal modules exported from the crate root:

- `config`
- `elements`
- `event`
- `keymap`
- `process`
- `theme`
- `access`
- `calculator`
- `cha`
- `chan`
- `composer`
- `dnd`
- `error`
- `fd`
- `file`
- `handle`
- `icon`
- `id`
- `image`
- `input`
- `iter`
- `layer`
- `mouse`
- `path`
- `permit`
- `range`
- `runtime`
- `scheme`
- `selector`
- `stage`
- `style`
- `tty`
- `url`
- `utils`

## Main files

- `src/lib.rs` — entry/core
- `src/access.rs` (file)
- `src/calculator.rs` (file)
- `src/cha.rs` (file)
- `src/chan.rs` (file)
- `src/composer.rs` (file)
- `src/config` (dir)
- `src/dnd.rs` (file)
- `src/elements` (dir)
- `src/error.rs` (file)
- `src/event` (dir)
- `src/fd.rs` (file)
- `src/file.rs` (file)
- `src/handle.rs` (file)
- `src/icon.rs` (file)
- `src/id.rs` (file)
- `src/image.rs` (file)
- `src/input.rs` (file)
- `src/iter.rs` (file)
- `src/keymap` (dir)
- `src/layer.rs` (file)
- `src/lib.rs` (file)
- `src/macros.rs` (file)
- `src/mouse.rs` (file)
- `src/path.rs` (file)
- `src/permit.rs` (file)
- `src/process` (dir)
- `src/range.rs` (file)
- `src/runtime.rs` (file)
- `src/scheme.rs` (file)

## Key public items

- **src/access.rs**: `struct Access`
- **src/calculator.rs**: `enum SizeCalculator`
- **src/cha.rs**: `struct Cha`
- **src/chan.rs**: `struct MpscTx`, `struct MpscRx`, `struct MpscUnboundedTx`, `struct MpscUnboundedRx`, `struct OneshotTx`, `struct OneshotRx`
- **src/composer.rs**: `type ComposerGet`, `type ComposerSet`, `struct Composer`
- **src/config/fetcher.rs**: `struct Fetcher`, `struct FetcherMatcher`
- **src/config/fetchers.rs**: `struct Fetchers`
- **src/config/open_rule.rs**: `struct OpenRule`, `struct OpenRuleMatcher`
- **src/config/open_rules.rs**: `struct OpenRules`
- **src/config/opener.rs**: `struct Opener`
- **src/config/opener_rule.rs**: `struct OpenerRule`, `struct OpenerRuleMatcher`
- **src/config/opener_rules.rs**: `struct OpenerRules`
- **src/config/preloader.rs**: `struct Preloader`, `struct PreloaderMatcher`
- **src/config/preloaders.rs**: `struct Preloaders`
- **src/config/previewer.rs**: `struct Previewer`, `struct PreviewerMatcher`
- **src/config/previewers.rs**: `struct Previewers`
- **src/config/spotter.rs**: `struct Spotter`, `struct SpotterMatcher`
- **src/config/spotters.rs**: `struct Spotters`
- **src/dnd.rs**: `struct DndEvent`
- **src/elements/align.rs**: `struct Align`
- **src/elements/area.rs**: `enum Area`
- **src/elements/bar.rs**: `struct Bar`
- **src/elements/border.rs**: `struct Border`
- **src/elements/cell.rs**: `struct Cell`
- **src/elements/clear.rs**: `struct Clear`

## Source layout (partial)

```
src/access.rs
src/calculator.rs
src/cha.rs
src/chan.rs
src/composer.rs
src/config/fetcher.rs
src/config/fetchers.rs
src/config/mod.rs
src/config/open_rule.rs
src/config/open_rules.rs
src/config/opener.rs
src/config/opener_rule.rs
src/config/opener_rules.rs
src/config/preloader.rs
src/config/preloaders.rs
src/config/previewer.rs
src/config/previewers.rs
src/config/spotter.rs
src/config/spotters.rs
src/dnd.rs
src/elements/align.rs
src/elements/area.rs
src/elements/bar.rs
src/elements/border.rs
src/elements/cell.rs
src/elements/clear.rs
src/elements/color.rs
src/elements/constraint.rs
src/elements/edge.rs
src/elements/elements.rs
src/elements/fill.rs
src/elements/gauge.rs
src/elements/layout.rs
src/elements/line.rs
src/elements/list.rs
src/elements/mod.rs
src/elements/pad.rs
src/elements/pos.rs
src/elements/rect.rs
src/elements/renderable.rs
src/elements/row.rs
src/elements/span.rs
src/elements/table.rs
src/elements/text.rs
src/elements/wrap.rs
src/error.rs
src/event/action.rs
src/event/cmd.rs
src/event/mod.rs
src/fd.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
