---
title: "Production & Scaling"
weight: 15
bookToc: true
---

# Production & Scaling

Take your app to production with confidence.

## Pre-Launch Checklist

- [ ] All features work correctly
- [ ] Authentication is secure
- [ ] RLS policies are set on all tables
- [ ] Error handling is in place
- [ ] Mobile responsive
- [ ] Custom domain configured
- [ ] SEO meta tags added

## SEO

> Add proper meta tags: title, description, and Open Graph tags for social sharing.

## Environment Variables

Keep secrets out of code:
- Supabase keys → Supabase dashboard
- API keys → Edge Function secrets
- Never commit `.env` files to GitHub

## Monitoring

Set up monitoring for your production app:

| Tool | Purpose |
|------|---------|
| Supabase Dashboard | Database metrics, auth logs |
| Vercel Analytics | Page views, web vitals |
| Sentry | Error tracking |
| UptimeRobot | Uptime monitoring |

## Scaling with Supabase

- **Database:** Supabase scales PostgreSQL automatically on paid plans.
- **Storage:** File uploads scale with your plan.
- **Edge Functions:** Auto-scale based on traffic.

## Backup

- Supabase creates daily backups on Pro plans.
- Export your GitHub repo regularly.
- Document your Supabase schema.

## Cost Planning

| Usage Level | Estimated Cost |
|------------|---------------|
| Hobby (< 1K users) | Free tier |
| Startup (< 10K users) | $25–50/mo |
| Growth (< 100K users) | $100–300/mo |

## Summary

Prepare your app for production with proper security, monitoring, and scaling. Lovable + Supabase gives you a solid foundation to grow.

Congratulations — you've completed the full course! 🎉
