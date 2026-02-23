---
title: "Team Management & Tenants"
weight: 14
bookToc: true
---

# Team Management & Tenants

## Multi-User Support

Nexent is designed for teams. Multiple users can share the same installation, each with their own accounts, agents, and knowledge bases.

## Key Concepts

| Concept | Description |
|---------|-------------|
| **Tenant** | An isolated workspace — like a separate company within Nexent |
| **User** | A person with an account in a tenant |
| **Role** | A set of permissions (admin, editor, viewer) |
| **Invitation** | How you add new users to your tenant |

## Setting Up Users

1. Go to **Settings → User Management**.
2. Click **Invite User**.
3. Enter their email address.
4. Assign a role.
5. Send the invitation.

## Roles & Permissions

- **Admin** — full access: manage users, agents, knowledge bases, and settings.
- **Editor** — can create and edit agents and knowledge bases, but cannot manage users.
- **Viewer** — can use agents and search knowledge bases, but cannot create or modify them.

## Shared vs. Personal Resources

- **Global knowledge bases** — accessible to all users in the tenant.
- **Personal knowledge bases** — only visible to the creator.
- **Agents** — can be shared across the team or kept private.

## Tenant Isolation

Each tenant is fully isolated:

- Data is not shared between tenants.
- Agents from one tenant cannot access another tenant's knowledge bases.
- Model provider configurations can be separate per tenant.

## Best Practices

- **Create clear roles.** Don't give everyone admin access.
- **Organize knowledge bases.** Use naming conventions so the team can find what they need.
- **Review access regularly.** Remove users who no longer need access.

## Practice Exercise

1. Create a new user account.
2. Assign them a limited role.
3. Share an agent and a knowledge base with them.
4. Verify they can use shared resources but not access restricted ones.
