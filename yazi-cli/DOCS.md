# yazi-cli

## Purpose

Standalone `ya` CLI binary for DDS pub/sub, package management, and emitting actions into a running Yazi instance.

**Crate description (Cargo.toml):** Yazi command-line interface

## Dependencies (workspace)

`yazi-adapter`, `yazi-boot`, `yazi-config`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-term`, `yazi-tty`, `yazi-version`, `yazi-shared`

## Module map

Public/internal modules exported from the crate root:

- `cache`
- `dds`
- `env`
- `package`
- `shared`
- `args`

## Main files

- `src/main.rs` — entry/core
- `src/args.rs` (file)
- `src/cache` (dir)
- `src/dds` (dir)
- `src/env` (dir)
- `src/main.rs` (file)
- `src/package` (dir)
- `src/shared` (dir)

## Key public items

- **src/shared/shared.rs**: `fn must_exists`, `fn maybe_exists`, `fn copy_and_seal`, `fn remove_sealed`

## Source layout (partial)

```
src/args.rs
src/cache/clear.rs
src/cache/mod.rs
src/dds/draw.rs
src/dds/exec.rs
src/dds/mod.rs
src/dds/shot.rs
src/env/env.rs
src/env/mod.rs
src/main.rs
src/package/add.rs
src/package/delete.rs
src/package/dependency.rs
src/package/deploy.rs
src/package/git.rs
src/package/hash.rs
src/package/install.rs
src/package/mod.rs
src/package/package.rs
src/package/upgrade.rs
src/shared/mod.rs
src/shared/shared.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
