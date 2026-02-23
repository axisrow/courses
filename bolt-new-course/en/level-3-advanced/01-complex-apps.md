---
title: "Building Complex Multi-Page Apps"
weight: 11
bookToc: true
---

# Building Complex Multi-Page Apps

## Thinking Bigger

Now that you know the basics, it's time to build real, complex applications with multiple pages, user flows, and interconnected features.

## Planning Your App

Before you start prompting, plan your app structure:

1. **List all pages** — Home, Dashboard, Settings, etc.
2. **Define user flows** — What does a user do step by step?
3. **Identify data** — What information is stored and displayed?
4. **Sketch relationships** — How do pages connect to each other?

## Building in Phases

Don't try to build everything at once. Break it into phases:

### Phase 1: Core structure
> "Create a project management app with these pages: Dashboard, Projects list, Single Project view, Tasks list, and Settings. Set up navigation between all pages."

### Phase 2: Add data
> "Add a database for projects (name, description, status, due date) and tasks (title, assigned to, priority, status). Each project has multiple tasks."

### Phase 3: Add features
> "On the Dashboard, show: total projects, tasks due this week, a chart of task completion, and recent activity."

### Phase 4: Polish
> "Add animations for page transitions, loading skeletons while data loads, and empty states when there's no data yet."

## Managing Context

For large projects, Bolt's improved context management handles complexity well. But you can help by:

- Referencing specific pages: "On the Projects page..."
- Being precise about components: "In the sidebar navigation..."
- Naming things consistently

## Real-World App Example

A complete freelancer management app:
- Client list with contact details
- Project tracking per client
- Invoice generation
- Time tracking
- Dashboard with earnings overview

## Practice Exercise

Plan and build a 5-page application of your choice. Write out all pages, data, and features before you start prompting.

---

**Next lesson:** [SEO & Performance Optimization →](02-seo-performance.md)
