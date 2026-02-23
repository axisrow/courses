---
title: "Контрибьюция в GSD"
level: 3
lesson: 5
language: ru
tags: [gsd, contributing, open-source]
---

# Контрибьюция в GSD

## Введение

GSD — open-source проект с MIT лицензией. Вы можете вносить изменения, исправлять баги и добавлять фичи.

## Инструкции

### Начало работы

```bash
git clone https://github.com/glittercowboy/get-shit-done.git
cd get-shit-done
node bin/install.js --claude --local
```

Это установит GSD локально для тестирования изменений.

### Структура проекта

```
get-shit-done/
├── bin/
│   └── install.js          # Установщик
├── prompts/
│   └── claude/
│       └── commands/gsd/    # Slash-команды
├── docs/
│   └── USER-GUIDE.md       # Документация
└── README.md
```

### Что можно контрибьютить

- **Команды** — новые slash-команды или улучшение существующих
- **Документация** — исправления, переводы, примеры
- **Баг-фиксы** — исправление проблем
- **Рантаймы** — поддержка новых AI-агентов
- **Тесты** — улучшение покрытия

### Процесс

1. Форкните репозиторий
2. Создайте ветку: `git checkout -b feature/my-feature`
3. Внесите изменения
4. Тестируйте локально через `node bin/install.js --claude --local`
5. Создайте Pull Request

### Сообщество

- [Discord](https://discord.gg/5JJgD5svVS) — вопросы и обсуждения
- [GitHub Issues](https://github.com/glittercowboy/get-shit-done/issues) — баги и предложения
- [Twitter/X](https://x.com/gsd_foundation) — новости

## Примеры

```bash
# Тестирование изменений в команде
cd get-shit-done
# Отредактировать prompts/claude/commands/gsd/some-command.md
node bin/install.js --claude --local
# Открыть Claude Code и протестировать /gsd:some-command
```

## Итоги

- GSD — open-source (MIT)
- Клонируйте и устанавливайте локально для разработки
- Контрибьютить можно команды, документацию, фиксы
- Сообщество в Discord
- PR через стандартный GitHub-процесс
