---
title: "Оценка и тестирование"
weight: 13
bookToc: true
---

# Оценка и тестирование

## Зачем оценивать?

Ответы LLM недетерминированны. Нужна систематическая оценка для обеспечения качества.

## LangSmith для оценки

LangSmith — платформа LangChain для трассировки, тестирования и мониторинга.

```bash
pip install langsmith
export LANGSMITH_API_KEY="ваш-ключ"
export LANGSMITH_TRACING=true
```

## Создание тестовых наборов

```python
from langsmith import Client

client = Client()
dataset = client.create_dataset("my-qa-test")

client.create_examples(
    inputs=[
        {"question": "Кто создал LangChain?"},
        {"question": "На каком языке написан LangChain?"},
    ],
    outputs=[
        {"answer": "Харрисон Чейз"},
        {"answer": "Python и JavaScript"},
    ],
    dataset_id=dataset.id,
)
```

## Запуск оценки

```python
from langsmith.evaluation import evaluate

def predict(inputs):
    return {"answer": rag_chain.invoke(inputs["question"])}

results = evaluate(predict, data="my-qa-test", evaluators=["qa"])
```

## Пользовательские оценщики

```python
from langsmith.schemas import Example, Run

def check_length(run: Run, example: Example) -> dict:
    prediction = run.outputs["answer"]
    return {
        "key": "short_enough",
        "score": len(prediction) < 500,
    }

results = evaluate(predict, data="my-qa-test", evaluators=[check_length])
```

## Юнит-тестирование

```python
import pytest

def test_rag_chain():
    result = rag_chain.invoke("Кто создал LangChain?")
    assert "Харрисон Чейз" in result

def test_chain_returns_string():
    result = chain.invoke({"topic": "ИИ"})
    assert isinstance(result, str)
    assert len(result) > 0
```

## Советы по тестированию

- Тестируйте с разнообразными входными данными
- Используйте `temperature=0` для тестов
- Отслеживайте метрики во времени
- Сравнивайте разные промпты и модели

## Далее

Научимся развёртывать LangChain-приложения в продакшен.
