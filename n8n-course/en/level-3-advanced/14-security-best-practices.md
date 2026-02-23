---
title: "Security Best Practices"
weight: 14
bookToc: true
---

# Security Best Practices

## Why Security Matters

n8n workflows often handle sensitive data: API keys, user data, passwords, and business information. One mistake can expose everything.

## Credential Management

### Use n8n Credentials
- **Never** hardcode API keys in node parameters
- Always use the credential system
- Credentials are encrypted at rest
- Share credentials across workflows safely

### Rotate Keys Regularly
- Update API keys every 90 days
- Remove unused credentials
- Audit who has access to what

## Environment Variables

Store sensitive configuration outside n8n:

```bash
export API_SECRET=your_secret_here
export DB_PASSWORD=your_password_here
```

Access them in workflows (if allowed by admin):
```
{{ $env.API_SECRET }}
```

## Webhook Security

### Authentication
Always protect public webhooks:
- **Basic Auth** — Username/password
- **Header Auth** — Custom header with secret token
- **IP Whitelist** — Only allow specific IP addresses

### Validate Input
Never trust incoming data:
```
Webhook → IF (required fields exist?)
        → IF (data types are correct?)
        → Process data
```

### Verify Signatures
Services like GitHub and Stripe sign webhook payloads:
```javascript
const crypto = require('crypto');
const signature = $json.headers['x-hub-signature-256'];
const hash = 'sha256=' + crypto.createHmac('sha256', SECRET)
  .update(JSON.stringify($json.body))
  .digest('hex');

if (signature !== hash) {
  throw new Error('Invalid signature');
}
```

## Network Security

- **Use HTTPS** — Always encrypt traffic
- **Reverse proxy** — Put n8n behind Nginx or Caddy
- **Firewall** — Restrict access to n8n port (5678)
- **VPN** — Access n8n through a VPN for internal use

### Nginx Configuration Example
```nginx
server {
    listen 443 ssl;
    server_name n8n.yourdomain.com;

    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;

    location / {
        proxy_pass http://localhost:5678;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## User Access Control

- **Limit admin access** — Only admins should change settings
- **Use separate instances** — Isolate production from development
- **Audit logs** — Track who changed what
- **Disable public API** if not needed

## Data Protection

- **Minimize data collection** — Only process what you need
- **Encrypt sensitive fields** — Before storing in databases
- **Set execution data retention** — Auto-delete old execution data
- **Comply with regulations** — GDPR, CCPA, etc.

```
N8N_EXECUTIONS_DATA_PRUNE=true
N8N_EXECUTIONS_DATA_MAX_AGE=168  # hours
```

## Practice

1. Set up a webhook with Basic Auth
2. Add input validation (check required fields)
3. Store results using credentials (not hardcoded values)
4. Configure execution data pruning

## Summary

Security is not optional. Apply these practices to every workflow. Next, the final lesson: deploying n8n to production.
