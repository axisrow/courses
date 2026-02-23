---
title: "Использование Skills в Claude Code, Claude.ai и API"
weight: 2
bookToc: true
---

# Использование Skills

## Введение

Skills можно использовать тремя способами: в Claude Code (CLI), в веб-интерфейсе Claude.ai и через API. Каждый способ имеет свои особенности.

## Claude Code

Claude Code — это CLI-инструмент от Anthropic. Для работы с навыками:

### Добавление маркетплейса

```bash
/plugin marketplace add anthropics/skills
```

### Установка навыка

1. Выберите `Browse and install plugins`
2. Выберите `anthropic-agent-skills`
3. Выберите нужный набор (`document-skills` или `example-skills`)
4. Нажмите `Install now`

### Быстрая установка

```bash
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

### Использование

После установки просто упомяните навык в запросе:

> «Используй навык PDF, чтобы извлечь поля формы из файла report.pdf»

## Claude.ai

В веб-интерфейсе Claude.ai навыки уже доступны для платных планов. Для загрузки пользовательских навыков:

1. Откройте настройки проекта
2. Перейдите в раздел навыков
3. Загрузите папку с навыком

## Claude API

Навыки доступны через API. Пример:

```python
import anthropic

client = anthropic.Anthropic()

# Навыки подключаются как часть системного промпта
# или через специальный параметр skills
```

Подробнее: [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide)

## Итоги

- Claude Code: установка через `/plugin` команды
- Claude.ai: навыки встроены для платных планов
- API: подключение через параметры запроса
- Во всех случаях навыки активируются автоматически при упоминании задачи
