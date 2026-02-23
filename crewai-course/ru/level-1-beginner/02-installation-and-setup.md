---
title: "Установка и настройка"
weight: 2
bookToc: true
---

# Установка и настройка

## Требования

- Python 3.10 или выше
- API-ключ OpenAI (или другого провайдера LLM)
- Пакетный менеджер pip или uv

## Установка CrewAI

```bash
pip install crewai
```

С встроенными инструментами:

```bash
pip install 'crewai[tools]'
```

## CLI-инструмент

CrewAI имеет командную строку для создания проектов:

```bash
crewai create crew my_project
```

Это создаёт структуру папок с шаблонами для агентов, задач и конфигурации.

## Настройка API-ключа

```bash
export OPENAI_API_KEY="sk-your-key-here"
```

Или добавьте в файл `.env`:

```
OPENAI_API_KEY=sk-your-key-here
```

## Проверка установки

```python
import crewai
print(crewai.__version__)
```

## Структура проекта

```
my_project/
├── src/
│   └── my_project/
│       ├── config/
│       │   ├── agents.yaml
│       │   └── tasks.yaml
│       ├── crew.py
│       └── main.py
├── pyproject.toml
└── README.md
```

- `agents.yaml` — определение агентов
- `tasks.yaml` — определение задач
- `crew.py` — сборка команды
- `main.py` — точка входа

## Итого

Установите CrewAI через pip, настройте API-ключ и используйте CLI для создания проекта. Теперь вы готовы создавать агентов.

---

**Далее:** Агенты — подробный разбор.
