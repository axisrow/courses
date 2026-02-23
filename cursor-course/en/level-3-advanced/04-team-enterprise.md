---
title: "Team Collaboration & Enterprise"
weight: 4
bookToc: true
---

# Team Collaboration & Enterprise

## Cursor for Teams

Cursor isn't just for solo developers. Over half of the Fortune 500 use it, including Salesforce (20,000+ developers) and NVIDIA (40,000+ engineers).

## Business & Enterprise Plans

- **Business** — Team management, centralized billing, usage analytics
- **Enterprise** — SSO, SAML, admin controls, compliance features, dedicated support

## Sharing Rules Across Teams

### Shared .cursorrules
Commit `.cursorrules` to your Git repository. Every team member gets the same AI behavior:
```
# Team coding standards
- Use our internal component library from @company/ui
- Follow the API patterns in docs/api-guide.md
- All PRs must include tests
```

### Shared Documentation
Keep a `docs/` folder with architecture decisions, style guides, and patterns. Team members can reference it with `@docs/`.

## Security & Privacy

Enterprise features include:
- **Privacy mode** — Your code is never stored on Cursor's servers
- **SOC 2 compliance** — Enterprise-grade security
- **Self-hosted options** — Keep everything on your infrastructure
- **Admin controls** — Manage which models and features are available

## Onboarding New Team Members

Cursor helps new developers understand existing code:
1. Open the project → Chat → "Explain the architecture of this project"
2. `@codebase` "Where is the main entry point?"
3. `@docs/` "What are the key patterns used here?"

## Summary

- Cursor scales from individual to 40,000+ developer teams
- Share `.cursorrules` via Git for consistent AI behavior
- Enterprise features cover security, compliance, and admin control
- AI helps new team members ramp up faster
