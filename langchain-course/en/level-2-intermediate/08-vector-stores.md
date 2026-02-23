---
title: "Vector Stores and Embeddings"
weight: 8
bookToc: true
---

# Vector Stores and Embeddings

## What Are Embeddings?

Embeddings convert text into numbers (vectors). Similar texts get similar vectors. This lets us search by meaning, not just keywords.

## Creating Embeddings

```python
from langchain_openai import OpenAIEmbeddings

embeddings = OpenAIEmbeddings(model="text-embedding-3-small")

vector = embeddings.embed_query("What is LangChain?")
print(f"Vector length: {len(vector)}")  # 1536
```

## What is a Vector Store?

A vector store is a database optimized for storing and searching vectors. You put documents in, and later find the most relevant ones by similarity.

## Using FAISS (Local)

```python
# pip install faiss-cpu
from langchain_community.vectorstores import FAISS

texts = ["LangChain is a framework", "Python is a language", "Cats are cute"]
vectorstore = FAISS.from_texts(texts, embeddings)

# Search
results = vectorstore.similarity_search("What is LangChain?", k=2)
for doc in results:
    print(doc.page_content)
```

## Using Chroma

```python
# pip install chromadb
from langchain_chroma import Chroma

vectorstore = Chroma.from_documents(
    documents=chunks,
    embedding=embeddings,
    persist_directory="./chroma_db",
)
```

## Popular Vector Stores

| Store | Type | Notes |
|-------|------|-------|
| FAISS | Local | Fast, no server needed |
| Chroma | Local/Server | Easy to use, persistent |
| Pinecone | Cloud | Managed, scalable |
| Weaviate | Cloud/Self-hosted | Feature-rich |
| Qdrant | Cloud/Self-hosted | High performance |

## Retriever Interface

Convert any vector store to a retriever:

```python
retriever = vectorstore.as_retriever(
    search_type="similarity",
    search_kwargs={"k": 3},
)

docs = retriever.invoke("Tell me about LangChain")
```

## Next Steps

With vector stores and retrievers ready, we can build RAG — Retrieval-Augmented Generation.
