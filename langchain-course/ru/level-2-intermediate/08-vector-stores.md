---
title: "Векторные хранилища и эмбеддинги"
weight: 8
bookToc: true
---

# Векторные хранилища и эмбеддинги

## Что такое эмбеддинги?

Эмбеддинги превращают текст в числа (векторы). Похожие тексты получают похожие векторы. Это позволяет искать по смыслу, а не только по ключевым словам.

## Создание эмбеддингов

```python
from langchain_openai import OpenAIEmbeddings

embeddings = OpenAIEmbeddings(model="text-embedding-3-small")
vector = embeddings.embed_query("Что такое LangChain?")
print(f"Длина вектора: {len(vector)}")  # 1536
```

## Что такое векторное хранилище?

Это база данных, оптимизированная для хранения и поиска векторов. Вы загружаете документы, а затем находите самые релевантные по схожести.

## Использование FAISS

```python
from langchain_community.vectorstores import FAISS

texts = ["LangChain — это фреймворк", "Python — это язык", "Коты милые"]
vectorstore = FAISS.from_texts(texts, embeddings)

results = vectorstore.similarity_search("Что такое LangChain?", k=2)
for doc in results:
    print(doc.page_content)
```

## Использование Chroma

```python
from langchain_chroma import Chroma

vectorstore = Chroma.from_documents(
    documents=chunks,
    embedding=embeddings,
    persist_directory="./chroma_db",
)
```

## Популярные хранилища

| Хранилище | Тип | Особенности |
|-----------|-----|------------|
| FAISS | Локальное | Быстрое, без сервера |
| Chroma | Локальное/Сервер | Простое, с сохранением |
| Pinecone | Облачное | Управляемое, масштабируемое |
| Weaviate | Облако/Свой сервер | Много функций |
| Qdrant | Облако/Свой сервер | Высокая производительность |

## Интерфейс Retriever

```python
retriever = vectorstore.as_retriever(
    search_type="similarity",
    search_kwargs={"k": 3},
)

docs = retriever.invoke("Расскажи о LangChain")
```

## Далее

С векторными хранилищами и ретриверами мы готовы строить RAG.
