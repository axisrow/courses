---
title: "Advanced Workflows"
weight: 2
bookToc: true
---

# Advanced Workflows

## Beyond Simple Chains

Level 2 covered basic workflows. Now let's build production-grade pipelines.

## Parallel Execution

Run multiple branches at the same time:

1. From one node, draw connections to several nodes
2. They execute in parallel
3. Use a **Variable Assigner** to merge results

**Use case**: Query 3 knowledge bases simultaneously, then combine answers.

## Iteration (Loops)

Process a list of items one by one:

1. Use a **Code** node to generate an array
2. Connect to an **Iteration** node
3. Inside the loop, process each item (e.g., LLM call)
4. Collect results

**Use case**: Analyze 10 customer reviews, one at a time.

## Error Handling

- **Retry**: Set retry count on HTTP and LLM nodes
- **Fallback**: Use IF/ELSE to check if a node returned an error
- **Default values**: Provide fallback responses if a step fails

## Code Nodes

Write Python or JavaScript for custom logic:

```python
def main(inputs):
    text = inputs["text"]
    words = text.split()
    return {
        "word_count": len(words),
        "preview": " ".join(words[:20])
    }
```

## Advanced Patterns

### Map-Reduce
1. Split input into parts
2. Process each part with LLM (iteration)
3. Combine results with another LLM

### Chain of Verification
1. LLM generates answer
2. LLM generates verification questions
3. LLM answers verification questions
4. LLM revises original answer

## Performance Tips

- Minimize LLM calls — each one adds latency
- Use Code nodes for logic that doesn't need AI
- Cache frequently used knowledge retrieval results

## Next Step

Let's deploy Dify for enterprise use!
