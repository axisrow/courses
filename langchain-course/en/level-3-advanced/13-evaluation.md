---
title: "Evaluation and Testing"
weight: 13
bookToc: true
---

# Evaluation and Testing

## Why Evaluate?

LLM outputs are non-deterministic. You need systematic evaluation to ensure quality.

## LangSmith for Evaluation

LangSmith is LangChain's platform for tracing, testing, and monitoring.

```bash
pip install langsmith
export LANGSMITH_API_KEY="your-key"
export LANGSMITH_TRACING=true
```

All chain runs are now automatically traced.

## Creating Test Datasets

```python
from langsmith import Client

client = Client()

dataset = client.create_dataset("my-qa-test")

client.create_examples(
    inputs=[
        {"question": "Who created LangChain?"},
        {"question": "What language is LangChain written in?"},
    ],
    outputs=[
        {"answer": "Harrison Chase"},
        {"answer": "Python and JavaScript"},
    ],
    dataset_id=dataset.id,
)
```

## Running Evaluations

```python
from langsmith.evaluation import evaluate

def predict(inputs):
    return {"answer": rag_chain.invoke(inputs["question"])}

results = evaluate(
    predict,
    data="my-qa-test",
    evaluators=["qa"],
)
```

## Custom Evaluators

```python
from langsmith.schemas import Example, Run

def check_length(run: Run, example: Example) -> dict:
    prediction = run.outputs["answer"]
    return {
        "key": "short_enough",
        "score": len(prediction) < 500,
    }

results = evaluate(predict, data="my-qa-test", evaluators=[check_length])
```

## Unit Testing Chains

```python
import pytest

def test_rag_chain():
    result = rag_chain.invoke("Who created LangChain?")
    assert "Harrison Chase" in result

def test_chain_returns_string():
    result = chain.invoke({"topic": "AI"})
    assert isinstance(result, str)
    assert len(result) > 0
```

## Testing Tips

- Test with diverse inputs (edge cases, languages, long text)
- Use deterministic settings (`temperature=0`) for testing
- Track metrics over time
- Compare different prompts and models

## Next Steps

Let's learn how to deploy LangChain applications to production.
