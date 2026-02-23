---
title: "Создание первого Workflow"
weight: 1
bookToc: true
---

# Создание первого Workflow

## Использование Ali

Ali — встроенный конструктор workflow. Он проведёт вас через этапы:

1. **Настройка** — опишите проект
2. **Мозговой штурм** — определите цели
3. **Определение workflow** — структурируйте шаги
4. **Агенты** — настройте AI-работников
5. **Промпты** — напишите инструкции
6. **Генерация** — создайте финальные файлы

## Ручное создание

Вам нужно три вещи:

### 1. Конфигурация агентов (`config/main.agents.js`)

```javascript
export default [
  {
    id: 'researcher',
    name: 'Research Agent',
    description: 'Собирает информацию',
    promptPath: '.codemachine/prompts/research.md',
  },
  {
    id: 'implementer',
    name: 'Implementation Agent',
    description: 'Пишет код',
    promptPath: '.codemachine/prompts/implement.md',
  },
];
```

### 2. Файлы промптов

```markdown
---
name: 'Фаза исследования'
description: 'Сбор требований и контекста'
---

# Фаза исследования

## ЦЕЛЬ ШАГА:
Понять, что нужно построить, изучив кодовую базу и требования.

## Последовательность инструкций
### 1. Прочитать спецификацию проекта
### 2. Изучить существующий код
### 3. Подготовить резюме для следующего шага
```

### 3. Файл workflow

```javascript
export default {
  name: 'My First Workflow',
  steps: [
    resolveStep('researcher'),
    resolveStep('implementer'),
  ],
};
```

## Запуск

```bash
codemachine
```

Выберите workflow из списка — CodeMachine начнёт выполнение.

## Итог

- Используйте Ali для пошагового создания
- Или создайте файлы конфигурации, промптов и workflow вручную
- Запускайте командой `codemachine`

> **Следующий урок:** Написание эффективных промптов.
