---
title: "Deploying to Production"
weight: 15
bookToc: true
---

# Deploying to Production

## Production vs. Development

| Aspect | Development | Production |
|--------|-------------|------------|
| Database | SQLite | PostgreSQL |
| Process manager | Manual | PM2 or Docker |
| URL | localhost | Custom domain + HTTPS |
| Backups | None | Automated |
| Monitoring | Manual | Alerts |

## Docker Compose Deployment

The recommended way to run n8n in production:

```yaml
version: '3.8'
services:
  n8n:
    image: docker.n8n.io/n8nio/n8n
    restart: always
    ports:
      - "5678:5678"
    environment:
      - DB_TYPE=postgresdb
      - DB_POSTGRESDB_HOST=postgres
      - DB_POSTGRESDB_PORT=5432
      - DB_POSTGRESDB_DATABASE=n8n
      - DB_POSTGRESDB_USER=n8n
      - DB_POSTGRESDB_PASSWORD=${DB_PASSWORD}
      - N8N_ENCRYPTION_KEY=${ENCRYPTION_KEY}
      - WEBHOOK_URL=https://n8n.yourdomain.com/
      - EXECUTIONS_MODE=queue
      - QUEUE_BULL_REDIS_HOST=redis
    volumes:
      - n8n_data:/home/node/.n8n
    depends_on:
      - postgres
      - redis

  postgres:
    image: postgres:15
    restart: always
    environment:
      - POSTGRES_DB=n8n
      - POSTGRES_USER=n8n
      - POSTGRES_PASSWORD=${DB_PASSWORD}
    volumes:
      - postgres_data:/var/lib/postgresql/data

  redis:
    image: redis:7
    restart: always

  n8n-worker:
    image: docker.n8n.io/n8nio/n8n
    command: worker
    restart: always
    environment:
      - DB_TYPE=postgresdb
      - DB_POSTGRESDB_HOST=postgres
      - DB_POSTGRESDB_PORT=5432
      - DB_POSTGRESDB_DATABASE=n8n
      - DB_POSTGRESDB_USER=n8n
      - DB_POSTGRESDB_PASSWORD=${DB_PASSWORD}
      - N8N_ENCRYPTION_KEY=${ENCRYPTION_KEY}
      - EXECUTIONS_MODE=queue
      - QUEUE_BULL_REDIS_HOST=redis
    depends_on:
      - redis

volumes:
  n8n_data:
  postgres_data:
```

## Essential Environment Variables

```bash
# .env file
DB_PASSWORD=strong_random_password
ENCRYPTION_KEY=random_32_char_string
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=secure_password
WEBHOOK_URL=https://n8n.yourdomain.com/
```

## Backups

### Database Backup
```bash
# Daily PostgreSQL backup
pg_dump -U n8n n8n > backup_$(date +%Y%m%d).sql
```

### Workflow Export
Use the n8n CLI or API to export all workflows:
```bash
n8n export:workflow --all --output=workflows/
n8n export:credentials --all --output=credentials/
```

Automate with a cron job or a dedicated n8n workflow.

## Monitoring Checklist

- [ ] Set up error workflow for alerts
- [ ] Monitor disk space and memory
- [ ] Track execution success rate
- [ ] Set up uptime monitoring (e.g., UptimeRobot)
- [ ] Configure log rotation

## Update Strategy

1. **Test updates** on a staging instance first
2. **Backup** database and workflows before updating
3. **Pull new image**: `docker compose pull`
4. **Restart**: `docker compose up -d`
5. **Verify** all workflows are running correctly

## Going Live Checklist

- [ ] PostgreSQL configured (not SQLite)
- [ ] HTTPS enabled with valid certificate
- [ ] Encryption key set and backed up
- [ ] Credentials are stored securely
- [ ] Error workflow is active
- [ ] Backups are automated
- [ ] Monitoring is in place
- [ ] Unnecessary public access is restricted
- [ ] Execution data pruning is configured

## Summary

Congratulations! You have completed the n8n course. You now know how to build, optimize, secure, and deploy n8n workflows in production. Keep automating!
