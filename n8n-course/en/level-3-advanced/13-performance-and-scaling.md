---
title: "Performance and Scaling"
weight: 13
bookToc: true
---

# Performance and Scaling

## When Performance Matters

As your workflows grow, you may face:
- Slow executions
- Memory issues with large datasets
- Timeouts on long-running tasks
- Too many concurrent executions

## Processing Large Datasets

### Split In Batches
Process data in chunks instead of all at once:

1. Add **Split In Batches** node after your data source
2. Set batch size (e.g., 50 items per batch)
3. Process each batch
4. Loop back to Split In Batches

This prevents memory overload.

### Limit Node
If you only need the first N items, use the Limit node early to avoid processing unnecessary data.

### Pagination
When fetching from APIs, use pagination to load data in pages rather than all at once.

## Execution Settings

### Timeout
Set maximum execution time in **Workflow Settings**:
- Default: 300 seconds (5 minutes)
- Increase for long workflows
- Set per-workflow in Settings tab

### Error Behavior
- **Stop on first error** — Default
- **Continue on error** — Process remaining items even if some fail

## Queue Mode

For high-volume production environments, use **queue mode**:

1. Set up Redis as the message broker
2. Configure n8n to use queue mode:
```
EXECUTIONS_MODE=queue
QUEUE_BULL_REDIS_HOST=localhost
QUEUE_BULL_REDIS_PORT=6379
```
3. Run separate **worker** processes:
```bash
n8n worker
```

Benefits:
- Distribute work across multiple workers
- Handle more concurrent executions
- Better fault tolerance

## Memory Optimization

- **Avoid loading everything at once** — Use pagination and batching
- **Remove unused fields early** — Use Set node with "Keep Only Set"
- **Use the Code node wisely** — Avoid creating large arrays in memory
- **Stream binary data** — Don't load large files into memory

## Monitoring

### Execution List
Check execution history for:
- Execution time
- Success/failure rate
- Data volume

### External Monitoring
Send metrics to monitoring tools:
```
Schedule Trigger (every 5 min)
  → HTTP Request (n8n API: get execution stats)
  → IF (failure rate > 10%)
  → Slack alert
```

## Scaling Strategies

| Strategy | When to Use |
|----------|-------------|
| **Batch processing** | Large datasets |
| **Queue mode** | High concurrency |
| **Multiple workers** | CPU-heavy tasks |
| **Separate instances** | Isolate critical workflows |
| **Database optimization** | Slow queries |

## Practice

1. Create a workflow that processes 1000 items using Split In Batches (batch size 100)
2. Add timing: record start time, end time, and total duration
3. Compare performance with and without batching

## Summary

You now know how to optimize n8n for production workloads. Next, you will learn about security best practices.
