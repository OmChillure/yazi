# yazi-build — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Build-script and packaging helpers invoked while compiling workspace members.

> Cargo description: *Yazi build system*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-build`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `build.rs`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 1 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-tty`

### External (sample)

`anyhow`, `path`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/main.rs` |

### Notable source files

- `src/main.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

_No straightforward top-level `pub` items parsed (crate may be macros-only, re-exports, or heavily gated)._

## 6. Entry / init surface

Primary entry file: **`src/main.rs`**

```rust
fn main() {
	println!("See https://yazi-rs.github.io/docs/installation#crates on how to install Yazi.");
}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-tty`

**Depended on by (workspace scan)**: _leaf or only indirect_

## 8. Maintainer tips

- Start reading at `src/main.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-build`.*
