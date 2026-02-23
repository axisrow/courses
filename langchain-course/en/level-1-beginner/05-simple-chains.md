---
title: "Simple Chains"
weight: 5
bookToc: true
---

# Simple Chains

## What is a Chain?

A chain connects multiple steps together. For example: format a prompt → send to LLM → parse the output.

## LCEL — LangChain Expression Language

LCEL uses the pipe operator `|` to connect components:

```python
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser

prompt = ChatPromptTemplate.from_template("Tell a joke about {topic}")
llm = ChatOpenAI(model="gpt-4o-mini")
parser = StrOutputParser()

chain = prompt | llm | parser

result = chain.invoke({"topic": "programming"})
print(result)  # A string, not an AIMessage
```

## Output Parsers

Output parsers convert model responses into useful formats:

```python
from langchain_core.output_parsers import JsonOutputParser

parser = JsonOutputParser()

prompt = ChatPromptTemplate.from_template(
    "List 3 facts about {topic}. Return as JSON array."
)

chain = prompt | llm | parser
result = chain.invoke({"topic": "Mars"})
# result is a Python list
```

## Sequential Chains

You can chain multiple LLM calls:

```python
first = ChatPromptTemplate.from_template(
    "Write a one-sentence summary of {topic}."
) | llm | StrOutputParser()

second = ChatPromptTemplate.from_template(
    "Translate this to Spanish: {text}"
) | llm | StrOutputParser()

# Run sequentially
summary = first.invoke({"topic": "black holes"})
translation = second.invoke({"text": summary})
```

## RunnablePassthrough

Pass data through without changes:

```python
from langchain_core.runnables import RunnablePassthrough

chain = (
    {"text": RunnablePassthrough()}
    | ChatPromptTemplate.from_template("Summarize: {text}")
    | llm
    | StrOutputParser()
)

result = chain.invoke("LangChain is a framework for LLM apps...")
```

## Summary

You now know the basics of LangChain! You can:

- Set up an environment
- Use LLMs and chat models
- Create prompt templates
- Build chains with LCEL

In the next level, we'll explore memory, RAG, and agents.
