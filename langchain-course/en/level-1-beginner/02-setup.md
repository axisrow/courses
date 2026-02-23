---
title: "Setting Up Your Environment"
weight: 2
bookToc: true
---

# Setting Up Your Environment

## Prerequisites

- Python 3.9 or higher
- A terminal or command line
- An API key from OpenAI (or another LLM provider)

## Install Python

Check your Python version:

```bash
python --version
```

If you need Python, download it from [python.org](https://python.org).

## Create a Virtual Environment

```bash
python -m venv langchain-env
source langchain-env/bin/activate  # Linux/macOS
# langchain-env\Scripts\activate   # Windows
```

## Install LangChain

```bash
pip install langchain langchain-openai
```

## Set Your API Key

Create a `.env` file:

```
OPENAI_API_KEY=sk-your-key-here
```

Load it in Python:

```python
from dotenv import load_dotenv
load_dotenv()
```

Or set it directly:

```python
import os
os.environ["OPENAI_API_KEY"] = "sk-your-key-here"
```

## Verify Installation

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini")
response = llm.invoke("Say hello!")
print(response.content)
```

If you see a response, everything is working.

## Project Structure

```
my-langchain-project/
├── .env
├── requirements.txt
└── main.py
```

## Next Steps

Now that your environment is ready, let's learn how to work with LLMs in LangChain.
