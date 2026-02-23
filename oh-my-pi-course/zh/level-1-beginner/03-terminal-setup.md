---
title: "终端设置"
level: 1
lesson: 3
lang: zh
tags: [终端, kitty, iterm, ghostty, wezterm]
---

# 终端设置

## 介绍

OMP 使用 Kitty 键盘协议来可靠地检测修饰键。大多数现代终端支持此协议，但部分需要配置。

## 开箱即用的终端

- **Kitty** — 直接可用
- **iTerm2** — 直接可用

## Ghostty

添加到 `~/.config/ghostty/config`：

```
keybind = alt+backspace=text:\x1b\x7f
keybind = shift+enter=text:\n
```

## WezTerm

创建 `~/.wezterm.lua`：

```lua
local wezterm = require 'wezterm'
local config = wezterm.config_builder()
config.enable_kitty_keyboard = true
return config
```

## Windows Terminal

Windows Terminal 不支持 Kitty 键盘协议。Shift+Enter 无法与 Enter 区分。请使用 Ctrl+Enter 进行多行输入。其他快捷键正常工作。

## 常用快捷键

| 按键 | 操作 |
|------|------|
| Enter | 发送消息 |
| Shift+Enter | 换行 |
| Escape | 取消流式输出 |
| Ctrl+C | 清除/退出 |
| Tab | 路径补全 |
| Ctrl+R | 搜索历史 |
| Ctrl+L | 模型选择器 |

## 总结

最佳体验请使用 Kitty、iTerm2 或配置 Ghostty/WezTerm。Windows Terminal 也可使用但有限制。
