---
title: "Advanced LCEL and Custom Chains"
weight: 11
bookToc: true
---

# Advanced LCEL and Custom Chains

## LCEL Deep Dive

LCEL (LangChain Expression Language) is the backbone of LangChain. Every component implements the Runnable interface: `invoke`, `batch`, `stream`, `ainvoke`.

## RunnableLambda

Wrap any function as a chain step:

```python
from langchain_core.runnables import RunnableLambda

def uppercase(text: str) -> str:
    return text.upper()

chain = RunnableLambda(uppercase)
result = chain.invoke("hello")  # "HELLO"
```

## Parallel Execution

```python
from langchain_core.runnables import RunnableParallel

parallel = RunnableParallel(
    summary=summary_chain,
    translation=translation_chain,
    keywords=keywords_chain,
)

result = parallel.invoke({"text": "LangChain is great"})
# result["summary"], result["translation"], result["keywords"]
```

## Branching with RunnableBranch

```python
from langchain_core.runnables import RunnableBranch

branch = RunnableBranch(
    (lambda x: "code" in x["topic"], code_chain),
    (lambda x: "math" in x["topic"], math_chain),
    default_chain,
)
```

## Fallbacks

```python
primary_llm = ChatOpenAI(model="gpt-4o")
fallback_llm = ChatOpenAI(model="gpt-4o-mini")

llm_with_fallback = primary_llm.with_fallbacks([fallback_llm])
```

## Custom Runnables

```python
from langchain_core.runnables import Runnable

class MyRunnable(Runnable):
    def invoke(self, input, config=None):
        # Your custom logic
        return {"result": process(input)}
```

## Retry Logic

```python
chain_with_retry = chain.with_retry(
    stop_after_attempt=3,
    wait_exponential_jitter=True,
)
```

## Configurable Chains

```python
from langchain_core.runnables import ConfigurableField

llm = ChatOpenAI(model="gpt-4o-mini").configurable_fields(
    model_name=ConfigurableField(id="model")
)

# Use default
llm.invoke("Hello")

# Override at runtime
llm.with_config(configurable={"model": "gpt-4o"}).invoke("Hello")
```

## Next Steps

Let's learn about callbacks and streaming for real-time applications.
