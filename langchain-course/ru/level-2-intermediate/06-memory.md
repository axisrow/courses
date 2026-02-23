---
title: "Память и диалоги"
weight: 6
bookToc: true
---

# Память и диалоги

## Зачем нужна память?

По умолчанию LLM не имеют состояния — каждый вызов независим. Память позволяет приложению помнить предыдущие сообщения.

## История сообщений

```python
from langchain_core.chat_history import InMemoryChatMessageHistory

history = InMemoryChatMessageHistory()
history.add_user_message("Меня зовут Алиса")
history.add_ai_message("Привет, Алиса!")
history.add_user_message("Как меня зовут?")
```

## RunnableWithMessageHistory

```python
from langchain_core.runnables.history import RunnableWithMessageHistory
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder

prompt = ChatPromptTemplate.from_messages([
    ("system", "Ты полезный ассистент."),
    MessagesPlaceholder(variable_name="history"),
    ("human", "{input}"),
])

llm = ChatOpenAI(model="gpt-4o-mini")
chain = prompt | llm

store = {}

def get_session_history(session_id):
    if session_id not in store:
        store[session_id] = InMemoryChatMessageHistory()
    return store[session_id]

with_history = RunnableWithMessageHistory(
    chain,
    get_session_history,
    input_messages_key="input",
    history_messages_key="history",
)

# Первое сообщение
response = with_history.invoke(
    {"input": "Меня зовут Боб"},
    config={"configurable": {"session_id": "user-1"}},
)

# Второе — помнит!
response = with_history.invoke(
    {"input": "Как меня зовут?"},
    config={"configurable": {"session_id": "user-1"}},
)
print(response.content)  # "Вас зовут Боб"
```

## Обрезка сообщений

```python
from langchain_core.messages import trim_messages

trimmed = trim_messages(
    history.messages,
    max_tokens=100,
    token_counter=llm,
    strategy="last",
)
```

## Постоянное хранение

Для продакшена используйте базу данных:

```python
from langchain_redis import RedisChatMessageHistory

history = RedisChatMessageHistory(
    session_id="user-1",
    redis_url="redis://localhost:6379",
)
```

## Далее

Следующий урок — загрузка и обработка документов.
