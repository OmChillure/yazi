# yazi-ffi — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Foreign-function / C-interop helpers where Yazi needs to call or expose non-Rust interfaces.

> Cargo description: *Yazi foreign function interface*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-ffi`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 5 files

## 3. Dependencies

### Workspace / Yazi crates

- `yazi-macro`

### External (sample)

`anyhow`, `core-foundation-sys`, `libc`, `objc2`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/cf_dict` |
| module/file | `src/cf_string` |
| module/file | `src/disk_arbitration` |
| module/file | `src/io_kit` |
| module/file | `src/lib.rs` |

### Notable source files

- `src/cf_dict.rs`
- `src/cf_string.rs`
- `src/disk_arbitration.rs`
- `src/io_kit.rs`
- `src/lib.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `struct` | `CFDict` | `src/cf_dict.rs` |
| `fn` | `take` | `src/cf_dict.rs` |
| `fn` | `value` | `src/cf_dict.rs` |
| `fn` | `bool` | `src/cf_dict.rs` |
| `fn` | `integer` | `src/cf_dict.rs` |
| `fn` | `os_string` | `src/cf_dict.rs` |
| `fn` | `path_buf` | `src/cf_dict.rs` |
| `struct` | `CFString` | `src/cf_string.rs` |
| `fn` | `new` | `src/cf_string.rs` |
| `fn` | `len` | `src/cf_string.rs` |
| `fn` | `is_empty` | `src/cf_string.rs` |
| `fn` | `DASessionCreate` | `src/disk_arbitration.rs` |
| `fn` | `DADiskCreateFromBSDName` | `src/disk_arbitration.rs` |
| `fn` | `DADiskCopyDescription` | `src/disk_arbitration.rs` |
| `fn` | `DARegisterDiskAppearedCallback` | `src/disk_arbitration.rs` |
| `fn` | `DARegisterDiskDescriptionChangedCallback` | `src/disk_arbitration.rs` |
| `fn` | `DARegisterDiskDisappearedCallback` | `src/disk_arbitration.rs` |
| `fn` | `DASessionScheduleWithRunLoop` | `src/disk_arbitration.rs` |
| `fn` | `IOServiceGetMatchingServices` | `src/io_kit.rs` |
| `fn` | `IOServiceMatching` | `src/io_kit.rs` |
| `fn` | `IOIteratorNext` | `src/io_kit.rs` |
| `fn` | `IORegistryEntryCreateCFProperty` | `src/io_kit.rs` |
| `fn` | `IOObjectRelease` | `src/io_kit.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
#[cfg(target_os = "macos")]
yazi_macro::mod_flat!(cf_dict cf_string disk_arbitration io_kit);
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: `yazi-macro`

**Depended on by (workspace scan)**: `yazi-fs`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-ffi`.*
