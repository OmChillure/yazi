# yazi-boot

## Purpose

CLI/bootstrapping: parses args, loads config/theme/keymaps, initializes logging and process-wide singletons before the UI starts.

**Crate description (Cargo.toml):** Yazi bootstrapper

## Dependencies (workspace)

`yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`, `yazi-vfs`, `yazi-shared`

## Module map

Public/internal modules exported from the crate root:

- `actions`
- `args`
- `boot`

## Main files

- `src/lib.rs` — entry/core
- `src/actions` (dir)
- `src/args.rs` (file)
- `src/boot.rs` (file)
- `src/lib.rs` (file)

## Key public items

- **src/actions/actions.rs**: `struct Actions`
- **src/args.rs**: `struct Args`
- **src/boot.rs**: `struct Boot`
- **src/lib.rs**: `static ARGS`, `static BOOT`, `fn init`, `fn init_default`

## Source layout (partial)

```
src/actions/actions.rs
src/actions/mod.rs
src/args.rs
src/boot.rs
src/lib.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
