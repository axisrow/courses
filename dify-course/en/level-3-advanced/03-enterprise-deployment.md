---
title: "Enterprise Deployment"
weight: 3
bookToc: true
---

# Enterprise Deployment

## Production Architecture

A production Dify deployment includes:

- **Nginx** — reverse proxy and SSL termination
- **API Server** — Flask-based backend
- **Worker** — Celery workers for async tasks
- **Web** — Next.js frontend
- **PostgreSQL** — main database
- **Redis** — cache and message queue
- **Vector DB** — Weaviate, Qdrant, or Pgvector

## Docker Compose (Production)

```yaml
# Key changes from development:
services:
  nginx:
    image: nginx:latest
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    ports:
      - "443:443"

  api:
    image: langgenius/dify-api:latest
    environment:
      - MODE=api
      - LOG_LEVEL=WARNING
    deploy:
      replicas: 2

  worker:
    image: langgenius/dify-api:latest
    environment:
      - MODE=worker
    deploy:
      replicas: 2
```

## Kubernetes Deployment

For larger teams, use the official Helm chart:

```bash
helm repo add dify https://langgenius.github.io/dify-helm
helm install dify dify/dify -f values.yaml
```

## Environment Variables

Key production settings:

| Variable | Purpose |
|----------|---------|
| `SECRET_KEY` | Encryption key (change from default!) |
| `CONSOLE_URL` | Public URL of your instance |
| `APP_URL` | Public URL for app access |
| `LOG_LEVEL` | Set to WARNING or ERROR |
| `SQLALCHEMY_POOL_SIZE` | Database connection pool |

## Backups

Back up regularly:
- PostgreSQL: `pg_dump`
- Vector DB: provider-specific backup
- Uploaded files: `/app/api/storage`

## Next Step

Let's secure and monitor your deployment!
