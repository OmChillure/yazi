# yazi-packing

## Purpose

Packaging/distribution metadata only — not runtime library code. Holds Debian (`.deb`) package metadata via `cargo-deb` (`package.metadata.deb`) so release builds can produce installable packages with binaries, docs, and shell completions.

## Dependencies

None at runtime. `src/lib.rs` is intentionally empty.

## Main files

| File | Role |
|------|------|
| `Cargo.toml` | `package.metadata.deb` assets, depends, recommends |
| `src/lib.rs` | Empty placeholder |

## Key configuration

| Item | Description |
|------|-------------|
| Assets | Ships `yazi` and `ya` to `/usr/bin/`, README, bash completions |
| Depends | External tools: `file`, `ffmpeg`, `7zip`, `jq`, `poppler-utils`, `fd`, `ripgrep`, `fzf`, `zoxide`, `imagemagick`, clipboard utils |
| Recommends | `bash-completion` |

## Notes

Used only in release/packaging pipelines, not by the live file manager.
