---
title: "Лучшие практики"
weight: 5
bookToc: true
---

# Лучшие практики

## Введение

Рекомендации от Anthropic и сообщества по созданию эффективных навыков.

## Описание (description)

### Будьте конкретны

```yaml
# ❌ Плохо
description: Helps write stuff

# ✅ Хорошо  
description: >
  Creates structured technical documentation including API references,
  architecture diagrams, and deployment guides. Use when user needs 
  to write or update technical docs, README files, or API documentation.
```

### Включайте триггеры

Перечислите ключевые слова и ситуации активации прямо в описании.

## Инструкции

### Структурируйте процесс

Разбейте работу на пронумерованные шаги:

```markdown
## Process
1. First, analyze the input
2. Then, identify key patterns
3. Generate output following the template
4. Validate against guidelines
```

### Давайте примеры

Примеры «вход → выход» самый эффективный способ обучить Claude:

```markdown
## Example
Input: "Quick brown fox"
Output: 
- Words: 3
- Characters: 15
- Readability: Simple
```

### Устанавливайте ограничения

```markdown
## Guidelines
- Never expose API keys in output
- Limit response to 500 words
- Always include source references
```

## Структура папки

```
my-skill/
├── SKILL.md              # Обязательно
├── scripts/              # Для сложной логики
├── examples/             # Образцы входов/выходов
├── reference/            # Справочные материалы
└── LICENSE.txt           # Лицензия
```

## Пять правил хорошего навыка

1. **Одна задача** — навык решает одну задачу хорошо
2. **Конкретные инструкции** — без двусмысленности
3. **Примеры** — покажите ожидаемый результат
4. **Тестирование** — проверяйте с разными входами
5. **Итерации** — улучшайте на основе результатов

## Итоги

- Хорошее описание = правильная активация
- Структурированные инструкции с примерами — ключ к качеству
- Один навык = одна задача
- Тестируйте и улучшайте итеративно
