---
title: "Установка навыков"
weight: 5
bookToc: true
---

# Установка навыков

## Введение

Рассмотрим пошаговую установку навыков из репозитория Anthropic и пользовательских навыков.

## Установка из репозитория Anthropic

### Шаг 1: Клонирование репозитория

```bash
git clone https://github.com/anthropics/skills.git
cd skills
```

### Шаг 2: Изучение структуры

```
skills/
├── skills/           # Все навыки
│   ├── algorithmic-art/
│   ├── docx/
│   ├── pdf/
│   └── ...
├── spec/             # Спецификация
└── template/         # Шаблон
```

### Шаг 3: Установка в Claude Code

```bash
# Добавить маркетплейс
/plugin marketplace add anthropics/skills

# Установить набор навыков
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

## Установка пользовательского навыка

### Шаг 1: Создайте папку навыка

```bash
mkdir my-skill
```

### Шаг 2: Создайте SKILL.md

```bash
cat > my-skill/SKILL.md << 'EOF'
---
name: my-skill
description: My custom skill description
---

# My Skill Instructions
EOF
```

### Шаг 3: Подключите в Claude

- **Claude Code**: поместите в директорию проекта
- **Claude.ai**: загрузите через настройки проекта
- **API**: передайте содержимое как часть запроса

## Проверка установки

После установки попробуйте дать Claude задачу, связанную с навыком. Если навык подключён правильно, Claude будет следовать инструкциям из `SKILL.md`.

## Итоги

- Навыки устанавливаются через Claude Code (`/plugin`) или вручную
- Репозиторий Anthropic содержит готовые наборы навыков
- Пользовательские навыки создаются из папки с `SKILL.md`
- После установки навыки активируются автоматически
