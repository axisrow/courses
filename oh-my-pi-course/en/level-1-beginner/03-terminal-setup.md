---
title: "Terminal Setup"
level: 1
lesson: 3
lang: en
tags: [terminal, kitty, iterm, ghostty, wezterm]
---

# Terminal Setup

## Introduction

OMP uses the Kitty keyboard protocol for reliable modifier key detection. Most modern terminals support it, but some need configuration.

## Terminals That Work Out of the Box

- **Kitty** — works immediately
- **iTerm2** — works immediately

## Ghostty

Add to `~/.config/ghostty/config`:

```
keybind = alt+backspace=text:\x1b\x7f
keybind = shift+enter=text:\n
```

## WezTerm

Create `~/.wezterm.lua`:

```lua
local wezterm = require 'wezterm'
local config = wezterm.config_builder()
config.enable_kitty_keyboard = true
return config
```

## Windows Terminal

Windows Terminal doesn't support the Kitty keyboard protocol. Shift+Enter can't be distinguished from Enter. Use Ctrl+Enter for multi-line input instead. All other shortcuts work correctly.

## Useful Shortcuts

| Key | Action |
|-----|--------|
| Enter | Send message |
| Shift+Enter | New line |
| Escape | Cancel streaming |
| Ctrl+C | Clear / exit |
| Tab | Path completion |
| Ctrl+R | Search history |
| Ctrl+L | Model selector |

## Summary

For the best experience use Kitty, iTerm2, or configure Ghostty/WezTerm. Windows Terminal works with limitations.
