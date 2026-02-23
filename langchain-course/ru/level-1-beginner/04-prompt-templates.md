---
title: "Шаблоны промптов"
weight: 4
bookToc: true
---

# Шаблоны промптов

## Зачем нужны шаблоны?

Жёстко заданные промпты негибкие. Шаблоны позволяют создавать переиспользуемые промпты с переменными.

## Базовый шаблон

```python
from langchain_core.prompts import PromptTemplate

template = PromptTemplate.from_template(
    "Объясни {topic} простыми словами."
)

prompt = template.invoke({"topic": "квантовые вычисления"})
print(prompt.text)
```

## Шаблоны для чат-моделей

```python
from langchain_core.prompts import ChatPromptTemplate

template = ChatPromptTemplate.from_messages([
    ("system", "Ты эксперт в области {field}."),
    ("human", "{question}"),
])

messages = template.invoke({
    "field": "биология",
    "question": "Что такое ДНК?",
})
```

## Комбинация с моделями

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini")

template = ChatPromptTemplate.from_messages([
    ("system", "Ты переводчик. Переведи на {language}."),
    ("human", "{text}"),
])

# Используем LCEL
chain = template | llm

response = chain.invoke({
    "language": "французский",
    "text": "Привет, как дела?",
})
print(response.content)
```

## Few-shot промптинг

```python
from langchain_core.prompts import FewShotChatMessagePromptTemplate

examples = [
    {"input": "счастливый", "output": "грустный"},
    {"input": "высокий", "output": "низкий"},
]

example_prompt = ChatPromptTemplate.from_messages([
    ("human", "{input}"),
    ("ai", "{output}"),
])

few_shot = FewShotChatMessagePromptTemplate(
    example_prompt=example_prompt,
    examples=examples,
)

final = ChatPromptTemplate.from_messages([
    ("system", "Дай антоним для каждого слова."),
    few_shot,
    ("human", "{input}"),
])
```

## Далее

Теперь, когда вы умеете создавать промпты, научимся строить цепочки.
