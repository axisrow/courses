---
title: "Working with Databases"
weight: 6
bookToc: true
---

# Working with Databases

## What Is a Database?

A database is where your app stores information — like user profiles, product lists, or blog posts. Think of it as a smart spreadsheet that your app can read and write to automatically.

## Databases in Bolt.new

Bolt.new includes built-in database support. You don't need to set up servers or install anything. Just tell the AI what data you need to store.

## Example: Building a Contact List App

Try this prompt:

> "Create a contact manager app. I need to store contacts with name, email, phone number, and company. Include a form to add new contacts and a table to view all contacts. Allow editing and deleting contacts."

Bolt will automatically:
- Create a database to store contacts
- Build a form for adding data
- Build a table for viewing data
- Add edit and delete functionality

## Understanding Data Structure

When you ask Bolt to store data, think about:

- **What information** do you need to save? (fields)
- **How are things related?** (e.g., a user has many orders)
- **What actions** do users need? (create, read, update, delete)

## Common Database Uses

| Use Case | Data Stored |
|----------|------------|
| Blog | Posts, authors, comments |
| Online store | Products, orders, customers |
| Task manager | Tasks, categories, users |
| Booking system | Appointments, clients, services |

## Tips

- **Start simple** — begin with a few fields, add more later
- **Think about what changes** — data that users create or update belongs in a database
- **Static content** (like your About page text) doesn't need a database

## Practice Exercise

Ask Bolt to create a simple book library app where you can add books (title, author, year, rating) and view them in a list.

---

**Next lesson:** [User Authentication →](02-user-authentication.md)
