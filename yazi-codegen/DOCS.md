# yazi-codegen

## Purpose

Procedural macro crate that generates serde/TOML configuration overlay logic. Lets user config partially override defaults without losing unspecified fields — core to Yazi's config merging model.

## Dependencies

- `proc-macro2`, `quote`, `syn` (proc-macro toolchain)

## Main files

| File | Role |
|------|------|
| `src/lib.rs` | Derive macro implementations |
| `src/helper.rs` | Field/generic/attribute helpers for codegen |

## Key derives

| Derive | Description |
|--------|-------------|
| `DeserializeOver` | Implements `DeserializeOverHook` marker for TOML overlay |
| `DeserializeOver1` | Map-based deserialize-over with kebab-case keys and flatten support |
| `DeserializeOver2` | Variant using `Cow<str>` keys and per-field serde attrs |
| `Overlay` | Generates field-by-field overlay/merge from another instance |
| Lua-related derives | Bridge config types to/from Lua (`FromLua` / conversion helpers) |

## Notes

Works with `yazi-shim::toml` traits (`DeserializeOverWith`, `DeserializeOverSeed`). Consumed primarily by `yazi-config`.
