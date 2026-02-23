---
title: "Scaling & Performance"
weight: 5
bookToc: true
---

# Scaling & Performance

## Horizontal Scaling

### API Servers
Run multiple API replicas behind a load balancer:
- Use Nginx, HAProxy, or cloud load balancers
- Session affinity is NOT required (stateless API)

### Workers
Scale Celery workers independently:
- More workers = faster document processing
- More workers = more concurrent async tasks

### Vector Database
- **Qdrant**: supports distributed mode with sharding
- **Weaviate**: built-in clustering
- **Pgvector**: scale with PostgreSQL read replicas

## Caching Strategies

- **Redis**: already used by Dify for caching and queues
- **Prompt caching**: some LLM providers cache repeated prompts (cheaper & faster)
- **Knowledge retrieval cache**: cache frequent queries to reduce vector DB load

## Database Optimization

```sql
-- Monitor slow queries
SELECT query, mean_time, calls
FROM pg_stat_statements
ORDER BY mean_time DESC
LIMIT 10;
```

- Increase `SQLALCHEMY_POOL_SIZE` for more concurrent connections
- Use connection pooling (PgBouncer) for high traffic
- Regular VACUUM and index maintenance

## Cost Optimization

| Strategy | Impact |
|----------|--------|
| Use smaller models for simple tasks | 💰💰💰 |
| Cache repeated queries | 💰💰 |
| Set max token limits | 💰💰 |
| Use local models for internal apps | 💰💰💰 |
| Monitor and alert on cost spikes | 💰 |

## High Availability

- Run 2+ API replicas across availability zones
- Use managed PostgreSQL with automatic failover
- Redis Sentinel or Redis Cluster for HA
- Regular automated backups with tested restore procedures

## Congratulations! 🎉

You've completed the entire Dify course! You can now:
- ✅ Build and publish AI apps
- ✅ Use RAG, workflows, tools, and APIs
- ✅ Deploy, secure, and scale Dify for production

Happy building! 🚀
