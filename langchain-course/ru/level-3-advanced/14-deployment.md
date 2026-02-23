---
title: "Развёртывание и продакшен"
weight: 14
bookToc: true
---

# Развёртывание и продакшен

## LangServe — развёртывание как API

LangServe превращает любую цепочку в REST API:

```bash
pip install langserve[all] fastapi uvicorn
```

```python
from fastapi import FastAPI
from langserve import add_routes
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate

app = FastAPI(title="Мой LangChain API")

prompt = ChatPromptTemplate.from_template("Расскажи о {topic}")
llm = ChatOpenAI(model="gpt-4o-mini")
chain = prompt | llm

add_routes(app, chain, path="/chat")

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)
```

## Docker

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

## Чеклист для продакшена

- ✅ Переменные окружения для API-ключей
- ✅ Ограничение частоты запросов
- ✅ Логирование и трассировка (LangSmith)
- ✅ Обработка ошибок и фоллбэки
- ✅ Кэширование повторных запросов
- ✅ Мониторинг использования токенов
- ✅ Аутентификация API

## Кэширование

```python
from langchain_core.globals import set_llm_cache
from langchain_community.cache import SQLiteCache

set_llm_cache(SQLiteCache(database_path="cache.db"))
```

## Ограничение частоты запросов

```python
from langchain_core.rate_limiters import InMemoryRateLimiter

limiter = InMemoryRateLimiter(requests_per_second=1)
llm = ChatOpenAI(model="gpt-4o-mini", rate_limiter=limiter)
```

## Платформы для развёртывания

| Платформа | Особенности |
|-----------|------------|
| AWS Lambda | Бессерверная, для малого трафика |
| Google Cloud Run | Контейнеры, автомасштабирование |
| Azure Container Apps | Интеграция с Azure OpenAI |
| Railway / Render | Простое развёртывание из Git |
| LangGraph Cloud | Управляемый хостинг для LangGraph |

## Далее

В последнем уроке изучим мультиагентные системы с LangGraph.
