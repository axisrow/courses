---
title: "Performance Optimization"
weight: 14
bookToc: true
---

# Performance Optimization

## Why Optimize?

CrewAI crews can be slow and expensive. Each agent call uses the LLM API. Optimizing saves time and money.

## 1. Choose the Right Model

| Task Type | Recommended Model |
|-----------|------------------|
| Complex reasoning | GPT-4o, Claude Sonnet |
| Simple formatting | GPT-4o-mini |
| Local/private data | Ollama (Llama 3) |

## 2. Reduce Agent Count

More agents = more API calls. Only create agents that serve a distinct purpose.

❌ Bad: 5 agents for a simple blog post
✅ Good: 2 agents — researcher + writer

## 3. Optimize Task Descriptions

Short, clear descriptions produce faster results:

```python
# Slow - vague
Task(description="Write something about AI")

# Fast - specific
Task(
    description="Write a 300-word blog post about 3 benefits of AI in healthcare.",
    expected_output="A markdown blog post with 3 sections, each 100 words."
)
```

## 4. Use Async Execution

Run independent tasks in parallel:

```python
task_a = Task(
    description="Research topic A",
    expected_output="Summary of A",
    agent=researcher,
    async_execution=True
)

task_b = Task(
    description="Research topic B",
    expected_output="Summary of B",
    agent=researcher,
    async_execution=True
)
```

## 5. Limit Iterations

```python
agent = Agent(
    role="Analyst",
    goal="Analyze data",
    backstory="...",
    max_iter=5  # prevent runaway loops
)
```

## 6. Cache and Memory

Enable memory to avoid re-computing information:

```python
crew = Crew(
    agents=[...],
    tasks=[...],
    memory=True,
    cache=True
)
```

## 7. Output Files

Save intermediate results to avoid re-running:

```python
Task(
    description="Research topic",
    expected_output="Report",
    agent=researcher,
    output_file="research_cache.md"
)
```

## Cost Monitoring

Track your spending:

```python
result = crew.kickoff()
print(result.token_usage)
```

## Optimization Checklist

1. ✅ Use the cheapest model that works for each task
2. ✅ Minimize agent count
3. ✅ Write specific task descriptions
4. ✅ Use async for parallel tasks
5. ✅ Set max_iter on agents
6. ✅ Enable caching
7. ✅ Monitor token usage

## Summary

Optimize by choosing the right models, writing specific tasks, running parallel work, and monitoring costs. Small changes can save significant time and money.

---

**Next:** Building a real-world project.
