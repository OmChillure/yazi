# yazi-version

## Purpose

Provides compile-time and runtime version/build information for Yazi binaries (`yazi` and `ya`). Uses `vergen-gitcl` at build time to embed git SHA, build date, and rustc metadata so `--version` and diagnostics always reflect the exact build.

## Dependencies

- **Build:** `vergen-gitcl` (git/build/rustc info)

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | All version helpers |
| `build.rs` | Invokes vergen to emit `VERGEN_*` env vars |

## Key functions

| Function | Description |
|----------|-------------|
| `version()` | Short string: `CARGO_PKG_VERSION` + git SHA |
| `version_long()` | Version with SHA and build date |
| `version_full()` | Multi-line report (version, debug flag, target triple, rustc semver/commit) |

## Notes

Internal crate — no stable external API guarantee. Used by `yazi-boot`, `yazi-cli`, and `yazi-runner`.
