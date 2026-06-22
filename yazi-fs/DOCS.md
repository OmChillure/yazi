# yazi-fs

## Purpose

Local filesystem abstraction: file metadata (Cha), mounts, XDG paths, providers for ordinary disk I/O.

**Crate description (Cargo.toml):** Yazi file system

## Dependencies (workspace)

`yazi-ffi`, `yazi-macro`, `yazi-shared`, `yazi-shim`

## Module map

Public/internal modules exported from the crate root:

- `cha`
- `error`
- `mounts`
- `path`
- `provider`
- `cwd`
- `file`
- `files`
- `filter`
- `fns`
- `hash`
- `op`
- `scheme`
- `sorter`
- `sorting`
- `splatter`
- `stage`
- `url`
- `xdg`

## Main files

- `src/lib.rs` — entry/core
- `src/cha` (dir)
- `src/cwd.rs` (file)
- `src/error` (dir)
- `src/file.rs` (file)
- `src/files.rs` (file)
- `src/filter.rs` (file)
- `src/fns.rs` (file)
- `src/hash.rs` (file)
- `src/lib.rs` (file)
- `src/mounts` (dir)
- `src/op.rs` (file)
- `src/path` (dir)
- `src/provider` (dir)
- `src/scheme.rs` (file)
- `src/sorter.rs` (file)
- `src/sorting.rs` (file)
- `src/splatter.rs` (file)
- `src/stage.rs` (file)
- `src/url.rs` (file)
- `src/xdg.rs` (file)

## Key public items

- **src/cha/cha.rs**: `struct Cha`
- **src/cha/type.rs**: `enum ChaType`
- **src/cwd.rs**: `static CWD`, `struct Cwd`
- **src/error/error.rs**: `enum Error`
- **src/file.rs**: `struct File`
- **src/files.rs**: `struct Files`
- **src/filter.rs**: `struct Filter`, `enum FilterCase`
- **src/fns.rs**: `fn ok_or_not_found`, `fn max_common_root`, `fn create_owned_dir`, `fn create_owned_dir_blocking`
- **src/hash.rs**: `trait FsHash64`, `trait FsHash128`
- **src/lib.rs**: `fn init`
- **src/mounts/partition.rs**: `struct Partition`
- **src/mounts/partitions.rs**: `static PARTITIONS`, `struct Partitions`
- **src/op.rs**: `static FILES_TICKET`, `enum FilesOp`
- **src/path/clean.rs**: `fn clean_url`
- **src/path/expand.rs**: `fn expand_url`
- **src/path/path.rs**: `fn skip_url`
- **src/path/percent.rs**: `trait PercentEncoding`
- **src/path/relative.rs**: `fn path_relative_to`
- **src/provider/attrs.rs**: `struct Attrs`
- **src/provider/capabilities.rs**: `struct Capabilities`
- **src/provider/local/absolute.rs**: `fn try_absolute`
- **src/provider/local/calculator.rs**: `enum SizeCalculator`
- **src/provider/local/casefold.rs**: `fn match_name_case`
- **src/provider/local/dir_entry.rs**: `enum DirEntry`
- **src/provider/local/gate.rs**: `struct Gate`

## Source layout (partial)

```
src/cha/cha.rs
src/cha/kind.rs
src/cha/mod.rs
src/cha/mode.rs
src/cha/type.rs
src/cwd.rs
src/error/error.rs
src/error/mod.rs
src/error/serde.rs
src/file.rs
src/files.rs
src/filter.rs
src/fns.rs
src/hash.rs
src/lib.rs
src/mounts/linux.rs
src/mounts/macos.rs
src/mounts/mod.rs
src/mounts/partition.rs
src/mounts/partitions.rs
src/op.rs
src/path/clean.rs
src/path/expand.rs
src/path/mod.rs
src/path/path.rs
src/path/percent.rs
src/path/relative.rs
src/provider/attrs.rs
src/provider/capabilities.rs
src/provider/local/absolute.rs
src/provider/local/calculator.rs
src/provider/local/casefold.rs
src/provider/local/copier.rs
src/provider/local/dir_entry.rs
src/provider/local/gate.rs
src/provider/local/identical.rs
src/provider/local/local.rs
src/provider/local/mod.rs
src/provider/local/read_dir.rs
src/provider/mod.rs
src/provider/traits.rs
src/scheme.rs
src/sorter.rs
src/sorting.rs
src/splatter.rs
src/stage.rs
src/url.rs
src/xdg.rs
```

## Notes for contributors

- Prefer reading `src/lib.rs` (or `src/main.rs` for binaries) first, then the modules listed under `mod_pub!` / `mod_flat!`.
- Many crates use `yazi_macro::mod_pub!` / `mod_flat!` to declare modules; this is equivalent to normal `mod` + `pub use` patterns.
- Cross-crate flow often goes: **config/boot → core/vfs/fs → actor/proxy/scheduler → fm/cli/plugin**.

---
_Auto-generated documentation from codebase exploration (Yazi MCP + source reads)._
