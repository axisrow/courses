---
title: "Формат SKILL.md"
weight: 4
bookToc: true
---

# Формат SKILL.md

## Введение

`SKILL.md` — это главный файл любого навыка. Он содержит метаданные и инструкции для Claude.

## Структура файла

```markdown
---
name: my-skill-name
description: Описание навыка и когда его использовать
license: Complete terms in LICENSE.txt
---

# Название навыка

Инструкции, которым Claude будет следовать.

## Примеры
- Пример 1
- Пример 2

## Правила
- Правило 1
- Правило 2
```

## Frontmatter (метаданные)

Блок между `---` в начале файла. Обязательные поля:

| Поле | Описание |
|------|----------|
| `name` | Уникальный идентификатор (строчные буквы, дефисы) |
| `description` | Полное описание навыка и когда его использовать |

Необязательные поля:

| Поле | Описание |
|------|----------|
| `license` | Информация о лицензии |

## Тело документа (Markdown)

После frontmatter идёт обычный Markdown с инструкциями:

- **Заголовки** для структуры
- **Списки** для правил и примеров
- **Код** для технических инструкций
- **Таблицы** для справочных данных

## Пример: минимальный навык

```markdown
---
name: template-skill
description: Replace with description of the skill and when Claude should use it.
---

# Insert instructions below
```

## Пример: полный навык

```markdown
---
name: code-reviewer
description: Reviews code for best practices, security, and performance. Use when user asks to review code or check for issues.
---

# Code Reviewer

Review code following these principles:

## Process
1. Read the entire code first
2. Check for security issues
3. Check for performance problems
4. Suggest improvements

## Guidelines
- Be constructive, not critical
- Explain the "why" behind suggestions
- Provide code examples for fixes
```

## Итоги

- `SKILL.md` — обязательный файл каждого навыка
- Frontmatter содержит `name` и `description`
- Тело файла — Markdown-инструкции для Claude
- Чем конкретнее инструкции, тем лучше результат
