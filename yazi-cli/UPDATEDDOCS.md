# yazi-cli — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Companion `ya` CLI: DDS client commands (emit, pub, sub, pack, etc.) for scripting and automation.

> Cargo description: *Yazi command-line interface*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-cli`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `build.rs`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 22 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-adapter`
- `yazi-boot`
- `yazi-config`
- `yazi-dds`
- `yazi-emulator`
- `yazi-fs`
- `yazi-macro`
- `yazi-shared`
- `yazi-term`
- `yazi-tty`
- `yazi-version`

### External (sample)

`anyhow`, `bin-dir`, `clap`, `clap_complete`, `clap_complete_fig`, `clap_complete_nushell`, `hashbrown`, `path`, `pkg-url`, `regex`, `serde`, `serde_json`, `tokio`, `toml`, `twox-hash`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/args` |
| module/file | `src/cache` |
| module/file | `src/dds` |
| module/file | `src/env` |
| module/file | `src/main.rs` |
| module/file | `src/package` |
| module/file | `src/shared` |

### Notable source files

- `src/args.rs`
- `src/cache/clear.rs`
- `src/cache/mod.rs`
- `src/dds/draw.rs`
- `src/dds/exec.rs`
- `src/dds/mod.rs`
- `src/dds/shot.rs`
- `src/env/env.rs`
- `src/env/mod.rs`
- `src/main.rs`
- `src/package/add.rs`
- `src/package/delete.rs`
- `src/package/dependency.rs`
- `src/package/deploy.rs`
- `src/package/git.rs`
- `src/package/hash.rs`
- `src/package/install.rs`
- `src/package/mod.rs`
- `src/package/package.rs`
- `src/package/upgrade.rs`
- `src/shared/mod.rs`
- `src/shared/shared.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `Args` | `src/args.rs` |
| `enum` | `Command` | `src/args.rs` |
| `struct` | `CommandEmit` | `src/args.rs` |
| `struct` | `CommandEmitTo` | `src/args.rs` |
| `struct` | `CommandExec` | `src/args.rs` |
| `enum` | `CommandPkg` | `src/args.rs` |
| `struct` | `CommandPub` | `src/args.rs` |
| `fn` | `receiver` | `src/args.rs` |
| `struct` | `CommandPubTo` | `src/args.rs` |
| `struct` | `CommandSub` | `src/args.rs` |
| `enum` | `CommandCache` | `src/args.rs` |
| `fn` | `body` | `src/args.rs` |
| `fn` | `clear` | `src/cache/clear.rs` |
| `struct` | `Cache` | `src/cache/mod.rs` |
| `fn` | `draw` | `src/dds/draw.rs` |
| `fn` | `exec` | `src/dds/exec.rs` |
| `struct` | `Dds` | `src/dds/mod.rs` |
| `fn` | `shot` | `src/dds/shot.rs` |
| `fn` | `ensure_version` | `src/dds/shot.rs` |
| `fn` | `ensure_ability` | `src/dds/shot.rs` |
| `fn` | `print` | `src/env/env.rs` |
| `struct` | `Env` | `src/env/mod.rs` |
| `fn` | `add` | `src/package/add.rs` |
| `fn` | `delete` | `src/package/delete.rs` |
| `fn` | `delete_assets` | `src/package/delete.rs` |
| `fn` | `delete_sources` | `src/package/delete.rs` |
| `struct` | `Dependency` | `src/package/dependency.rs` |
| `fn` | `local` | `src/package/dependency.rs` |
| `fn` | `remote` | `src/package/dependency.rs` |
| `fn` | `target` | `src/package/dependency.rs` |
| `fn` | `identical` | `src/package/dependency.rs` |
| `fn` | `header` | `src/package/dependency.rs` |
| `fn` | `plugin_files` | `src/package/dependency.rs` |
| `fn` | `flavor_files` | `src/package/dependency.rs` |
| `fn` | `deploy` | `src/package/deploy.rs` |

## 6. Entry / init surface

Primary entry file: **`src/main.rs`**

```rust
yazi_macro::mod_pub!(cache dds env package shared);

yazi_macro::mod_flat!(args);

use std::process::ExitCode;

use clap::Parser;
use yazi_macro::{errln, outln};
use yazi_shared::LOCAL_SET;

#[tokio::main]
async fn main() -> ExitCode {
	yazi_shared::init();
	yazi_fs::init();

	match LOCAL_SET.run_until(run()).await {
		Ok(()) => ExitCode::SUCCESS,
		Err(e) => {
			for cause in e.chain() {
				if let Some(ioerr) = cause.downcast_ref::<std::io::Error>()
					&& ioerr.kind() == std::io::ErrorKind::BrokenPipe
				{
					return ExitCode::from(0);
				}
			}
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-adapter`, `yazi-boot`, `yazi-config`, `yazi-dds`, `yazi-emulator`, `yazi-fs`, `yazi-macro`, `yazi-shared`, `yazi-term`, `yazi-tty`, `yazi-version`

**Depended on by (workspace scan)**: _leaf or only indirect_

## 8. Maintainer tips

- Start reading at `src/main.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-cli`.*
