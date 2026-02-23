---
title: "Celery Workers and the Task Engine"
weight: 12
bookToc: true
---

# Celery Workers and the Task Engine

## The Background Brain

While the FastAPI server handles real-time chat, **Celery** handles everything that runs in the background. Celery is a distributed task queue for Python.

## Key Components

| Component | File | Role |
|---|---|---|
| Celery App | `workers/celery_app.py` | Configures the Celery instance and broker (Redis). |
| Task Definitions | `workers/tasks.py` | Defines executable task functions. |
| Long-form Tasks | `workers/long_form_tasks.py` | Complex multi-step tasks that may take minutes. |
| Retention Tasks | `workers/retention_tasks.py` | Periodic cleanup and data retention jobs. |
| Planner | `workers/planner/` | AI-driven planning: breaks a goal into steps. |
| Executor | `workers/executor/` | Runs planned steps using MCP tools. |

## How Scheduled Tasks Work

1. You create a task with a cron expression (e.g., "every day at 9 AM").
2. The task definition is saved to the database.
3. **Celery Beat** (a scheduler process) reads the database and triggers tasks at the right time.
4. A **Celery Worker** picks up the task from the Redis queue.
5. The worker calls the planner → executor pipeline.
6. Results are stored and optionally pushed as notifications.

## The Planner → Executor Pipeline

For complex tasks, Sentient uses a two-stage approach:

1. **Planner** — An AI call that breaks the task into ordered steps.
2. **Executor** — Runs each step sequentially, calling MCP tools as needed.

This is similar to how AI agent frameworks like LangChain work, but Sentient implements its own lightweight version.

## Monitoring Workers

```bash
# Start a worker
celery -A workers.celery_app worker --loglevel=info

# Start the scheduler
celery -A workers.celery_app beat --loglevel=info

# Monitor with Flower (optional)
celery -A workers.celery_app flower
```

## Scaling

Need more throughput? Run multiple workers:

```bash
celery -A workers.celery_app worker --concurrency=4
```

Each worker can handle multiple tasks in parallel.

## Summary

Celery is the backbone of Sentient's automation. Understanding workers, beat, and the planner/executor pipeline gives you full control over background processing.
