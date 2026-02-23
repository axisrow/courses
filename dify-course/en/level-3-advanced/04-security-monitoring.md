---
title: "Security & Monitoring"
weight: 4
bookToc: true
---

# Security & Monitoring

## Security Checklist

### Authentication
- ✅ Change the default `SECRET_KEY`
- ✅ Enable HTTPS (TLS/SSL)
- ✅ Use strong admin passwords
- ✅ Restrict console access by IP if possible

### API Keys
- ✅ Rotate API keys regularly
- ✅ Use separate keys per client/integration
- ✅ Never expose keys in frontend code

### Network
- ✅ Put Dify behind a firewall
- ✅ Only expose ports 80/443
- ✅ Use private networks for internal services (DB, Redis, Vector DB)

### Data
- ✅ Encrypt data at rest (database, file storage)
- ✅ Set up automated backups
- ✅ Review uploaded documents for sensitive content

## Content Moderation

Dify has built-in moderation:

1. **Studio → your app → Add Feature → Content Moderation**
2. Options:
   - **OpenAI Moderation API** — checks for harmful content
   - **Keyword blocklist** — block specific words
   - **Custom API** — your own moderation service

## Monitoring

### Built-in Logs

- **Logs** tab in each app shows all conversations
- Filter by user, date, token usage
- Export logs for analysis

### External Monitoring

Integrate with observability tools:

- **Prometheus + Grafana** — metrics and dashboards
- **Sentry** — error tracking
- **LangFuse / Langsmith** — LLM-specific tracing

### Key Metrics to Track

| Metric | Why |
|--------|-----|
| Response latency | User experience |
| Token usage | Cost control |
| Error rate | Reliability |
| Active users | Growth |
| Knowledge retrieval accuracy | RAG quality |

## Next Step

Let's scale Dify for high traffic!
