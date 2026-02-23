---
title: "Components & Layout"
weight: 6
bookToc: true
---

# Components & Layout

Build complex UIs using reusable components.

## What Are Components?

Components are building blocks. A button, a card, a navigation bar — each is a component. Lovable generates React components automatically.

## Creating Components via Prompts

> Create a reusable card component with an image, title, description, and a "Learn More" button.

The AI will create a separate component file you can reuse across pages.

## Multi-Page Apps

> Add a second page called "About". Add navigation between Home and About.

Lovable sets up routing (React Router) for you.

## Layout Patterns

### Dashboard Layout

> Create a dashboard with a sidebar navigation, a top header with user avatar, and a main content area.

### Landing Page Layout

> Create a landing page with hero section, features grid, testimonials, and footer.

## Shadcn/UI Components

Lovable uses [shadcn/ui](https://ui.shadcn.com/) — a popular component library. You can request specific components:

- Dialog, Sheet, Drawer
- Table, DataTable
- Tabs, Accordion
- Toast notifications
- Dropdown menus

Example:

> Add a data table with sorting and pagination for the users list.

## Component Organization

The generated code follows clean structure:

```
src/
  components/
    ui/          ← shadcn/ui primitives
    Header.tsx
    Sidebar.tsx
    TaskCard.tsx
  pages/
    Home.tsx
    About.tsx
```

## Summary

Components keep your app organized and reusable. Lovable handles component creation, routing, and uses shadcn/ui for polished interfaces.
