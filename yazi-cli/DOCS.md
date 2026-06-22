# yazi-cli

## Purpose

**`ya`** command-line interface for controlling/interacting with running Yazi instances and managing plugins/packages/cache/env. Talks over DDS (`emit`, `exec`, `pub`, `sub`) rather than owning a TUI.

## Dependencies

- `yazi-adapter`, `yazi-boot`, `yazi-config`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-term`, `yazi-tty`, `yazi-version`
- External: `clap`, `anyhow`, `serde_json`, `tokio`, `toml`, …

## Main files / modules

| Module | Role |
|--------|------|
| `src/main.rs` | Entry + command dispatch |
| `src/args.rs` | Clap `Args` / `Command` tree |
| `dds/` | Emit/exec/pub/sub helpers |
| `package/` | Plugin package manager (`pkg add/install/…`) |
| `cache/` | Cache maintenance |
| `env/` | Print env/config diagnostics |
| `shared/` | Shared CLI helpers |
| `build.rs` | Completions generation |

## Commands

| Command | Description |
|---------|-------------|
| `emit` / `emit-to` | Fire an action on current/specified instance |
| `exec` | Run action and print JSON result |
| `pub` / `pub-to` | Publish DDS message |
| `sub` | Subscribe to remote instance messages |
| `pkg` | Add/delete/install/list/upgrade packages |
| `cache` | Cache operations (e.g. clear) |
| `env` | Environment/config info |
| `-V` / `--version` | Full version via `yazi-version` |

## Notes

Workspace default member alongside `yazi-fm`. Requires a live Yazi with matching client/DDS for most control commands.
