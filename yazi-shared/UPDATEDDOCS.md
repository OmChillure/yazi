# yazi-shared — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Workspace-wide shared primitives: URLs/schemes, events, pools, debounce/throttle, env/logging init, and misc utilities.

> Cargo description: *Yazi shared library*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-shared`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 102 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-macro`
- `yazi-shim`
- `yazi-term`

### External (sample)

`anyhow`, `dyn-clone`, `foldhash`, `futures`, `hashbrown`, `inventory`, `libc`, `memchr`, `mlua`, `ordered-float`, `parking_lot`, `paste`, `percent-encoding`, `serde`, `serde_with`, `strum`, `thiserror`, `tokio`, `typed-path`, `uzers`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/alias` |
| module/file | `src/any_data` |
| module/file | `src/bytes` |
| module/file | `src/chars` |
| module/file | `src/completion_token` |
| module/file | `src/condition` |
| module/file | `src/data` |
| module/file | `src/debounce` |
| module/file | `src/env` |
| module/file | `src/event` |
| module/file | `src/id` |
| module/file | `src/kebab_cased_string` |
| module/file | `src/last_value` |
| module/file | `src/layer` |
| module/file | `src/lib.rs` |
| module/file | `src/loc` |
| module/file | `src/localset` |
| module/file | `src/natsort` |
| module/file | `src/non_empty_string` |
| module/file | `src/os` |
| module/file | `src/path` |
| module/file | `src/pool` |
| module/file | `src/predictor` |
| module/file | `src/scheme` |
| module/file | `src/shell` |
| module/file | `src/snake_cased_string` |
| module/file | `src/source` |
| module/file | `src/strand` |
| module/file | `src/tests` |
| module/file | `src/throttle` |
| module/file | `src/time` |
| module/file | `src/translit` |
| module/file | `src/url` |
| module/file | `src/wtf8` |

### Notable source files

- `src/alias.rs`
- `src/any_data.rs`
- `src/bytes.rs`
- `src/chars.rs`
- `src/completion_token.rs`
- `src/condition.rs`
- `src/data/any.rs`
- `src/data/data.rs`
- `src/data/de.rs`
- `src/data/de_bytes.rs`
- `src/data/de_key.rs`
- `src/data/de_owned.rs`
- `src/data/inventory.rs`
- `src/data/key.rs`
- `src/data/macros.rs`
- `src/data/mod.rs`
- `src/debounce.rs`
- `src/env.rs`
- `src/event/action.rs`
- `src/event/cmd.rs`
- `src/event/cow.rs`
- `src/event/de.rs`
- `src/event/de_owned.rs`
- `src/event/event.rs`
- `src/event/mod.rs`
- `src/id.rs`
- `src/kebab_cased_string.rs`
- `src/last_value.rs`
- `src/layer.rs`
- `src/lib.rs`
- _…and 72 more_

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `type` | `SStr` | `src/alias.rs` |
| `struct` | `AnyData` | `src/any_data.rs` |
| `trait` | `BytesExt` | `src/bytes.rs` |
| `fn` | `strip_trailing_newline` | `src/chars.rs` |
| `fn` | `replace_cow` | `src/chars.rs` |
| `fn` | `replacen_cow` | `src/chars.rs` |
| `fn` | `replace_vec_cow` | `src/chars.rs` |
| `fn` | `replace_to_printable` | `src/chars.rs` |
| `fn` | `push_printable_char` | `src/chars.rs` |
| `struct` | `CompletionToken` | `src/completion_token.rs` |
| `fn` | `complete` | `src/completion_token.rs` |
| `fn` | `completed` | `src/completion_token.rs` |
| `fn` | `future` | `src/completion_token.rs` |
| `enum` | `ConditionOp` | `src/condition.rs` |
| `fn` | `new` | `src/condition.rs` |
| `struct` | `Condition` | `src/condition.rs` |
| `fn` | `eval` | `src/condition.rs` |
| `trait` | `DataAny` | `src/data/any.rs` |
| `fn` | `downcast_ref` | `src/data/any.rs` |
| `fn` | `downcast` | `src/data/any.rs` |
| `enum` | `Data` | `src/data/data.rs` |
| `fn` | `as_str` | `src/data/data.rs` |
| `fn` | `as_any` | `src/data/data.rs` |
| `fn` | `into_sstr` | `src/data/data.rs` |
| `fn` | `into_any` | `src/data/data.rs` |
| `fn` | `into_any2` | `src/data/data.rs` |
| `struct` | `BytesDeserializer` | `src/data/de_bytes.rs` |
| `enum` | `KeyDeserializer` | `src/data/de_key.rs` |
| `struct` | `DataInventory` | `src/data/inventory.rs` |
| `enum` | `DataKey` | `src/data/key.rs` |
| `fn` | `is_integer` | `src/data/key.rs` |
| `fn` | `float_to_i64` | `src/data/macros.rs` |
| `struct` | `Debounce` | `src/debounce.rs` |
| `static` | `LOG_LEVEL` | `src/env.rs` |
| `fn` | `env_exists` | `src/env.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
extern crate self as yazi_shared;

yazi_macro::mod_pub!(any_data data event loc path pool scheme shell strand translit url wtf8);

yazi_macro::mod_flat!(alias bytes chars completion_token condition debounce env id kebab_cased_string last_value layer localset natsort non_empty_string os predictor snake_cased_string source tests throttle time);

pub fn init() {
	LOCAL_SET.with(tokio::task::LocalSet::new);

	LOG_LEVEL.replace(<_>::from(std::env::var("YAZI_LOG").unwrap_or_default()));

	#[cfg(unix)]
	USERS_CACHE.with(<_>::default);

	pool::init();
	event::Event::init();
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-macro`, `yazi-shim`, `yazi-term`

**Depended on by (workspace scan)**: `yazi-tui`, `yazi-fs`, `yazi-vfs`, `yazi-watcher`, `yazi-config`, `yazi-boot`, `yazi-emulator`, `yazi-adapter`, `yazi-dds`, `yazi-proxy`, `yazi-parser`, `yazi-binding`, `yazi-widgets`, `yazi-core`, `yazi-plugin`
  _(and 5 more)_

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-shared`.*
