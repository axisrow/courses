---
title: "Frontmatter и metadata"
weight: 2
bookToc: true
---

# Frontmatter и metadata

## Введение

Frontmatter — это YAML-блок в начале `SKILL.md`, определяющий метаданные навыка. От качества метаданных зависит, когда и как Claude активирует навык.

## Обязательные поля

### name

Уникальный идентификатор навыка:

```yaml
name: my-skill-name
```

Правила:
- Только строчные буквы и дефисы
- Без пробелов и спецсимволов
- Должен быть уникальным

### description

Описание навыка — **самое важное поле**:

```yaml
description: >
  Guide for creating high-quality MCP servers that enable LLMs 
  to interact with external services. Use when building MCP servers 
  to integrate external APIs or services.
```

Хорошее описание содержит:
1. Что делает навык
2. Когда его использовать (триггеры)
3. Ключевые слова для активации

## Необязательные поля

### license

```yaml
license: Complete terms in LICENSE.txt
```

## Примеры хороших описаний

❌ Плохо:
```yaml
description: Helps with code
```

✅ Хорошо:
```yaml
description: >
  Reviews Python code for security vulnerabilities, performance issues,
  and PEP 8 compliance. Use when user asks to review code, audit 
  code quality, or check for security issues in Python projects.
```

## Итоги

- Frontmatter определяет, когда Claude активирует навык
- `name` — уникальный ID навыка
- `description` — ключевое поле для правильной активации
- Описание должно содержать триггеры и ключевые слова
