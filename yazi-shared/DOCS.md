# yazi-shared

## Purpose

Cross-cutting shared utilities: events, URLs, errors, debounce, IDs, terminal helpers, sync primitives.

**Crate description (Cargo.toml):** Yazi shared library

## Dependencies (workspace)

`yazi-macro`, `yazi-shim`, `yazi-term`

## Module map

Public/internal modules exported from the crate root:

- `any_data`
- `data`
- `event`
- `loc`
- `path`
- `pool`
- `scheme`
- `shell`
- `strand`
- `translit`
- `url`
- `wtf8`
- `alias`
- `bytes`
- `chars`
- `completion_token`
- `condition`
- `debounce`
- `env`
- `id`
- `kebab_cased_string`
- `last_value`
- `layer`
- `localset`
- `natsort`
- `non_empty_string`
- `os`
- `predictor`
- `snake_cased_string`
- `source`
- `tests`
- `throttle`
- `time`

## Main files

- `src/lib.rs` — entry/core
- `src/alias.rs` (file)
- `src/any_data.rs` (file)
- `src/bytes.rs` (file)
- `src/chars.rs` (file)
- `src/completion_token.rs` (file)
- `src/condition.rs` (file)
- `src/data` (dir)
- `src/debounce.rs` (file)
- `src/env.rs` (file)
- `src/event` (dir)
- `src/id.rs` (file)
- `src/kebab_cased_string.rs` (file)
- `src/last_value.rs` (file)
- `src/layer.rs` (file)
- `src/lib.rs` (file)
- `src/loc` (dir)
- `src/localset.rs` (file)
- `src/natsort.rs` (file)
- `src/non_empty_string.rs` (file)
- `src/os.rs` (file)
- `src/path` (dir)
- `src/pool` (dir)
- `src/predictor.rs` (file)
- `src/scheme` (dir)
- `src/shell` (dir)
- `src/snake_cased_string.rs` (file)
- `src/source.rs` (file)
- `src/strand` (dir)
- `src/tests.rs` (file)

## Key public items

- **src/alias.rs**: `type SStr`
- **src/any_data.rs**: `struct AnyData`
- **src/bytes.rs**: `trait BytesExt`
- **src/chars.rs**: `fn strip_trailing_newline`, `fn replace_cow`, `fn replacen_cow`, `fn replace_vec_cow`, `fn replace_to_printable`, `fn push_printable_char`
- **src/completion_token.rs**: `struct CompletionToken`
- **src/condition.rs**: `enum ConditionOp`, `struct Condition`
- **src/data/any.rs**: `trait DataAny`
- **src/data/data.rs**: `enum Data`
- **src/data/inventory.rs**: `struct DataInventory`
- **src/data/key.rs**: `enum DataKey`
- **src/debounce.rs**: `struct Debounce`
- **src/env.rs**: `static LOG_LEVEL`, `fn env_exists`, `fn in_wsl`, `fn in_ssh_connection`, `enum LogLevel`
- **src/event/action.rs**: `struct Action`
- **src/event/cmd.rs**: `struct Cmd`
- **src/event/cow.rs**: `enum ActionCow`
- **src/event/event.rs**: `enum Event`
- **src/event/mod.rs**: `type Replier`, `static NEED_RENDER`
- **src/id.rs**: `struct Id`, `struct Ids`
- **src/kebab_cased_string.rs**: `struct KebabCasedString`
- **src/last_value.rs**: `struct LastValue`
- **src/layer.rs**: `enum Layer`
- **src/lib.rs**: `fn init`
- **src/loc/able.rs**: `trait LocAble`, `trait LocBufAble`, `trait StrandAble`
- **src/loc/buf.rs**: `struct LocBuf`
- **src/loc/cow.rs**: `enum LocCow`

## Source layout (partial)

```
src/alias.rs
src/any_data.rs
src/bytes.rs
src/chars.rs
src/completion_token.rs
src/condition.rs
src/data/any.rs
src/data/data.rs
src/data/de.rs
src/data/de_bytes.rs
src/data/de_key.rs
src/data/de_owned.rs
src/data/inventory.rs
src/data/key.rs
src/data/macros.rs
src/data/mod.rs
src/debounce.rs
src/env.rs
src/event/action.rs
src/event/cmd.rs
src/event/cow.rs
src/event/de.rs
src/event/de_owned.rs
src/event/event.rs
src/event/mod.rs
src/id.rs
src/kebab_cased_string.rs
src/last_value.rs
src/layer.rs
src/lib.rs
src/loc/able.rs
src/loc/buf.rs
src/loc/cow.rs
src/loc/loc.rs
src/loc/mod.rs
src/localset.rs
src/natsort.rs
src/non_empty_string.rs
src/os.rs
src/path/buf.rs
src/path/component.rs
src/path/components.rs
src/path/conversion.rs
src/path/cow.rs
src/path/display.rs
src/path/error.rs
src/path/kind.rs
src/path/like.rs
src/path/mod.rs
src/path/path.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
