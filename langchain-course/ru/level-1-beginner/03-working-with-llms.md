---
title: "Работа с LLM"
weight: 3
bookToc: true
---

# Работа с LLM

## Чат-модели vs LLM

LangChain поддерживает два типа моделей:

- **Чат-модели** — работают с сообщениями (рекомендуется). Примеры: GPT-4, Claude.
- **LLM** — работают с текстовыми строками. Устаревший подход.

## Использование чат-модели

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini", temperature=0.7)
response = llm.invoke("Что такое LangChain?")
print(response.content)
```

## Типы сообщений

```python
from langchain_core.messages import SystemMessage, HumanMessage

messages = [
    SystemMessage(content="Ты полезный ассистент."),
    HumanMessage(content="Что такое Python?"),
]

response = llm.invoke(messages)
print(response.content)
```

| Тип сообщения | Назначение |
|--------------|-----------|
| `SystemMessage` | Задаёт поведение и контекст |
| `HumanMessage` | Ввод пользователя |
| `AIMessage` | Ответ модели |

## Параметры модели

```python
llm = ChatOpenAI(
    model="gpt-4o-mini",
    temperature=0.0,   # 0 = детерминированный, 1 = креативный
    max_tokens=500,     # Максимальная длина ответа
)
```

## Другие провайдеры

```python
# Anthropic
from langchain_anthropic import ChatAnthropic
llm = ChatAnthropic(model="claude-sonnet-4-20250514")

# Google
from langchain_google_genai import ChatGoogleGenerativeAI
llm = ChatGoogleGenerativeAI(model="gemini-pro")
```

## Пакетная обработка и стриминг

```python
# Обработка нескольких запросов
results = llm.batch(["Привет", "Как дела?"])

# Потоковый вывод
for chunk in llm.stream("Расскажи историю"):
    print(chunk.content, end="")
```

## Далее

Дальше мы узнаем о шаблонах промптов — мощном способе структурировать запросы.
