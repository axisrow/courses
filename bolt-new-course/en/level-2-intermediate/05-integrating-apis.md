---
title: "Integrating External APIs"
weight: 10
bookToc: true
---

# Integrating External APIs

## What Is an API?

An API (Application Programming Interface) is a way for your app to talk to other services. For example, showing weather data, processing payments, or sending emails.

## How to Add Integrations

Simply tell Bolt what you want to connect:

> "Add a weather widget that shows the current weather for any city using a free weather API"

> "Integrate Stripe payment processing so users can pay with credit cards"

> "Add a contact form that sends emails when someone submits it"

## Popular Integrations

| Service | What It Does |
|---------|-------------|
| Stripe | Accept payments |
| Google Maps | Show maps and locations |
| SendGrid / Email | Send automated emails |
| Weather APIs | Display weather data |
| Social media | Share buttons, feeds |
| Analytics | Track visitor behavior |

## API Keys

Some services require an API key (like a password for your app). Bolt will tell you when you need one and guide you through getting it.

> "I have a Google Maps API key: ABC123. Add a map showing my business location at 123 Main Street, New York."

## Tips for Working with APIs

- **Start with free APIs** — many services have free tiers
- **Keep API keys secret** — never share them publicly
- **Handle errors gracefully** — ask Bolt to show a friendly message if an API is unavailable
- **Test thoroughly** — external services can behave differently than expected

## Real-World Example

> "Build a restaurant website with: a menu page, a reservation form that sends me an email notification, a Google Maps embed showing our location, and a reviews section that pulls from Google Reviews."

## Practice Exercise

Add a weather widget or a map to one of your existing projects. Describe clearly what service you want and where it should appear.

---

**Next level:** [Level 3 — Advanced →](../level-3-advanced/01-complex-apps.md)
