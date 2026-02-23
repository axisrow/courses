---
title: "Простые цепочки"
weight: 5
bookToc: true
---

# Простые цепочки

## Что такое цепочка?

Цепочка соединяет несколько шагов: сформировать промпт → отправить в LLM → обработать результат.

## LCEL — LangChain Expression Language

LCEL использует оператор `|` для соединения компонентов:

```python
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser

prompt = ChatPromptTemplate.from_template("Расскажи шутку про {topic}")
llm = ChatOpenAI(model="gpt-4o-mini")
parser = StrOutputParser()

chain = prompt | llm | parser

result = chain.invoke({"topic": "программирование"})
print(result)  # Строка, а не AIMessage
```

## Парсеры вывода

```python
from langchain_core.output_parsers import JsonOutputParser

parser = JsonOutputParser()

prompt = ChatPromptTemplate.from_template(
    "Назови 3 факта о {topic}. Верни как JSON-массив."
)

chain = prompt | llm | parser
result = chain.invoke({"topic": "Марс"})
```

## Последовательные цепочки

```python
first = ChatPromptTemplate.from_template(
    "Напиши краткое описание {topic} в одном предложении."
) | llm | StrOutputParser()

second = ChatPromptTemplate.from_template(
    "Переведи на английский: {text}"
) | llm | StrOutputParser()

summary = first.invoke({"topic": "чёрные дыры"})
translation = second.invoke({"text": summary})
```

## RunnablePassthrough

```python
from langchain_core.runnables import RunnablePassthrough

chain = (
    {"text": RunnablePassthrough()}
    | ChatPromptTemplate.from_template("Резюмируй: {text}")
    | llm
    | StrOutputParser()
)

result = chain.invoke("LangChain — это фреймворк для LLM-приложений...")
```

## Итоги уровня

Теперь вы знаете основы LangChain:

- Настройка окружения
- Работа с LLM и чат-моделями
- Создание шаблонов промптов
- Построение цепочек с LCEL

На следующем уровне: память, RAG и агенты.
