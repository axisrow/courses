---
title: "Настройка терминала"
level: 1
lesson: 3
lang: ru
tags: [терминал, kitty, iterm, ghostty, wezterm]
---

# Настройка терминала

## Введение

OMP использует Kitty keyboard protocol для надёжного определения клавиш. Большинство терминалов поддерживают его, но некоторые требуют настройки.

## Терминалы, работающие сразу

- **Kitty** — работает из коробки
- **iTerm2** — работает из коробки

## Ghostty

Добавьте в `~/.config/ghostty/config`:

```
keybind = alt+backspace=text:\x1b\x7f
keybind = shift+enter=text:\n
```

## WezTerm

Создайте `~/.wezterm.lua`:

```lua
local wezterm = require 'wezterm'
local config = wezterm.config_builder()
config.enable_kitty_keyboard = true
return config
```

## Windows Terminal

Windows Terminal не поддерживает Kitty keyboard protocol. Shift+Enter не отличается от Enter. Используйте Ctrl+Enter для многострочного ввода. Остальные горячие клавиши работают.

## Полезные горячие клавиши

| Клавиша | Действие |
|---------|----------|
| Enter | Отправить сообщение |
| Shift+Enter | Новая строка |
| Escape | Отменить стриминг |
| Ctrl+C | Очистить / выйти |
| Tab | Автодополнение пути |
| Ctrl+R | Поиск по истории |
| Ctrl+L | Выбор модели |

## Итоги

Для лучшего опыта используйте Kitty, iTerm2 или настройте Ghostty/WezTerm. Windows Terminal тоже работает с ограничениями.
