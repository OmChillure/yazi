# yazi-runner

## Purpose

Lua execution runner for isolated plugin jobs: spawns short-lived Lua states with a configured setter, loads plugin chunks, and runs entry/fetcher/preloader/previewer/spot entrypoints used by the scheduler and preview pipeline.

## Dependencies

- `yazi-binding`, `yazi-config`, `yazi-dds`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-version`
- External: `mlua`, `anyhow`, `tokio`, `tokio-util`, `tracing`, …

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `RUNNER`, `init(setter)` |
| `src/runner.rs` | `Runner::spawn` — new Lua isolate |
| `loader/` | Load/cache Lua plugin code |
| `entry/` | Generic plugin entry runner |
| `fetcher/` | Metadata/fetch plugins |
| `preloader/` | Preload plugins |
| `previewer/` | Preview plugins |
| `spot/` | Spot/metadata plugins |

## Key items

| Item | Description |
|------|-------------|
| `init(setter)` | Init loader + `RUNNER` with Lua setup fn |
| `RUNNER` | Global runner singleton |
| `Runner::spawn(name)` | New `Lua` + isolate `Runtime` + apply setter |
| Loader | Resolves plugin names to Lua bytecode/source |

## Notes

`yazi-fm` passes `yazi_plugin::slim_lua` as the setter so isolates get a reduced but sufficient API without the full interactive globals.
