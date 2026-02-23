---
title: "Коллбэки и стриминг"
weight: 12
bookToc: true
---

# Коллбэки и стриминг

## Потоковый вывод

Стриминг показывает ответ токен за токеном — важно для хорошего UX.

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini")

for chunk in llm.stream("Расскажи историю"):
    print(chunk.content, end="", flush=True)
```

## Стриминг цепочек

```python
chain = prompt | llm | StrOutputParser()

for chunk in chain.stream({"topic": "космос"}):
    print(chunk, end="", flush=True)
```

## Асинхронный стриминг

```python
import asyncio

async def main():
    async for chunk in chain.astream({"topic": "космос"}):
        print(chunk, end="", flush=True)

asyncio.run(main())
```

## События потока

```python
async for event in chain.astream_events(
    {"topic": "космос"}, version="v2"
):
    kind = event["event"]
    if kind == "on_chat_model_stream":
        print(event["data"]["chunk"].content, end="")
    elif kind == "on_chain_start":
        print(f"\nЗапуск: {event['name']}")
```

## Коллбэки

Коллбэки позволяют встраиваться в выполнение цепочки:

```python
from langchain_core.callbacks import BaseCallbackHandler

class MyHandler(BaseCallbackHandler):
    def on_llm_start(self, serialized, prompts, **kwargs):
        print(f"LLM запущен с {len(prompts)} промптами")

    def on_llm_end(self, response, **kwargs):
        print("LLM завершён")

    def on_llm_error(self, error, **kwargs):
        print(f"Ошибка LLM: {error}")

llm = ChatOpenAI(model="gpt-4o-mini", callbacks=[MyHandler()])
```

## Подсчёт токенов

```python
from langchain_community.callbacks import get_openai_callback

with get_openai_callback() as cb:
    result = chain.invoke({"topic": "ИИ"})
    print(f"Использовано токенов: {cb.total_tokens}")
    print(f"Стоимость: ${cb.total_cost:.4f}")
```

## Далее

Следующий урок — оценка и тестирование LLM-приложений.
