---
title: "Настройка окружения"
weight: 2
bookToc: true
---

# Настройка окружения

## Требования

- Python 3.9 или выше
- Терминал или командная строка
- API-ключ от OpenAI (или другого провайдера LLM)

## Установка Python

Проверьте версию:

```bash
python --version
```

## Создание виртуального окружения

```bash
python -m venv langchain-env
source langchain-env/bin/activate  # Linux/macOS
# langchain-env\Scripts\activate   # Windows
```

## Установка LangChain

```bash
pip install langchain langchain-openai
```

## Настройка API-ключа

Создайте файл `.env`:

```
OPENAI_API_KEY=sk-ваш-ключ
```

Загрузите в Python:

```python
from dotenv import load_dotenv
load_dotenv()
```

## Проверка установки

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini")
response = llm.invoke("Привет!")
print(response.content)
```

Если вы видите ответ — всё работает.

## Структура проекта

```
my-langchain-project/
├── .env
├── requirements.txt
└── main.py
```

## Далее

Теперь, когда окружение готово, научимся работать с LLM в LangChain.
