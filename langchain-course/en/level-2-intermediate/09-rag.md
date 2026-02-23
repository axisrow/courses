---
title: "Retrieval-Augmented Generation (RAG)"
weight: 9
bookToc: true
---

# Retrieval-Augmented Generation (RAG)

## What is RAG?

RAG combines retrieval with generation. Instead of relying only on the model's training data, you fetch relevant documents and include them in the prompt. This gives the model up-to-date, specific knowledge.

## How RAG Works

1. User asks a question
2. Retrieve relevant documents from a vector store
3. Add those documents to the prompt
4. LLM generates an answer based on the documents

## Building a RAG Chain

```python
from langchain_openai import ChatOpenAI, OpenAIEmbeddings
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_core.runnables import RunnablePassthrough
from langchain_community.vectorstores import FAISS

# 1. Create vector store
embeddings = OpenAIEmbeddings(model="text-embedding-3-small")
texts = [
    "LangChain was created by Harrison Chase in 2022.",
    "LangChain supports Python and JavaScript.",
    "LCEL is LangChain Expression Language for composing chains.",
]
vectorstore = FAISS.from_texts(texts, embeddings)
retriever = vectorstore.as_retriever()

# 2. Create prompt
prompt = ChatPromptTemplate.from_template("""
Answer the question based on the context below.
If you don't know, say "I don't know."

Context: {context}

Question: {question}
""")

# 3. Build chain
llm = ChatOpenAI(model="gpt-4o-mini")

def format_docs(docs):
    return "\n".join(d.page_content for d in docs)

rag_chain = (
    {"context": retriever | format_docs, "question": RunnablePassthrough()}
    | prompt
    | llm
    | StrOutputParser()
)

# 4. Ask a question
answer = rag_chain.invoke("Who created LangChain?")
print(answer)  # "Harrison Chase created LangChain in 2022."
```

## Adding Sources

```python
from langchain_core.runnables import RunnableParallel

rag_with_sources = RunnableParallel(
    answer=rag_chain,
    sources=retriever,
)

result = rag_with_sources.invoke("Who created LangChain?")
print(result["answer"])
print(result["sources"])
```

## Tips for Better RAG

- Use good chunk sizes (500-1000 characters)
- Add overlap between chunks
- Experiment with different embedding models
- Use metadata filtering when possible

## Next Steps

Let's explore agents — LLMs that can use tools and make decisions.
