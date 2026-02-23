---
title: "Working with LLMs"
weight: 3
bookToc: true
---

# Working with LLMs

## Chat Models vs LLMs

LangChain supports two types of models:

- **Chat Models** — Work with messages (recommended). Examples: GPT-4, Claude.
- **LLMs** — Work with plain text strings. Older style.

Most modern applications use chat models.

## Using a Chat Model

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini", temperature=0.7)
response = llm.invoke("What is LangChain?")
print(response.content)
```

## Message Types

Chat models work with messages:

```python
from langchain_core.messages import SystemMessage, HumanMessage

messages = [
    SystemMessage(content="You are a helpful assistant."),
    HumanMessage(content="What is Python?"),
]

response = llm.invoke(messages)
print(response.content)
```

| Message Type | Purpose |
|-------------|---------|
| `SystemMessage` | Sets behavior and context |
| `HumanMessage` | User input |
| `AIMessage` | Model response |

## Model Parameters

```python
llm = ChatOpenAI(
    model="gpt-4o-mini",
    temperature=0.0,   # 0 = deterministic, 1 = creative
    max_tokens=500,     # Maximum response length
)
```

## Using Other Providers

```python
# Anthropic
from langchain_anthropic import ChatAnthropic
llm = ChatAnthropic(model="claude-sonnet-4-20250514")

# Google
from langchain_google_genai import ChatGoogleGenerativeAI
llm = ChatGoogleGenerativeAI(model="gemini-pro")
```

## Batch and Stream

```python
# Process multiple inputs
results = llm.batch(["Hello", "How are you?"])

# Stream responses
for chunk in llm.stream("Tell me a story"):
    print(chunk.content, end="")
```

## Next Steps

Next, we will learn about prompt templates — a powerful way to structure your inputs.
