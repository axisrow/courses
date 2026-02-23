---
title: "Security, Authentication, and Self-Hosting"
weight: 14
bookToc: true
---

# Security, Authentication, and Self-Hosting

## Authentication System

Sentient uses **JWT (JSON Web Tokens)** for user authentication:

- `src/server/main/auth/` contains the authentication logic.
- Tokens are signed using the `python-jose` library with cryptographic keys.
- Each API request includes a JWT in the header, which the server validates.

## OAuth for Integrations

When you connect an external service (Gmail, Slack, etc.), Sentient uses **OAuth 2.0**:

1. The user clicks "Connect" and is redirected to the service's login page.
2. After granting permission, the service returns an **access token** and **refresh token**.
3. Sentient stores these tokens securely in the database.
4. Tokens are refreshed automatically when they expire.

The `requests-oauthlib` library handles the OAuth flow.

## Self-Hosting Best Practices

### Use Docker Compose

The `src/docker-compose.selfhost.yml` file is the recommended way to self-host. It includes all services with secure defaults.

### Environment Variables

- Never commit `.env` files to version control.
- Use strong, unique values for `SECRET_KEY` and database passwords.
- Rotate API keys periodically.

### Network Security

- Run Sentient behind a **reverse proxy** (nginx is included in both client and server Dockerfiles).
- Enable **HTTPS** with a valid SSL certificate (Let's Encrypt is free).
- Restrict database ports to internal networks only.

### Data Privacy

- All data is stored locally when self-hosting.
- If you use a local AI model (Ollama), no data leaves your network.
- Memories, chat history, and task results stay in your PostgreSQL database.

## Production Deployment Checklist

- [ ] HTTPS enabled with valid certificate.
- [ ] Database passwords changed from defaults.
- [ ] Redis protected with a password.
- [ ] Environment variables secured.
- [ ] Regular database backups configured.
- [ ] Firewall rules in place.
- [ ] Monitoring and logging enabled.

## Summary

Sentient takes security seriously with JWT auth, OAuth for integrations, and a fully self-hostable architecture. Follow the checklist above for a production-ready deployment.
