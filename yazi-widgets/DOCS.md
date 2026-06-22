# yazi-widgets

## Purpose

Reusable TUI widgets and input subsystem: text input actors/parsers, clipboard, scrollable regions, clear helpers, and step increments. Shared between core UI and actor handlers.

## Dependencies

- `yazi-macro`, `yazi-shared`, `yazi-shim`, `yazi-term`, plus ratatui/tokio as configured

## Main files / modules

| Module | Role |
|--------|------|
| `src/lib.rs` | `init()`, exports |
| `input/` | Input widget state, actors, parsers |
| Flat | `clear`, `clipboard`, `scrollable`, `step` |

## Key functions / items

| Item | Description |
|------|-------------|
| `init()` | Initializes `CLIPBOARD` global |
| `CLIPBOARD` | System/terminal clipboard abstraction |
| `input` module | Line/editor input with actor actions |
| `Scrollable` | Scroll/window helpers for lists |
| `Clear` / `Step` | UI utility widgets |

## Notes

`yazi-fm` calls `yazi_widgets::init()` during startup. Input actors integrate with `yazi-actor` / `yazi-core` input layer.
