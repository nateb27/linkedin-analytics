# LinkedIn Analytics Tools Research

## Problem Statement

Need a tool that shows **aggregated audience quality demographics** across all LinkedIn posts — not per-post, not vanity metrics — in a client-shareable format.

Specifically:
- **Where** are they? (Geographic location)
- **What level** within their company? (Seniority)
- **What industry** are they in?

Shield is the closest but only shows demographics per individual post, which is time-consuming to aggregate manually.

---

## Why This Gap Exists

1. **LinkedIn's privacy restrictions** limit demographic data to fuzzy percentages, minimum viewer thresholds, and top-5 results per category per post
2. **The Member Post Analytics API** (launched 2025) supports aggregated demographic retrieval, but approved partner tools are still building out those features
3. **Most tools** aggregate engagement metrics (impressions, likes, comments) but treat demographics as a per-post or per-follower feature

### LinkedIn Native Data Available Per Post
- Job title (top 5)
- Location (top 5)
- Industry (top 5)
- Seniority (top 5)
- Company size (top 5)
- Company (top 5)

These are shown as percentages of unique viewers per individual post — no native aggregated view exists across all content.

---

## Tool Assessment

### Shield Analytics
- **Price:** $8-25/mo (Starter to Influencer)
- **Demographics:** Available per-post via hover on pin icon in Content Overview
- **Aggregation:** Engagement metrics aggregated; demographics are per-post
- **Client reporting:** Agency dashboards available on Business plan
- **Verdict:** Best LinkedIn-specific tool, but demographics require post-by-post inspection — the exact problem we're trying to solve

### AgencyAnalytics
- **Price:** ~$79/mo
- **Demographics:** All 5 dimensions (location, seniority, company size, job function, industry)
- **Aggregation:** Yes, but primarily for **Company Pages**, not personal profiles
- **Client reporting:** White-label reports, automated scheduling, AI summaries
- **Verdict:** Best option if clients have Company Pages. Limited for personal profile analytics.

### Sprout Social
- **Price:** ~$199/mo+
- **Demographics:** Aggregated by seniority and job function
- **Aggregation:** Yes, but strongest for **Company Pages**
- **Client reporting:** Full reporting suite
- **Verdict:** Most comprehensive but expensive, and personal profile support is secondary.

### Metricool
- **Price:** ~$18/mo (free tier available)
- **Demographics:** Building on new Member Post Analytics API (integrated July 2025)
- **Aggregation:** Content metrics aggregated; demographic features still developing
- **Client reporting:** Multi-account management
- **Verdict:** Worth watching — one of the first tools on the new API. Demographic aggregation likely coming.

### Vista Social
- **Price:** ~$39/mo
- **Demographics:** Building on new Member Post Analytics API
- **Aggregation:** Still developing
- **Client reporting:** Multi-account support
- **Verdict:** Similar position to Metricool — new API integration, demographic features pending.

### AuthoredUp
- **Price:** ~$19.95/mo
- **Demographics:** Follower demographics (mirrors LinkedIn native data)
- **Aggregation:** No meaningful demographic aggregation
- **Verdict:** Primarily a content creation tool. Analytics are secondary. Does not solve this problem.

### Inlytics
- **Price:** ~$12.50/mo
- **Demographics:** Follower demographics (industries, titles, location)
- **Aggregation:** Follower-level only, not engagement/viewer level
- **Verdict:** LinkedIn-specific but shallow on demographics. Some users report LinkedIn restrictions after use.

### Taplio
- **Price:** $49-149/mo
- **Demographics:** Audience stats listed as "on roadmap" after absorbing Aware
- **Aggregation:** Not yet available
- **Verdict:** Generalist LinkedIn tool, not analytics-first. Does not solve this today.

### Hootsuite / Buffer
- **Price:** Hootsuite ~$99/mo, Buffer ~$6/mo per channel
- **Demographics:** Have API access, building features
- **Verdict:** General-purpose social management. Not built for deep LinkedIn demographic analysis.

---

## Comparison Matrix

| Tool | Audience Demographics | Aggregated Across Posts? | Personal Profiles? | Client Reports | Price |
|---|---|---|---|---|---|
| Shield | All 5 dimensions | No (per-post) | Yes | Agency dashboards | $8-25/mo |
| AgencyAnalytics | All 5 dimensions | Yes | Company Pages only | White-label | ~$79/mo |
| Sprout Social | Seniority + job function | Yes | Company Pages mainly | Full suite | ~$199/mo |
| Metricool | Building | TBD | Yes (new API) | Multi-account | ~$18/mo |
| Vista Social | Building | TBD | Yes (new API) | Multi-account | ~$39/mo |
| Inlytics | Follower only | Follower-level | Yes | Limited | ~$12/mo |
| AuthoredUp | Follower only | No | Yes | Limited | ~$20/mo |
| Taplio | Roadmap | No | Yes | Limited | $49-149/mo |

---

## Recommendations

### Right Now (Practical)
1. **Keep Shield** for ongoing analytics
2. **Export CSV from Shield** periodically → aggregate demographics in Google Sheets or Looker Studio dashboard
3. Share the dashboard/report with clients

### Near-Term (Monitor)
- **Metricool** and **Vista Social** are most likely to ship aggregated demographic dashboards for personal profiles first (both have the new API integration)

### Custom Build Option
- LinkedIn's `memberCreatorPostAnalytics` API endpoint supports aggregated demographic retrieval
- A lightweight dashboard pulling from this API would give exactly what's needed
- Challenge: requires API approval as a partner (non-trivial for individual developers)

### If Clients Have Company Pages
- **AgencyAnalytics** is the clear winner — all 5 demographic dimensions, white-label reports, automated delivery

---

## Key Insight

This is a product gap waiting to be filled. The API now supports aggregated personal profile demographics, but no tool has built a good UI around it yet. LinkedIn consultants and agencies are the obvious market. The first tool to ship "aggregated audience quality dashboard for personal profiles" wins this segment.

---

## Sources
- [LinkedIn Member Post Statistics API](https://learn.microsoft.com/en-us/linkedin/marketing/community-management/members/post-statistics)
- [LinkedIn Help - Recent Changes to Demographics](https://www.linkedin.com/help/linkedin/answer/a1624090)
- [Shield Analytics](https://www.shieldapp.ai)
- [AgencyAnalytics LinkedIn Integration](https://agencyanalytics.com/integrations/linkedin)
- [Sprout Social LinkedIn Analytics](https://sproutsocial.com/insights/linkedin-analytics/)
- [Metricool LinkedIn Personal Profile Analytics](https://metricool.com/press-release-metricool-launches-linkedin-analytics-for-personal-profiles/)
- [Vista Social LinkedIn Reports](https://support.vistasocial.com/hc/en-us/articles/26935050400667)
