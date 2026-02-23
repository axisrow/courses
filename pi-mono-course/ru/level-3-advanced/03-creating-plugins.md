---
title: "Создание плагинов"
weight: 3
bookToc: true
---

# Создание плагинов

## Введение

Pi поддерживает расширение через Extensions, Skills, Prompt Templates и Themes. Вы можете упаковать их в Pi Packages и делиться через npm.

## Расширения (Extensions)

Расширения добавляют новые инструменты агенту. Создайте файл в `.pi/extensions/`:

```typescript
// .pi/extensions/time.ts
import { Type } from '@mariozechner/pi-ai';

export default {
  name: 'current_time',
  description: 'Возвращает текущее время',
  parameters: Type.Object({}),
  execute: async () => {
    return new Date().toISOString();
  },
};
```

## Навыки (Skills)

Навыки — текстовые файлы с инструкциями:

```bash
mkdir -p .pi/skills
cat > .pi/skills/git.md << 'EOF'
При работе с Git:
- Всегда создавай feature-ветки
- Пиши осмысленные commit messages
- Используй conventional commits
EOF
```

## Шаблоны промптов (Prompt Templates)

Кастомные системные промпты для разных задач:

```bash
cat > .pi/prompts/reviewer.md << 'EOF'
Ты — ревьюер кода. Анализируй код на:
- Безопасность
- Производительность
- Читаемость
EOF
```

## Pi Packages

Упакуйте расширения в npm-пакет:

```json
{
  "name": "my-pi-package",
  "pi": {
    "extensions": ["./extensions/"],
    "skills": ["./skills/"],
    "prompts": ["./prompts/"]
  }
}
```

## Итоги

- Extensions добавляют инструменты
- Skills задают инструкции
- Prompt Templates определяют поведение
- Pi Packages — способ делиться всем этим
