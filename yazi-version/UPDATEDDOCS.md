# yazi-version — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Centralized version/build metadata and semver helpers shared by binaries and DDS/plugin version checks.

> Cargo description: *Yazi version information*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-version`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `build.rs`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 1 files

## 3. Dependencies

### Workspace / Yazi crates

- _(none or only indirect)_

### External (sample)

`vergen-gitcl`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/lib.rs` |

### Notable source files

- `src/lib.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `fn` | `version` | `src/lib.rs` |
| `fn` | `version_long` | `src/lib.rs` |
| `fn` | `version_full` | `src/lib.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
use std::{env::consts::{ARCH, OS}, fmt::Write};

pub fn version() -> &'static str { concat!(env!("CARGO_PKG_VERSION"), " ", env!("VERGEN_GIT_SHA")) }

pub fn version_long() -> &'static str {
	concat!(
		env!("CARGO_PKG_VERSION"),
		" (",
		env!("VERGEN_GIT_SHA"),
		" ",
		env!("VERGEN_BUILD_DATE"),
		")"
	)
}

pub fn version_full() -> String {
	let mut s = String::new();

	writeln!(s, "    Version: {}", version_long()).ok();
	writeln!(s, "    Debug  : {}", cfg!(debug_assertions)).ok();
	#[rustfmt::skip]
	writeln!(s, "    Triple : {} ({OS}-{ARCH})", env!("VERGEN_RUSTC_HOST_TRIPLE")).ok();
	#[rustfmt::skip]
	writeln!(s, "    Rustc  : {} ({} {})", env!("VERGEN_RUSTC_SEMVER"), &env!("VERGEN_RUSTC_COMMIT_HASH")[..8], env!("VERGEN_RUSTC_COMMIT_DATE")).ok();

```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: _none_

**Depended on by (workspace scan)**: `yazi-boot`, `yazi-dds`, `yazi-runner`, `yazi-cli`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-version`.*
