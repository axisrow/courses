---
title: "Database Nodes"
weight: 10
bookToc: true
---

# Database Nodes

## Why Use Databases?

Databases are essential for storing, querying, and managing structured data. n8n can connect to all major databases.

## Supported Databases

| Database | Node Name |
|----------|-----------|
| PostgreSQL | Postgres |
| MySQL | MySQL |
| MongoDB | MongoDB |
| SQLite | SQLite |
| Microsoft SQL | Microsoft SQL |
| Redis | Redis |

## Connecting to a Database

1. Add a database node (e.g., **Postgres**)
2. Click **Create New Credential**
3. Fill in: Host, Port, Database name, User, Password
4. Click **Test Connection** to verify
5. Save the credential

## Common Operations

### Read Data (Select)
```sql
SELECT * FROM customers WHERE country = 'US' LIMIT 10
```
- Each row becomes one item in n8n
- Fields become JSON properties

### Insert Data
- Operation: **Insert**
- Table: `customers`
- Columns to send: map n8n fields to table columns
- n8n inserts one row per item

### Update Data
- Operation: **Update**
- Table: `customers`
- Update key: the column to match (e.g., `id`)
- Columns to update: the fields to change

### Delete Data
- Operation: **Delete**
- Table: `customers`
- Where: define which rows to remove

## Using Raw SQL

For complex queries, use **Execute Query** mode:

```sql
SELECT c.name, COUNT(o.id) as order_count
FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id
GROUP BY c.name
HAVING COUNT(o.id) > 5
ORDER BY order_count DESC
```

## Best Practices

1. **Use credentials** — Never put passwords directly in queries
2. **Use parameterized queries** — Prevent SQL injection
3. **Limit results** — Always use LIMIT to avoid huge data transfers
4. **Test with small data** — Verify your query before running on production
5. **Use transactions** — For multi-step operations that must all succeed

## Example Workflow: Sync API to Database

```
Schedule Trigger (daily)
  → HTTP Request (fetch new data from API)
  → Set (map fields to table columns)
  → Postgres (upsert into database)
```

## Practice

1. Set up a SQLite or Postgres database
2. Create a table with `id`, `name`, `email`, `created_at`
3. Build a workflow that inserts 3 sample records
4. Build another workflow that reads and filters the records

## Summary

You can now read and write data from databases. This completes the intermediate level! Next, you will move to advanced topics starting with custom functions.
