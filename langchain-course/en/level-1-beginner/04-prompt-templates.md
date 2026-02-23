---
title: "Prompt Templates"
weight: 4
bookToc: true
---

# Prompt Templates

## Why Use Templates?

Hardcoding prompts is inflexible. Templates let you create reusable prompts with variables.

## Basic Prompt Template

```python
from langchain_core.prompts import PromptTemplate

template = PromptTemplate.from_template(
    "Explain {topic} in simple terms."
)

prompt = template.invoke({"topic": "quantum computing"})
print(prompt.text)
# Output: Explain quantum computing in simple terms.
```

## Chat Prompt Templates

```python
from langchain_core.prompts import ChatPromptTemplate

template = ChatPromptTemplate.from_messages([
    ("system", "You are an expert in {field}."),
    ("human", "{question}"),
])

messages = template.invoke({
    "field": "biology",
    "question": "What is DNA?",
})
```

## Combining with Models

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(model="gpt-4o-mini")

template = ChatPromptTemplate.from_messages([
    ("system", "You are a helpful translator. Translate to {language}."),
    ("human", "{text}"),
])

# Using LCEL (LangChain Expression Language)
chain = template | llm

response = chain.invoke({
    "language": "French",
    "text": "Hello, how are you?",
})
print(response.content)
```

## Few-Shot Prompting

```python
from langchain_core.prompts import FewShotChatMessagePromptTemplate

examples = [
    {"input": "happy", "output": "sad"},
    {"input": "tall", "output": "short"},
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
    ("system", "Give the opposite of each word."),
    few_shot,
    ("human", "{input}"),
])
```

## Next Steps

Now that you know how to create prompts, let's learn how to build chains.
