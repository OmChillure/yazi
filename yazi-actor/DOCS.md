# yazi-actor

## Purpose

Actor model implementation: each user/system action is an `Actor` with a typed `Form` (from `yazi-parser`) that mutates `Ctx` (core + lives + context) and returns `Data`. Organized by UI layer/subsystem mirroring `yazi-core` and `yazi-parser`.

## Dependencies

- Nearly the full stack: `yazi-binding`, `yazi-boot`, `yazi-config`, `yazi-core`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-parser`, `yazi-plugin`, `yazi-proxy`, `yazi-runner`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-tty`, `yazi-tui`, …

## Main files / modules

| Module | Role |
|--------|------|
| `src/actor.rs` | `Actor` trait (`NAME`, `act`, optional `hook`) |
| `src/context.rs` | `Ctx` — mutable context passed to actors |
| `app/` | App actors (quit, resize, plugin, render, …) |
| `mgr/` | Manager actors (~62 files: navigation, yank, tabs, …) |
| `cmp/`, `confirm/`, `help/`, `input/` | Modal actors |
| `notify/`, `pick/`, `spot/`, `tasks/`, `which/` | Subsystem actors |
| `core/` | Core/preflight actors |
| `lives/` | Lua “lives” / live value access during actor run |

## Key types

| Type | Description |
|------|-------------|
| `Actor` | Trait: `act(cx, form) -> Result<Data>` |
| `Ctx` | Context with core state, tabs, scheduler handles |
| `hook()` | Optional `SparkKind` for plugin interception |
| Per-action structs | One actor per parsed command form |

## Notes

Executed from `yazi-fm` dispatcher/executor after keymap/DDS/CLI routes a command through the parser.
