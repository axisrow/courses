---
title: "Архитектура монорепо"
weight: 1
bookToc: true
---

# Архитектура монорепо

## Введение

Pi Mono организован как монорепозиторий (monorepo) — все пакеты живут в одном Git-репозитории и управляются через npm workspaces.

## Структура проекта

```
pi-mono/
├── packages/
│   ├── ai/              # Unified LLM API
│   ├── agent/           # Agent runtime
│   ├── coding-agent/    # CLI coding assistant
│   ├── mom/             # Slack bot
│   ├── tui/             # Terminal UI
│   ├── web-ui/          # Web components
│   └── pods/            # GPU pod management
├── package.json         # Root workspace config
├── AGENTS.md            # Project rules
├── CONTRIBUTING.md      # Contribution guide
└── test.sh              # Test runner
```

## Зависимости между пакетами

```
coding-agent → agent → ai
                ↓
mom ──────────→ agent → ai
                        ↑
web-ui ─────────────────┘
tui (независимый)
pods (независимый)
```

## Команды разработки

```bash
npm install          # Установить все зависимости
npm run build        # Собрать все пакеты
npm run check        # Линтинг, форматирование, проверка типов
./test.sh            # Запустить тесты
```

## Важно

`npm run check` требует предварительного `npm run build`, так как web-ui использует скомпилированные `.d.ts` файлы зависимостей.

## Итоги

- Pi Mono — монорепо с npm workspaces
- 7 пакетов с чёткими зависимостями
- Единая система сборки и тестирования
