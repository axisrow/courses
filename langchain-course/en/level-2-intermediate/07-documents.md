---
title: "Document Loaders and Text Splitters"
weight: 7
bookToc: true
---

# Document Loaders and Text Splitters

## Loading Documents

LangChain can load data from many sources: files, web pages, databases, and more.

```python
# Load a text file
from langchain_community.document_loaders import TextLoader

loader = TextLoader("my_file.txt")
docs = loader.load()
print(docs[0].page_content)
```

## Common Loaders

| Loader | Source |
|--------|--------|
| `TextLoader` | Plain text files |
| `PyPDFLoader` | PDF files |
| `CSVLoader` | CSV files |
| `WebBaseLoader` | Web pages |
| `DirectoryLoader` | All files in a folder |

```python
# Load a PDF
from langchain_community.document_loaders import PyPDFLoader

loader = PyPDFLoader("report.pdf")
pages = loader.load()

# Load a web page
from langchain_community.document_loaders import WebBaseLoader

loader = WebBaseLoader("https://example.com")
docs = loader.load()
```

## Why Split Text?

LLMs have limited context windows. Large documents must be split into smaller chunks. Good splitting preserves meaning.

## Text Splitters

```python
from langchain_text_splitters import RecursiveCharacterTextSplitter

splitter = RecursiveCharacterTextSplitter(
    chunk_size=500,
    chunk_overlap=50,
)

chunks = splitter.split_documents(docs)
print(f"Split into {len(chunks)} chunks")
```

## Splitting Strategies

| Splitter | Best For |
|----------|----------|
| `RecursiveCharacterTextSplitter` | General text (recommended) |
| `CharacterTextSplitter` | Simple splitting |
| `MarkdownTextSplitter` | Markdown files |
| `PythonCodeTextSplitter` | Python source code |
| `TokenTextSplitter` | Token-based splitting |

## Document Metadata

Each document carries metadata:

```python
for chunk in chunks:
    print(chunk.metadata)  # {"source": "my_file.txt", "page": 0}
```

## Next Steps

Now that we can load and split documents, let's store them in a vector database.
