# yazi-ffi

## Purpose

Thin foreign-function interface layer for platform-specific APIs Yazi needs outside the standard library — primarily macOS CoreFoundation/IOKit/DiskArbitration bindings for volume/mount information.

## Dependencies

- `yazi-macro`, `anyhow`
- **Unix:** `libc`
- **macOS:** `core-foundation-sys`, `objc2`

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | Conditionally includes macOS modules via `mod_flat!` |
| `src/cf_dict.rs` | CoreFoundation dictionary helpers |
| `src/cf_string.rs` | CFString conversions |
| `src/disk_arbitration.rs` | DiskArbitration volume queries |
| `src/io_kit.rs` | IOKit device/volume info |

## Key functionality

| Area | Description |
|------|-------------|
| CF types | Safe-ish wrappers around CFString/CFDictionary for mount metadata |
| DiskArbitration | Enumerate/describe mounted volumes on macOS |
| IOKit | Low-level disk/device properties |

## Notes

Only compiled on macOS for the platform modules; other targets get an effectively empty crate. Used by `yazi-fs` mounts subsystem.
