# yazi-dds

## Purpose

Data Distribution Service for Yazi: client/server pub-sub so multiple Yazi instances (and `ya` CLI) can communicate — emit events, share state, synchronize tabs/CD, and integrate external tools.

## Dependencies

- `yazi-macro`, `yazi-shared`, `yazi-shim`, and related crates per Cargo.toml
- External: `anyhow`, `serde`, `tokio`, etc.

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Crate entry / init |
| `src/client.rs` | DDS client connecting to a Yazi instance |
| `src/server.rs` | In-process/server side receiver |
| `src/pubsub.rs` | Publish/subscribe hub |
| `src/pump.rs` | Event pump/loop |
| `src/payload.rs` | Message payloads |
| `src/sendable.rs` | Serializable sendables |
| `src/state.rs` | Shared DDS state |
| `src/stream.rs` | Transport streams |
| `src/ember/` | Ember event types (typed DDS messages) |

## Key concepts

| Concept | Description |
|---------|-------------|
| Client ID | `YAZI_ID` / `--client-id` targeting |
| Embers | Typed events (hover, cd, load, …) |
| PubSub | Topic-based broadcast within/between processes |
| `ya` integration | CLI subcommands publish/subscribe via DDS |

## Notes

Powers `ya emit`, `ya pub`, instance coordination, and MCP/external control patterns.
