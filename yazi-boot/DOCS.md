# yazi-boot

## Purpose

Application bootstrap for the `yazi` binary: CLI argument parsing (`clap`), global `ARGS`/`BOOT` singletons, one-shot boot actions (e.g. version/help paths), and shell completion generation at build time.

## Dependencies

- `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`, `yazi-vfs`
- External: `clap`, `futures`, `hashbrown`
- **Build:** `clap_complete`, `clap_complete_fig`, `clap_complete_nushell`

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | `ARGS`, `BOOT`, `init()` / `init_default()` |
| `src/args.rs` | Clap `Args` derive for `yazi` CLI flags |
| `src/boot.rs` | `Boot` struct derived from args (cwd, entries, client id, etc.) |
| `src/actions/` | Early-exit actions (version, completions, etc.) |

## Key functions / items

| Item | Description |
|------|-------------|
| `ARGS` | `RoCell<Args>` — parsed CLI |
| `BOOT` | `RoCell<Boot>` — normalized boot config |
| `init()` | Parse args, build boot, run actions |
| `init_default()` | Defaults without real CLI (tests/plugins) |
| `Actions::act` | Dispatches non-interactive startup actions |

## Notes

Called from `yazi-fm` after config/fs init. Completions are generated in `build.rs`.
