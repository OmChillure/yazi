# yazi-tty — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

TTY/session management: acquiring the terminal, raw mode, alternate screen, and low-level IO hooks for the FM.

> Cargo description: *Yazi TTY access layer*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-tty`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 5 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-macro`
- `yazi-shim`

### External (sample)

`libc`, `parking_lot`, `tracing`, `windows-sys`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/handle` |
| module/file | `src/lib.rs` |
| module/file | `src/reader` |
| module/file | `src/tty` |
| module/file | `src/writer` |

### Notable source files

- `src/handle.rs`
- `src/lib.rs`
- `src/reader.rs`
- `src/tty.rs`
- `src/writer.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Handle` | `src/handle.rs` |
| `fn` | `new` | `src/handle.rs` |
| `fn` | `poll` | `src/handle.rs` |
| `fn` | `try_clone` | `src/handle.rs` |
| `static` | `TTY` | `src/lib.rs` |
| `fn` | `init` | `src/lib.rs` |
| `struct` | `TtyReader` | `src/reader.rs` |
| `struct` | `Tty` | `src/tty.rs` |
| `const` | `fn` | `src/tty.rs` |
| `fn` | `lockin` | `src/tty.rs` |
| `fn` | `lockout` | `src/tty.rs` |
| `fn` | `read_until` | `src/tty.rs` |
| `struct` | `TtyWriter` | `src/writer.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
yazi_macro::mod_flat!(handle reader tty writer);

pub static TTY: yazi_shim::cell::RoCell<Tty> = yazi_shim::cell::RoCell::new();

pub fn init() { TTY.with(<_>::default); }
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-macro`, `yazi-shim`

**Depended on by (workspace scan)**: `yazi-term`, `yazi-tui`, `yazi-build`, `yazi-config`, `yazi-emulator`, `yazi-adapter`, `yazi-binding`, `yazi-widgets`, `yazi-actor`, `yazi-fm`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-tty`.*
