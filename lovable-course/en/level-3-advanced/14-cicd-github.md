---
title: "CI/CD & GitHub"
weight: 14
bookToc: true
---

# CI/CD & GitHub

Connect your project to GitHub and automate deployments.

## Export to GitHub

1. Click **Export to GitHub** in your project.
2. Lovable creates a GitHub repository with all your code.
3. Every change in Lovable syncs to GitHub automatically.

## GitHub Sync

After connecting:
- Lovable pushes commits for every change.
- You can pull the repo and work locally.
- Push changes back — Lovable picks them up.

## Working Locally

```bash
git clone https://github.com/your-user/your-app.git
cd your-app
npm install
npm run dev
```

Now you can develop locally with your favorite IDE.

## CI/CD with Vercel

1. Connect your GitHub repo to [Vercel](https://vercel.com).
2. Vercel deploys automatically on every push.
3. Preview deployments for pull requests.

## CI/CD with Netlify

Similar process:
1. Connect repo to [Netlify](https://netlify.com).
2. Set build command: `npm run build`.
3. Set output directory: `dist`.

## GitHub Actions

Add automated checks:

```yaml
name: Build
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm install
      - run: npm run build
```

## Branching Strategy

| Branch | Purpose |
|--------|---------|
| main | Production code |
| develop | Integration branch |
| feature/* | New features |

## Summary

Export to GitHub for version control. Deploy with Vercel or Netlify. Use GitHub Actions for CI/CD automation.
