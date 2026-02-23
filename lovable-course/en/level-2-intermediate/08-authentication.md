---
title: "Authentication"
weight: 8
bookToc: true
---

# Authentication

Add user login and registration to your app.

## Supabase Auth

Lovable uses Supabase Auth. It supports:

- Email + password
- Google login
- GitHub login
- Magic link (passwordless)

## Adding Auth

> Add user authentication. Users should be able to sign up with email and password, and log in.

Lovable creates:
- Sign up page
- Log in page
- Session management
- Protected routes

## Social Login

> Add Google login as an option on the sign-up page.

You'll need to configure Google OAuth in your Supabase dashboard.

## Protected Pages

> Make the dashboard page accessible only to logged-in users. Redirect others to the login page.

## User Profiles

> After sign-up, let users fill in their profile: name, avatar, and bio. Store it in a profiles table.

## Showing User Info

> Show the logged-in user's name and avatar in the top-right corner. Add a logout button.

## Auth Flow

```
User visits app
  → Not logged in → Show login page
  → Logged in → Show dashboard
    → Logout → Back to login
```

## Common Auth Patterns

| Pattern | Description |
|---------|-------------|
| Role-based access | Admin vs. regular user |
| Email verification | Confirm email before access |
| Password reset | "Forgot password" flow |
| Session persistence | Stay logged in across visits |

## Summary

Supabase Auth handles login, registration, and session management. Lovable sets it all up through simple prompts.
