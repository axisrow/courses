---
title: "Celery Workers 与任务引擎"
weight: 12
bookToc: true
---

# Celery Workers 与任务引擎

## 后台大脑

FastAPI 服务器处理实时聊天，而 **Celery** 处理所有后台任务。Celery 是 Python 的分布式任务队列。

## 关键组件

| 组件 | 文件 | 作用 |
|---|---|---|
| Celery App | `workers/celery_app.py` | 配置 Celery 实例和代理（Redis）。 |
| 任务定义 | `workers/tasks.py` | 定义可执行的任务函数。 |
| 长时间任务 | `workers/long_form_tasks.py` | 可能需要数分钟的复杂多步任务。 |
| 保留任务 | `workers/retention_tasks.py` | 定期清理和数据保留。 |
| 规划器 | `workers/planner/` | AI 驱动的规划：将目标分解为步骤。 |
| 执行器 | `workers/executor/` | 使用 MCP 工具运行规划的步骤。 |

## "规划器 → 执行器"管道

对于复杂任务，Sentient 使用两阶段方法：
1. **规划器** — AI 调用，将任务分解为有序步骤。
2. **执行器** — 按顺序执行每个步骤，根据需要调用 MCP 工具。

## 运行 Workers

```bash
celery -A workers.celery_app worker --loglevel=info
celery -A workers.celery_app beat --loglevel=info
```

## 扩展

```bash
celery -A workers.celery_app worker --concurrency=4
```

多个 worker 可以并行处理任务。

## 小结

Celery 是 Sentient 自动化的骨干。理解 workers、调度器和规划器/执行器管道，让你完全掌控后台处理。
