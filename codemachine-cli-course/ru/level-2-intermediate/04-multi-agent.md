---
title: "Мультиагентная оркестрация"
weight: 4
bookToc: true
---

# Мультиагентная оркестрация

## Зачем несколько агентов?

Как команда специалистов работает лучше одного универсала, несколько AI-агентов справляются со сложными задачами эффективнее.

## Суб-агенты

Суб-агенты работают параллельно с основными:

```javascript
// config/sub.agents.js
export default [
  {
    id: 'frontend-dev',
    name: 'Frontend Developer',
    mirrorPath: 'prompts/frontend-mirror.md',
  },
  {
    id: 'backend-dev',
    name: 'Backend Developer',
    mirrorPath: 'prompts/backend-mirror.md',
  },
];
```

### Использование в workflow

```javascript
export default {
  name: 'Full Stack Builder',
  steps: [
    resolveStep('architect'),
    resolveStep('implementation'),
  ],
  subAgentIds: ['frontend-dev', 'backend-dev'],
};
```

## Параллельное выполнение

```
Основной агент (Архитектор)
    ├── Суб-агент: Frontend  ──→ Строит UI
    └── Суб-агент: Backend   ──→ Строит API
```

## Контроллер

Контроллер наблюдает за workflow и принимает решения:

```javascript
export default {
  name: 'Managed Workflow',
  controller: controller('project-manager', {
    engine: 'claude',
  }),
  steps: [...],
};
```

## Комбинирование движков

```javascript
resolveStep('planning', { engine: 'claude' }),    // Анализ
resolveStep('coding', { engine: 'codex' }),       // Код
resolveStep('review', { engine: 'claude' }),      // Ревью
```

## Итог

- Суб-агенты для параллельной работы
- Контроллеры для надзора и решений
- Комбинируйте движки по задачам
- Параллельность экономит время

> **Следующий урок:** Модули и циклы.
