---
title: "Агенты и инструменты"
weight: 10
bookToc: true
---

# Агенты и инструменты

## Что такое агент?

Агент — это LLM, который сам решает, какие действия выполнять. Вместо фиксированной цепочки он рассуждает, какой инструмент использовать.

## Определение инструментов

```python
from langchain_core.tools import tool

@tool
def multiply(a: int, b: int) -> int:
    """Умножить два числа."""
    return a * b

@tool
def add(a: int, b: int) -> int:
    """Сложить два числа."""
    return a + b

tools = [multiply, add]
```

## Встроенные инструменты

```python
from langchain_community.tools import DuckDuckGoSearchRun

search = DuckDuckGoSearchRun()
result = search.invoke("LangChain последняя версия")
```

## Создание агента

```python
from langchain_openai import ChatOpenAI
from langgraph.prebuilt import create_react_agent

llm = ChatOpenAI(model="gpt-4o-mini")
agent = create_react_agent(llm, tools)

result = agent.invoke(
    {"messages": [{"role": "user", "content": "Сколько будет 15 * 37?"}]}
)
print(result["messages"][-1].content)
```

## Как работают агенты

1. LLM получает вопрос и описания инструментов
2. LLM решает вызвать инструмент (или ответить напрямую)
3. Инструмент выполняется и возвращает результат
4. LLM видит результат и решает, что делать дальше
5. Повторяет, пока не получит финальный ответ

## Агент с памятью

```python
from langgraph.checkpoint.memory import MemorySaver

memory = MemorySaver()
agent = create_react_agent(llm, tools, checkpointer=memory)

config = {"configurable": {"thread_id": "user-1"}}

agent.invoke(
    {"messages": [{"role": "user", "content": "Меня зовут Алиса"}]},
    config=config,
)

result = agent.invoke(
    {"messages": [{"role": "user", "content": "Как меня зовут?"}]},
    config=config,
)
```

## Итоги уровня 2

Вы теперь умеете:
- Добавлять память в диалоги
- Загружать и разделять документы
- Использовать векторные хранилища
- Строить RAG-пайплайны
- Создавать агентов с инструментами

Следующий уровень: продвинутые темы.
