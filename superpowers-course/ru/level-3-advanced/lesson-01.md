---
title: "Архитектура Superpowers"
level: 3
lesson: 1
lang: ru
---

# Архитектура Superpowers

## Введение

Глубокое погружение в архитектуру системы навыков.

## Структура репозитория

```
superpowers/
├── skills/                    # Навыки
│   ├── brainstorming/
│   │   └── SKILL.md
│   ├── test-driven-development/
│   │   └── SKILL.md
│   ├── subagent-driven-development/
│   │   └── SKILL.md
│   └── ...
├── docs/                      # Документация
├── .claude/                   # Конфигурация Claude Code
├── .codex/                    # Конфигурация Codex
├── .opencode/                 # Конфигурация OpenCode
└── README.md
```

## Как работают навыки

Каждый навык — это файл `SKILL.md` с инструкциями для агента. Когда агент видит определённый контекст, он загружает соответствующий навык.

### Цепочка навыков

```
brainstorming → using-git-worktrees → writing-plans → 
subagent-driven-development → test-driven-development → 
requesting-code-review → finishing-a-development-branch
```

## Система активации

Навыки проверяются **перед каждой задачей**. Это обязательные workflow, не предложения.

## Коммуникация между навыками

Навыки общаются через артефакты:
- Спецификация (brainstorming → writing-plans)
- План (writing-plans → subagent-driven-development)
- Код и тесты (subagent-driven-development → code-review)

## Итоги

- Навыки живут в `skills/*/SKILL.md`
- Активируются автоматически по контексту
- Образуют цепочку от идеи до мержа
- Общаются через артефакты (документы, код)
