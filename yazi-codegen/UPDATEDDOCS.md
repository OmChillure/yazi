# yazi-codegen — Updated crate notes

_Generated: 2026-06-22 via live Yazi MCP exploration + source scan._

## 1. What this crate is for

Build-time or proc-macro code generation supporting config, actions, or repetitive trait impls.

> Cargo description: *Yazi code generator*

## 2. Exploration snapshot (Yazi)

- **Path**: `/media/omchillure/Hackathon/yazi/yazi/yazi-codegen`
- **go_to ok**: `True`
- **Top-level entries**: `src`, `Cargo.toml`, `README.md`
- **Rust sources under `src/`**: 2 files

## 3. Dependencies

### Workspace / Yazi crates

- _(none or only indirect)_

### External (sample)

`proc-macro`, `proc-macro2`, `quote`, `syn`, `workspace`

## 4. Module / file map

| Module | Notes (from `lib.rs` / headers) |
|--------|----------------------------------|
| `helper` | — |

### Notable source files

- `src/helper.rs`
- `src/lib.rs`

## 5. Key public items

High-signal `pub` symbols discovered by scanning `src/**/*.rs` (not exhaustive):

| Kind | Name | Defined in |
|------|------|------------|
| `fn` | `named_fields` | `src/helper.rs` |
| `fn` | `ident_name` | `src/helper.rs` |
| `fn` | `generics_with_de` | `src/helper.rs` |
| `fn` | `has_serde_attr` | `src/helper.rs` |
| `fn` | `deserialize_over` | `src/lib.rs` |
| `fn` | `deserialize_over1` | `src/lib.rs` |
| `fn` | `deserialize_over2` | `src/lib.rs` |
| `fn` | `overlay` | `src/lib.rs` |
| `fn` | `from_lua` | `src/lib.rs` |

## 6. Entry / init surface

Primary entry file: **`src/lib.rs`**

```rust
use proc_macro::TokenStream;
use quote::quote;
mod helper;
use syn::{Data, DeriveInput, Fields, parse_macro_input};

use crate::helper::{generics_with_de, has_serde_attr, ident_name, named_fields};

#[proc_macro_derive(DeserializeOver)]
pub fn deserialize_over(input: TokenStream) -> TokenStream {
	let DeriveInput { ident, generics, .. } = parse_macro_input!(input as DeriveInput);
	let (impl_generics, ty_generics, where_clause) = generics.split_for_impl();

	quote! {
		impl #impl_generics yazi_shim::toml::DeserializeOverHook for #ident #ty_generics #where_clause {}
	}
	.into()
}

#[proc_macro_derive(DeserializeOver1)]
pub fn deserialize_over1(input: TokenStream) -> TokenStream {
	let DeriveInput { ident, generics, data, .. } = parse_macro_input!(input as DeriveInput);
	let (impl_generics, ty_generics, where_clause) = generics.split_for_impl();

	let visitor_generics = generics_with_de(&generics);
	let (impl_visitor_generics, ..) = visitor_generics.split_for_impl();
```

## 7. How it fits in Yazi

**Depends on (yazi-\*)**: _none_

**Depended on by (workspace scan)**: `yazi-config`, `yazi-binding`, `yazi-plugin`

## 8. Maintainer tips

- Start reading at `src/lib.rs` then drill into modules listed above.
- Prefer tracing call sites from `yazi-fm` / `yazi-cli` / `yazi-actor` when behavior is unclear.
- After behavior changes, consider whether `yazi-proxy`, DDS, or Lua bindings need matching updates.

---

*Replaces prior `DOCS.md` with this refreshed `UPDATEDDOCS.md` for `yazi-codegen`.*
