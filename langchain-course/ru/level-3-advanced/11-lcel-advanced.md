---
title: "Продвинутый LCEL и пользовательские цепочки"
weight: 11
bookToc: true
---

# Продвинутый LCEL и пользовательские цепочки

## LCEL — глубокое погружение

LCEL — основа LangChain. Каждый компонент реализует интерфейс Runnable: `invoke`, `batch`, `stream`, `ainvoke`.

## RunnableLambda

Оберните любую функцию как шаг цепочки:

```python
from langchain_core.runnables import RunnableLambda

def uppercase(text: str) -> str:
    return text.upper()

chain = RunnableLambda(uppercase)
result = chain.invoke("привет")  # "ПРИВЕТ"
```

## Параллельное выполнение

```python
from langchain_core.runnables import RunnableParallel

parallel = RunnableParallel(
    summary=summary_chain,
    translation=translation_chain,
    keywords=keywords_chain,
)

result = parallel.invoke({"text": "LangChain — это здорово"})
```

## Ветвление с RunnableBranch

```python
from langchain_core.runnables import RunnableBranch

branch = RunnableBranch(
    (lambda x: "код" in x["topic"], code_chain),
    (lambda x: "математика" in x["topic"], math_chain),
    default_chain,
)
```

## Фоллбэки

```python
primary_llm = ChatOpenAI(model="gpt-4o")
fallback_llm = ChatOpenAI(model="gpt-4o-mini")

llm_with_fallback = primary_llm.with_fallbacks([fallback_llm])
```

## Повторные попытки

```python
chain_with_retry = chain.with_retry(
    stop_after_attempt=3,
    wait_exponential_jitter=True,
)
```

## Конфигурируемые цепочки

```python
from langchain_core.runnables import ConfigurableField

llm = ChatOpenAI(model="gpt-4o-mini").configurable_fields(
    model_name=ConfigurableField(id="model")
)

# По умолчанию
llm.invoke("Привет")

# Переопределить в рантайме
llm.with_config(configurable={"model": "gpt-4o"}).invoke("Привет")
```

## Далее

Изучим коллбэки и стриминг для приложений реального времени.
