---
title: "Performance Optimization"
weight: 12
bookToc: true
---

# Performance Optimization

Make your app fast and efficient.

## Lazy Loading

> Lazy-load the dashboard page so it only loads when the user navigates to it.

This reduces initial bundle size.

## Image Optimization

> Use lazy loading for images. Add proper width and height attributes.

## Pagination

> Instead of loading all 1000 posts at once, add pagination — 20 posts per page.

## Caching

> Cache the API response for 5 minutes to avoid unnecessary requests.

## Code Splitting

Lovable uses React's `lazy()` and `Suspense` for automatic code splitting.

> Split the admin section into a separate code chunk.

## Database Query Optimization

> Add an index on the "created_at" column. Use pagination in the Supabase query.

## Monitoring Performance

Key metrics to watch:

| Metric | Target |
|--------|--------|
| First Contentful Paint | < 1.5s |
| Largest Contentful Paint | < 2.5s |
| Total Bundle Size | < 500KB |
| API Response Time | < 200ms |

## Debouncing

> Add debouncing to the search input so it waits 300ms before making an API call.

## Summary

Optimize with lazy loading, pagination, caching, and code splitting. Ask Lovable to implement these patterns through prompts.
