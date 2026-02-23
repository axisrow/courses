---
title: "Tracks and Conditions"
weight: 1
bookToc: true
---

# Tracks and Conditions

## What Are Tracks?

Tracks let users choose a project type when starting a workflow. Based on the choice, different steps may be included or excluded.

```javascript
export default {
  name: 'Web App Builder',
  tracks: {
    question: 'What type of web application?',
    options: {
      spa: { label: 'Single Page App', description: 'React/Vue/Angular SPA' },
      ssr: { label: 'Server-Side Rendered', description: 'Next.js/Nuxt.js' },
      static: { label: 'Static Site', description: 'HTML/CSS/JS only' },
    },
  },
  steps: [
    resolveStep('researcher'),
    resolveStep('spa-setup', { tracks: ['spa'] }),      // Only for SPAs
    resolveStep('ssr-setup', { tracks: ['ssr'] }),      // Only for SSR
    resolveStep('static-setup', { tracks: ['static'] }), // Only for static
    resolveStep('deployment'),                            // For all tracks
  ],
};
```

## Condition Groups

Conditions are like feature flags — users select options that affect which steps run and what context agents receive.

```javascript
conditionGroups: [
  {
    id: 'features',
    question: 'Which features do you need?',
    multiSelect: true,
    conditions: {
      auth: { label: 'Authentication', description: 'Login/signup system' },
      payments: { label: 'Payments', description: 'Stripe integration' },
      notifications: { label: 'Notifications', description: 'Email/push alerts' },
    },
  },
],
```

## Nested Conditions

Conditions can have children — follow-up questions based on selections:

```javascript
children: {
  auth: {
    question: 'What auth method?',
    multiSelect: false,
    conditions: {
      oauth: { label: 'OAuth', description: 'Google/GitHub login' },
      email: { label: 'Email/Password', description: 'Traditional login' },
    },
  },
},
```

## Combining Tracks and Conditions

```javascript
conditionGroups: [
  {
    id: 'database',
    question: 'Which database?',
    multiSelect: false,
    tracks: ['spa', 'ssr'],  // Only ask for SPA and SSR projects
    conditions: {
      postgres: { label: 'PostgreSQL' },
      mongodb: { label: 'MongoDB' },
    },
  },
],
```

## Using Conditions in Steps

```javascript
resolveStep('setup-postgres', { conditions: ['postgres'] }),
resolveStep('setup-mongodb', { conditions: ['mongodb'] }),
```

## Summary

- Tracks let users choose project types
- Conditions act as feature flags
- Nested conditions ask follow-up questions
- Combine tracks and conditions for flexible workflows
- Steps can be filtered by tracks and conditions

> **Next lesson:** Context engineering — controlling what each agent sees.
