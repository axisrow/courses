---
title: "Working with Databases"
weight: 12
bookToc: true
---

# Working with Databases

## What is a Database?

A database stores information for your app. User accounts, blog posts, product listings, orders — all of this lives in a database.

Think of it as a smart spreadsheet that your app can read and write to automatically.

## Databases in v0

v0 has built-in support for connecting to databases. It can:

- Create database schemas (the structure of your data)
- Generate code to read and write data
- Set up connections automatically

## How to Add a Database

1. In your prompt, describe what data you need:
   - "Create a to-do app that saves tasks to a database"
   - "Build a blog with posts stored in a database"
2. v0 will suggest or set up a database (often Supabase or Vercel Postgres)
3. Follow the setup instructions to create your database account

## Common Database Operations

| Operation | What It Does | Example |
|-----------|-------------|---------|
| Create | Add new data | Adding a new blog post |
| Read | Fetch existing data | Showing all products |
| Update | Change existing data | Editing a user profile |
| Delete | Remove data | Deleting a comment |

These are called **CRUD** operations.

## Database Providers That Work with v0

- **Vercel Postgres** — built into the Vercel ecosystem
- **Supabase** — popular, has a generous free tier
- **PlanetScale** — MySQL-based, scalable
- **Neon** — serverless Postgres

## Tips

- Start with simple data structures
- Always think about what data your app needs before building
- Use the AI to help you design your database schema

## Summary

Databases store your app's data. v0 can set up database connections and generate all the code you need. Next: agentic features.
