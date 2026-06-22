# yazi-build

## Purpose

Placeholder/helper binary for crates.io users. Prints installation guidance rather than building Yazi itself — steers people toward the documented install methods (`cargo install --locked yazi-fm yazi-cli` or distro packages).

## Dependencies

- **Build:** `anyhow`, `yazi-tty` (build-script side effects if any)

## Main files

| File | Role |
|------|------|
| `src/main.rs` | Prints install URL/message |
| `build.rs` | Build-time hooks |

## Key behavior

| Item | Description |
|------|-------------|
| `main()` | Emits message pointing at https://yazi-rs.github.io/docs/installation#crates |

## Notes

Not part of the normal runtime graph for `yazi`/`ya` execution.
