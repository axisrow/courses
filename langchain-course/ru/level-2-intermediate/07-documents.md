---
title: "Загрузчики документов и разделители текста"
weight: 7
bookToc: true
---

# Загрузчики документов и разделители текста

## Загрузка документов

LangChain умеет загружать данные из файлов, веб-страниц, баз данных и других источников.

```python
from langchain_community.document_loaders import TextLoader

loader = TextLoader("my_file.txt")
docs = loader.load()
print(docs[0].page_content)
```

## Популярные загрузчики

| Загрузчик | Источник |
|-----------|---------|
| `TextLoader` | Текстовые файлы |
| `PyPDFLoader` | PDF-файлы |
| `CSVLoader` | CSV-файлы |
| `WebBaseLoader` | Веб-страницы |
| `DirectoryLoader` | Все файлы в папке |

```python
from langchain_community.document_loaders import PyPDFLoader
loader = PyPDFLoader("report.pdf")
pages = loader.load()

from langchain_community.document_loaders import WebBaseLoader
loader = WebBaseLoader("https://example.com")
docs = loader.load()
```

## Зачем разделять текст?

У LLM ограниченное контекстное окно. Большие документы нужно разбивать на фрагменты. Хорошее разделение сохраняет смысл.

## Разделители текста

```python
from langchain_text_splitters import RecursiveCharacterTextSplitter

splitter = RecursiveCharacterTextSplitter(
    chunk_size=500,
    chunk_overlap=50,
)

chunks = splitter.split_documents(docs)
print(f"Разделено на {len(chunks)} фрагментов")
```

## Стратегии разделения

| Разделитель | Подходит для |
|------------|-------------|
| `RecursiveCharacterTextSplitter` | Общий текст (рекомендуется) |
| `MarkdownTextSplitter` | Markdown-файлы |
| `PythonCodeTextSplitter` | Код на Python |
| `TokenTextSplitter` | Разделение по токенам |

## Метаданные документов

```python
for chunk in chunks:
    print(chunk.metadata)  # {"source": "my_file.txt", "page": 0}
```

## Далее

Теперь научимся хранить документы в векторной базе данных.
