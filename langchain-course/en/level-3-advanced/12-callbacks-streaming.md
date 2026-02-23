---
title: "Callbacks and Streaming"
weight: 12
bookToc: true
---

# Callbacks and Streaming

## Streaming Responses

Streaming shows output token by token — essential for good UX.

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini")

for chunk in llm.stream("Tell me a story"):
    print(chunk.content, end="", flush=True)
```

## Streaming Full Chains

```python
chain = prompt | llm | StrOutputParser()

for chunk in chain.stream({"topic": "space"}):
    print(chunk, end="", flush=True)
```

## Async Streaming

```python
import asyncio

async def main():
    async for chunk in chain.astream({"topic": "space"}):
        print(chunk, end="", flush=True)

asyncio.run(main())
```

## Stream Events

Get detailed events from every step:

```python
async for event in chain.astream_events(
    {"topic": "space"}, version="v2"
):
    kind = event["event"]
    if kind == "on_chat_model_stream":
        print(event["data"]["chunk"].content, end="")
    elif kind == "on_chain_start":
        print(f"\nStarted: {event['name']}")
```

## Callbacks

Callbacks let you hook into chain execution:

```python
from langchain_core.callbacks import BaseCallbackHandler

class MyHandler(BaseCallbackHandler):
    def on_llm_start(self, serialized, prompts, **kwargs):
        print(f"LLM started with {len(prompts)} prompts")

    def on_llm_end(self, response, **kwargs):
        print(f"LLM finished")

    def on_llm_error(self, error, **kwargs):
        print(f"LLM error: {error}")

llm = ChatOpenAI(model="gpt-4o-mini", callbacks=[MyHandler()])
```

## Token Counting

```python
from langchain_community.callbacks import get_openai_callback

with get_openai_callback() as cb:
    result = chain.invoke({"topic": "AI"})
    print(f"Tokens used: {cb.total_tokens}")
    print(f"Cost: ${cb.total_cost:.4f}")
```

## Next Steps

Next, we will learn how to evaluate and test LLM applications.
