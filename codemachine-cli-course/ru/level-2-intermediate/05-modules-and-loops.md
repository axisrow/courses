---
title: "Модули и циклы"
weight: 5
bookToc: true
---

# Модули и циклы

## Что такое модуль?

Модуль — это шаг, который может повторяться. Идеален для итеративных задач.

## Настройка модуля

```javascript
// config/modules.js
export default [
  {
    id: 'quality-check',
    name: 'Quality Checker',
    promptPath: 'prompts/quality-check.md',
    behavior: {
      type: 'loop',
      action: 'stepBack',
    },
  },
];
```

## Использование в workflow

```javascript
steps: [
  resolveStep('planner'),
  resolveStep('coder'),
  resolveModule('quality-check', {
    loopSteps: 2,
    loopMaxIterations: 10,
    loopSkip: ['planner'],
  }),
],
```

### Как это работает

```
Шаг 1: План → Шаг 2: Код → Шаг 3: Проверка
                 ↑                    ↓
                 └──── Назад ─────────┘
                   (если есть проблемы)
```

## Опция executeOnce

```javascript
resolveStep('initial-setup', {
  executeOnce: true,  // Не повторится при перезапуске
}),
```

## Папки — группировка шагов

```javascript
...resolveFolder('preparation'),

...resolveFolder('implementation', {
  engine: 'codex',
  model: 'gpt-5',
}),
```

## Итог

- Модули — шаги с возможностью цикла
- `loopSteps`, `loopMaxIterations`, `loopSkip` управляют циклами
- `executeOnce` для одноразовых шагов
- `resolveFolder` загружает группы шагов

> **Поздравляем!** Уровень 2 пройден. В Уровне 3 — продвинутые паттерны.
