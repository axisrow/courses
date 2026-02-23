---
title: "Отличия от pi-mono"
level: 3
lesson: 2
lang: ru
tags: [pi-mono, форк, отличия, сравнение]
---

# Отличия от pi-mono

## Введение

OMP — форк pi-mono с существенными дополнениями. Рассмотрим ключевые отличия.

## Новые инструменты

| Функция | pi-mono | OMP |
|---------|---------|-----|
| Hashline-редактирование | ❌ | ✅ |
| Commit Tool (AI-коммиты) | ❌ | ✅ |
| Python Tool (IPython) | ❌ | ✅ |
| LSP-интеграция (40+ языков) | ❌ | ✅ |
| TTSR (правила по триггеру) | ❌ | ✅ |
| Task Tool (субагенты) | ❌ | ✅ |
| Code Review (/review) | ❌ | ✅ |
| Todo Tool | ❌ | ✅ |
| Ask Tool | ❌ | ✅ |
| Browser (14 stealth-скриптов) | ❌ | ✅ |
| SSH Tool | ❌ | ✅ |
| Image Generation | ❌ | ✅ |

## Нативный движок

pi-mono использует внешние утилиты (ripgrep, bash). OMP включает 7500 строк Rust N-API для встроенных grep, shell, подсветки синтаксиса и других модулей.

## Universal Config Discovery

OMP загружает конфигурацию из 8 инструментов: Claude Code, Cursor, Windsurf, Gemini, Codex, Cline, GitHub Copilot, VS Code.

## Расширенная поддержка провайдеров

- Больше провайдеров (30+)
- Мульти-credential с round-robin
- Cursor Provider
- Роли моделей (smol, slow, plan, commit)

## TUI

- 65+ тем
- Powerline-footer со статусом
- Автоматические заголовки сессий
- LSP-статус в интерфейсе
- Todo-панель (Ctrl+T)

## Итоги

OMP значительно расширяет pi-mono: hashline, нативный движок, субагенты, LSP, десятки новых инструментов и провайдеров.
