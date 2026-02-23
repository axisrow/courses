---
title: "Database with Supabase"
weight: 7
bookToc: true
---

# Database with Supabase

Store and retrieve data for your app.

## What Is Supabase?

Supabase is an open-source backend. It gives you a PostgreSQL database, authentication, and APIs — all managed for you. Lovable integrates with Supabase natively.

## Connecting Supabase

1. In your Lovable project, click **Supabase** in the settings.
2. Lovable can create a Supabase project for you automatically.
3. Or connect an existing one with your project URL and anon key.

## Creating Tables

Ask the AI:

> Create a "posts" table with columns: id, title, content, created_at. Show all posts on the home page.

Lovable will:
- Create the table in Supabase.
- Generate code to fetch and display data.
- Add proper TypeScript types.

## CRUD Operations

> Let users create new posts with a form. Add edit and delete buttons to each post.

Now you have full Create, Read, Update, Delete functionality.

## Real-Time Data

Supabase supports real-time subscriptions:

> Make the posts list update in real-time when a new post is added.

## Row Level Security (RLS)

Supabase uses RLS to control who can access data:

> Only allow users to edit their own posts.

The AI sets up proper RLS policies.

## Common Database Patterns

| Pattern | Example |
|---------|---------|
| User profiles | Store name, avatar, bio per user |
| Content management | Posts, articles, comments |
| E-commerce | Products, orders, cart items |
| Analytics | Events, page views, metrics |

## Summary

Supabase gives your Lovable app a powerful database. You can create tables, perform CRUD, use real-time updates, and secure data — all through prompts.
