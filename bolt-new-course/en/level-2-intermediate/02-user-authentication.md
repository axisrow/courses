---
title: "User Authentication"
weight: 7
bookToc: true
---

# User Authentication

## What Is Authentication?

Authentication means letting users create accounts and log in to your app. This way, each user sees their own data and settings.

## Adding Auth to Your App

Bolt.new has built-in user management. Simply ask:

> "Add user registration and login to my app. Users should sign up with email and password. After logging in, they should see their personal dashboard."

## What Bolt Creates

When you ask for authentication, Bolt sets up:

- **Sign-up page** — where new users create accounts
- **Login page** — where existing users sign in
- **Password security** — passwords are encrypted automatically
- **Session management** — users stay logged in until they log out
- **Protected pages** — certain pages only visible to logged-in users

## Social Login

You can also ask for social login:

> "Add Google and GitHub login options to the sign-up page"

This lets users sign in with their existing accounts — no new password needed.

## User Roles

For more complex apps, you can add roles:

> "Create two user roles: 'admin' and 'regular user'. Admins can see all data and manage users. Regular users can only see their own data."

## Common Authentication Features

- Email verification
- Password reset ("Forgot password?" flow)
- Profile editing
- Account deletion
- Remember me / Stay logged in

## Security Tips

- Always use Bolt's built-in auth — don't try to build your own
- Ask for email verification to prevent fake accounts
- Add password strength requirements

## Practice Exercise

Add user authentication to the contact manager from the previous lesson. Each user should only see their own contacts.

---

**Next lesson:** [Design Systems & Styling →](03-design-systems.md)
