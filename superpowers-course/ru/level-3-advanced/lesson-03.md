---
title: "Advanced Workflows"
level: 3
lesson: 3
lang: ru
---

# Advanced Workflows

## Введение

Сложные рабочие процессы: параллельные агенты, code review, git worktrees.

## Git Worktrees

Навык `using-git-worktrees` создаёт изолированные рабочие пространства:

```bash
# Superpowers автоматически создаёт worktree
git worktree add ../project-feature-x feature-x
```

Преимущества:
- Основная ветка не затронута
- Можно работать над несколькими фичами параллельно
- Чистый базовый набор тестов гарантирован

## Параллельные агенты

`dispatching-parallel-agents` позволяет:

1. Определить независимые задачи
2. Запустить субагента на каждую
3. Собрать результаты
4. Проверить совместимость

## Code Review Workflow

Двухэтапный процесс:

### Этап 1: requesting-code-review
- Чеклист перед review
- Автоматическая проверка тестов
- Линтинг и форматирование

### Этап 2: receiving-code-review
- Обработка фидбека
- Классификация по серьёзности
- Критические блокируют прогресс

## Finishing Workflow

`finishing-a-development-branch`:
1. Все тесты проходят
2. Выбор: merge / PR / сохранить / отменить
3. Очистка worktree

## Комбинирование workflow

```
Brainstorm → Worktree → Plan → 
[Parallel agents for tasks 1-3] → 
Code Review → Fix issues → 
[Parallel agents for tasks 4-6] → 
Final Review → Merge
```

## Итоги

- Git worktrees обеспечивают изоляцию
- Параллельные агенты ускоряют работу
- Code review — обязательный этап
- Workflow можно комбинировать гибко
