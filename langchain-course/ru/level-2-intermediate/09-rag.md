---
title: "Генерация с извлечением (RAG)"
weight: 9
bookToc: true
---

# Генерация с извлечением (RAG)

## Что такое RAG?

RAG (Retrieval-Augmented Generation) объединяет поиск с генерацией. Вместо того чтобы полагаться только на обучающие данные модели, мы находим релевантные документы и включаем их в промпт.

## Как работает RAG

1. Пользователь задаёт вопрос
2. Находим релевантные документы в векторном хранилище
3. Добавляем документы в промпт
4. LLM генерирует ответ на основе документов

## Построение RAG-цепочки

```python
from langchain_openai import ChatOpenAI, OpenAIEmbeddings
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_core.runnables import RunnablePassthrough
from langchain_community.vectorstores import FAISS

# 1. Создаём векторное хранилище
embeddings = OpenAIEmbeddings(model="text-embedding-3-small")
texts = [
    "LangChain создан Харрисоном Чейзом в 2022 году.",
    "LangChain поддерживает Python и JavaScript.",
    "LCEL — это LangChain Expression Language для компоновки цепочек.",
]
vectorstore = FAISS.from_texts(texts, embeddings)
retriever = vectorstore.as_retriever()

# 2. Создаём промпт
prompt = ChatPromptTemplate.from_template("""
Ответь на вопрос, используя контекст ниже.
Если не знаешь — скажи «Не знаю».

Контекст: {context}

Вопрос: {question}
""")

# 3. Строим цепочку
llm = ChatOpenAI(model="gpt-4o-mini")

def format_docs(docs):
    return "\n".join(d.page_content for d in docs)

rag_chain = (
    {"context": retriever | format_docs, "question": RunnablePassthrough()}
    | prompt
    | llm
    | StrOutputParser()
)

# 4. Задаём вопрос
answer = rag_chain.invoke("Кто создал LangChain?")
print(answer)
```

## Добавление источников

```python
from langchain_core.runnables import RunnableParallel

rag_with_sources = RunnableParallel(
    answer=rag_chain,
    sources=retriever,
)

result = rag_with_sources.invoke("Кто создал LangChain?")
```

## Советы для лучшего RAG

- Используйте размер фрагментов 500–1000 символов
- Добавляйте перекрытие между фрагментами
- Экспериментируйте с разными моделями эмбеддингов
- Используйте фильтрацию по метаданным

## Далее

Изучим агентов — LLM, которые используют инструменты и принимают решения.
