---
title: "Working with APIs"
weight: 6
bookToc: true
---

# Working with APIs

## What is an API?

An API (Application Programming Interface) is a way for two programs to talk to each other. When you use n8n to connect to Slack, Google Sheets, or any other service, you are using their API.

## The HTTP Request Node

This is your universal tool for working with any API.

### HTTP Methods

| Method | Purpose | Example |
|--------|---------|---------|
| **GET** | Read data | Fetch a list of users |
| **POST** | Create data | Add a new record |
| **PUT** | Update data | Change a user's name |
| **DELETE** | Remove data | Delete a record |

### Making a GET Request

1. Add an **HTTP Request** node
2. Set Method to **GET**
3. Enter the URL: `https://jsonplaceholder.typicode.com/posts/1`
4. Click **Execute Step**

You will receive a JSON object with `userId`, `id`, `title`, and `body`.

### Making a POST Request

1. Set Method to **POST**
2. URL: `https://jsonplaceholder.typicode.com/posts`
3. Body Content Type: **JSON**
4. Body:
```json
{
  "title": "My Post",
  "body": "Hello from n8n!",
  "userId": 1
}
```

## Authentication

Most APIs require authentication. n8n supports:

### API Key
Add a header like `Authorization: Bearer YOUR_KEY` or use query parameter `?api_key=YOUR_KEY`.

### OAuth2
For services like Google, Slack, GitHub:
1. Go to **Settings → Credentials**
2. Click **Add Credential**
3. Choose the service
4. Follow the OAuth2 flow (login and authorize)

### Credentials in n8n
Store API keys safely:
1. Create a credential once
2. Reuse it across multiple workflows
3. Keys are encrypted and stored securely

## Working with JSON

API responses are usually in JSON format. Access fields using expressions:

- `{{ $json.title }}` — Get the title field
- `{{ $json.data.items[0].name }}` — Access nested data
- `{{ $json.results.length }}` — Count items

## Pagination

Some APIs return data in pages. To get all data:

1. Use the **HTTP Request** node with pagination enabled
2. Set **Pagination Mode** to the appropriate type
3. n8n will automatically fetch all pages

## Error Handling for API Calls

APIs can fail. Common issues:
- **401** — Bad authentication
- **404** — Resource not found
- **429** — Too many requests (rate limit)
- **500** — Server error

Enable **Continue on Fail** in node settings to handle errors gracefully.

## Practice

Build a workflow that:
1. Fetches weather data from a free API (like OpenWeatherMap)
2. Extracts the temperature and description
3. Formats it into a readable message

## Summary

You can now work with any API using the HTTP Request node. Next, you will learn how to transform and reshape data.
