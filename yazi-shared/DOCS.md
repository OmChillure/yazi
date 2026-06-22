# yazi-shared

## Purpose

Cross-cutting shared types and utilities for the whole workspace: events, URLs/paths, schemes, shell helpers, transliteration, pools, debouncing, IDs, layers, and environment/logging initialization.

## Dependencies

- `yazi-macro`, `yazi-shim`, `yazi-term`
- External: `anyhow`, `dyn-clone`, `foldhash`, `futures`, `hashbrown`, `inventory`, `memchr`, `mlua`, `ordered-float`, `parking_lot`, `paste`, `percent-encoding`, `serde`, `serde_with`, `strum`, `thiserror`, `tokio`, plus platform-specific deps

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Public modules + `init()` |
| `any_data/` | Type-erased event/plugin data |
| `data/` | Shared data payloads |
| `event/` | Global event bus / `Event` types |
| `loc/` | Location/span types |
| `path/` | Path abstractions |
| `pool/` | Object/string pools |
| `scheme/` | URL schemes (`file`, `archive`, `sftp`, …) |
| `shell/` | Shell command helpers |
| `strand/` | Strand/string segment utilities |
| `translit/` | Filename transliteration |
| `url/` | `Url` type used throughout FS/VFS |
| `wtf8/` | WTF-8 path handling (esp. Windows) |
| Flat modules | `alias`, `bytes`, `chars`, `debounce`, `env`, `id`, `kebab_cased_string`, `layer`, `localset`, `natsort`, `throttle`, `time`, etc. |

## Key functions / items

| Item | Description |
|------|-------------|
| `init()` | Sets up `LocalSet`, log level from `YAZI_LOG`, users cache (Unix), pools, events |
| `LOCAL_SET` | Tokio `LocalSet` for `!Send` tasks |
| `Event` | Core event types/init for app messaging |
| `Url` / schemes | Canonical location type across local/remote/archive |
| `KebabCasedString` | Config key normalization |
| Debounce/throttle | UI/event rate limiting |

## Notes

Initialize early (`yazi_shared::init()`) in both `yazi-fm` and `yazi-cli`.
