# yazi-packing — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Archive/packing utilities (compress/extract/list) backing archive:// and related operations.

> Cargo description: *Yazi packing*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-packing`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 1 files

## 3. Dependencies

### Workspace / Yazi crates

- _(none or only indirect)_

### External (sample)

`assets`, `depends`, `extended-description-file`, `license-file`, `priority`, `recommends`, `section`, `workspace`

## 4. Module / file map

| Area | Path |
|------|------|
| module/file | `src/lib.rs` |

### Notable source files

- `src/lib.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

_No straightforward top-level `pub` items parsed (crate may be macros-only, re-exports, or heavily gated)._

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust

```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: _none_

**Depended on by (workspace scan)**: _leaf or only indirect_

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-packing`.*
