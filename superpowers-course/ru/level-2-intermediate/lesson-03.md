---
title: "Навыки (Skills)"
level: 2
lesson: 3
lang: ru
---

# Навыки (Skills)

## Введение

Обзор всех навыков Superpowers и когда они активируются.

## Категории навыков

### Тестирование
- **test-driven-development** — RED-GREEN-REFACTOR цикл с антипаттернами

### Отладка
- **systematic-debugging** — 4-фазный процесс поиска причины
- **verification-before-completion** — проверка перед объявлением «готово»

### Совместная работа
- **brainstorming** — сократический метод уточнения дизайна
- **writing-plans** — детальные планы реализации
- **executing-plans** — пакетное выполнение с чекпоинтами
- **dispatching-parallel-agents** — параллельные субагенты
- **subagent-driven-development** — итеративная разработка с двухэтапной проверкой

### Code Review
- **requesting-code-review** — чеклист перед review
- **receiving-code-review** — реакция на фидбек

### Git
- **using-git-worktrees** — параллельные ветки
- **finishing-a-development-branch** — завершение работы

### Мета
- **writing-skills** — создание новых навыков
- **using-superpowers** — введение в систему

## Когда навыки активируются

Навыки активируются **автоматически** по контексту:

| Триггер | Навык |
|---------|-------|
| Новая задача | brainstorming |
| Утверждённый дизайн | writing-plans |
| Готовый план | subagent-driven-development |
| Написание кода | test-driven-development |
| Баг | systematic-debugging |
| Завершение | finishing-a-development-branch |

## Итоги

- В Superpowers ~14 навыков в 6 категориях
- Навыки активируются автоматически
- Каждый навык — это набор инструкций для агента
- Навыки не опциональны — это обязательные процессы
