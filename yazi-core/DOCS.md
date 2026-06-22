# yazi-core

## Purpose

Application core state machine: owns the live `Core` struct aggregating manager, tabs/folders, tasks, and all modal UI subsystems (input, confirm, help, completion, which-key, pick, spot, notify). No I/O loop here — pure state + layout helpers.

## Dependencies

- `yazi-config`, `yazi-fs`, `yazi-macro`, `yazi-scheduler`, `yazi-shared`, `yazi-shim`, `yazi-term`, `yazi-widgets`, plus others
- External: `ratatui`, etc.

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | Module exports |
| `src/core.rs` | `Core` aggregate + `layer()` / `cursor()` |
| `mgr/` | Manager: tabs, yank, find, layout areas |
| `tab/` | Tab and folder state |
| `tasks/` | Tasks panel state (linked to scheduler) |
| `app/` | App-level core bits |
| `cmp/` | Completion popup state |
| `confirm/` | Confirm dialog state |
| `help/` | Help overlay state |
| `input/` | Input bar state |
| `notify/` | Toast/notify queue |
| `pick/` | Generic picker state |
| `spot/` | Spotlight/metadata spotter |
| `which/` | Which-key overlay |
| `highlighter.rs` | Syntax/highlight helpers |
| `proxy.rs` | Core-side proxy helpers |

## Key types / methods

| Item | Description |
|------|-------------|
| `Core::make()` | Construct default core (mgr + tasks service) |
| `Core::layer()` | Active `Layer` (Mgr/Input/Help/…) for keymap routing |
| `Core::cursor()` | Cursor position/style for TUI |
| `active()` / `current_mut()` | Active tab / current folder accessors |
| `Mgr` / `Tab` / `Folder` | Navigation model |

## Notes

Mutated by `yazi-actor` actors; rendered by `yazi-fm` UI modules; tasks backed by `yazi-scheduler`.
