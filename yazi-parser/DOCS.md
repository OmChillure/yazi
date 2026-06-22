# yazi-parser

## Purpose

Parses action names and arguments (from keymaps, CLI emit/exec, DDS) into strongly-typed command forms (`Form` structs) consumed by actors. Also defines `SparkKind` for optional pre/post hooks around actions.

## Dependencies

- `yazi-macro`, `yazi-shared`, `yazi-shim`, config/fs types as needed
- External: `anyhow`, `serde`, clap-like arg parsing patterns

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Module exports |
| `macros.rs` | Parser/boilerplate macros |
| `app/` | App commands (quit, resize, plugin, …) |
| `mgr/` | Manager commands (~46 files: cd, select, yank, search, …) |
| `cmp/`, `confirm/`, `help/`, `input/` | Modal command forms |
| `notify/`, `pick/`, `spot/`, `tasks/`, `which/` | Subsystem forms |
| `spark/` | `SparkKind` and spark routing |
| `arrow.rs` | Shared arrow/direction args |
| `void.rs` | No-op / empty form |

## Key concepts

| Concept | Description |
|---------|-------------|
| Form types | Each action deserializes to a `Form` (args, flags) |
| Actor pairing | `yazi-actor` implements `Actor` for each form |
| Spark | Optional plugin/hook invocation around actions |
| Arrow | Reusable navigation argument |

## Notes

Bridge between stringly-typed keymaps/CLI and typed actor handlers.
