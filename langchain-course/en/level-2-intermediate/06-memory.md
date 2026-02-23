---
title: "Memory and Conversation"
weight: 6
bookToc: true
---

# Memory and Conversation

## Why Memory?

By default, LLMs are stateless — each call is independent. Memory lets your app remember previous messages.

## Chat Message History

```python
from langchain_core.chat_history import InMemoryChatMessageHistory

history = InMemoryChatMessageHistory()
history.add_user_message("My name is Alice")
history.add_ai_message("Hello Alice!")
history.add_user_message("What is my name?")

print(history.messages)
```

## RunnableWithMessageHistory

```python
from langchain_core.runnables.history import RunnableWithMessageHistory
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate, MessagesPlaceholder

prompt = ChatPromptTemplate.from_messages([
    ("system", "You are a helpful assistant."),
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

# First message
response = with_history.invoke(
    {"input": "My name is Bob"},
    config={"configurable": {"session_id": "user-1"}},
)

# Second message — it remembers!
response = with_history.invoke(
    {"input": "What is my name?"},
    config={"configurable": {"session_id": "user-1"}},
)
print(response.content)  # "Your name is Bob"
```

## Trimming Messages

Long conversations use many tokens. Trim old messages:

```python
from langchain_core.messages import trim_messages

trimmed = trim_messages(
    history.messages,
    max_tokens=100,
    token_counter=llm,
    strategy="last",
)
```

## Persistent Storage

For production, use a database:

```python
# pip install langchain-redis
from langchain_redis import RedisChatMessageHistory

history = RedisChatMessageHistory(
    session_id="user-1",
    redis_url="redis://localhost:6379",
)
```

## Next Steps

Next, we will learn how to load and process documents.
