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

## LinkedIn API Approval Process

### What You Need
- **API Product:** Community Management API (includes `memberCreatorPostAnalytics`)
- **OAuth Scope:** `r_member_postAnalytics`

### Hard Requirements
- Registered legal entity (LLC, Corp, etc.) — individuals without one cannot apply
- LinkedIn Company Page where you are a super admin
- Business email address (no Gmail/Yahoo)
- Professional website with published privacy policy
- Community Management API must be the **sole product** on the app (cannot mix with Sign In, Share, etc.)

### Two-Tier Process

**Tier 1 — Development (2-4 weeks to months for approval):**
1. Create a developer app at developer.linkedin.com
2. Add the Community Management API product
3. Complete the access request form (company details, use case, privacy policy URL)
4. LinkedIn reviews and approves/rejects

**Tier 2 — Standard (additional review period):**
1. Build a fully working integration on Development Tier
2. Record a screencast demo of entire OAuth flow + every declared use case
3. Provide test credentials for LinkedIn reviewers
4. Submit Standard Tier upgrade request
5. **12-month deadline** from Development approval to complete this

### Timeline and Costs
- **End-to-end timeline:** 3-6 months typical
- **API access fee:** Free (LinkedIn reserves right to charge in future)
- **Real costs:** Time, legal entity formation, development effort, compliance engineering

### Approval Odds — Honest Assessment
- **Approval rate: under 10%** across all Marketing API applications
- Rejections come with **no useful feedback**
- If rejected, **cannot reapply with same app** — must create new one
- Many applicants report **never hearing back**
- LinkedIn retains full discretion regardless of whether you meet requirements

### Data Storage Restrictions (Potential Dealbreaker)
- Member social activity data: can only be cached for **48 hours**
- Member profile data: can only be cached for **24 hours**
- Data cannot be exported, distributed, or transferred from your application
- Data cannot be combined with other data sources
- These restrictions make historical aggregated dashboards technically challenging

### Who Gets Approved?
- **Better odds:** SaaS platforms serving many LinkedIn consultants/agencies (LinkedIn wants ecosystem growth)
- **Worse odds:** Internal tools for a single consulting practice
- Approved vendors include mid-size companies (Metricool, Publer, Vista Social) — not just enterprise giants
- Positioning as a third-party analytics platform significantly improves chances

### Strategic Paths

| Path | Feasibility | Timeline |
|---|---|---|
| Build a SaaS product, apply for API | Possible (~10% approval) | 3-6 months |
| Wait for Metricool/Vista Social to ship demographic aggregation | High | Months, not years |
| Shield CSV export → Google Sheets/Looker Studio dashboard | Works today | A weekend |
| Partner with an approved vendor to request the feature | Medium | Depends on relationship |
| **Apify scraping + enrichment pipeline** | **Works today** | **A weekend + classification work** |

---

## Apify Scraping + Enrichment Approach

An alternative to the official LinkedIn API: use Apify's marketplace of LinkedIn scrapers to extract engager data, enrich profiles, and classify demographics yourself.

### The Pipeline

```
Step 1: Scrape your posts
  → harvestapi/linkedin-profile-posts (~$2/1k posts)

Step 2: Extract engagers (commenters + likers) per post
  → scraping_solutions/linkedin-posts-engagers-no-cookies (~$1.2/1k)
  → harvestapi/linkedin-post-comments (~$2/1k)

Step 3: Deduplicate by profile URL

Step 4: Enrich unique profiles
  → anchor/linkedin-profile-enrichment
  → supreme_coder/linkedin-profile-scraper (~$3/1k)
  Returns: name, headline, location, industry, experience[], education[]

Step 5: Classify demographics (custom code required)
  → Parse job title → seniority bucket (Entry/Senior/Manager/Director/VP/CxO)
  → Parse company/headline → industry category
  → Parse location → geographic region
  → LLM classifier, regex, or lookup table

Step 6: Aggregate + build client report/dashboard
```

### Cost Estimates

| Volume | Monthly Cost |
|---|---|
| Small consultant (500 engagers/mo) | ~$5/mo on free tier |
| Active consultant (2,000 engagers/mo) | ~$39-49/mo on Starter |
| Agency (10,000 engagers/mo) | ~$199-300/mo on Scale |

### Key Limitations
- **No personal profile follower lists** — follower scrapers only work for company pages with admin access. For personal profiles, you can only get engagers (commenters/likers), not followers.
- **No "seniority" field in scraped data** — LinkedIn doesn't expose this publicly. Must be inferred from job titles via classification logic.
- **Scraper reliability varies** — third-party actors break when LinkedIn changes frontend. Dependent on actor developers maintaining them.
- **LinkedIn ToS risk:** No-cookie scrapers on public data are low risk (post-hiQ v. LinkedIn ruling), but cookie-based scraping risks account restriction. For a consultant whose livelihood depends on LinkedIn presence, use no-cookie actors only.

### What You Get vs. Official API

| Data Point | Apify Pipeline | Official API |
|---|---|---|
| Individual engager profiles | Yes (name, headline, URL) | No |
| Full profile enrichment | Yes (experience, education, location) | No |
| Seniority classification | Must build yourself | LinkedIn provides natively (as %) |
| Industry classification | Must build yourself | LinkedIn provides natively (as %) |
| Location | Yes (from profile) | LinkedIn provides natively (as %) |
| Impressions / reach | No (only engagement, not views) | Yes |
| Historical data | As far back as posts exist | Limited by API retention |

### Orchestration Options
- **Apify API + Python/Node script** — most flexible
- **n8n / Make / Zapier** — Apify integration nodes, no code
- **Apify Schedules** — recurring runs with webhook triggers

---

## Late (getlate.dev)

Developer-first multi-platform social media API. Supports 11+ platforms (LinkedIn, X, Instagram, TikTok, YouTube, Threads, Reddit, Pinterest, Bluesky, etc.).

### What It Does Well
- **Impressions data:** Yes — pulls impressions, reach, reactions, comments, reshares via official LinkedIn OAuth API
- **Aggregate metrics:** Can aggregate engagement data across all posts with date range filtering
- **Multi-platform publishing:** One API call publishes to all connected platforms
- **Connectors:** Integrates with n8n, Make, Zapier for automation workflows
- **Account scale:** Supports 300+ accounts on higher tiers

### What It Does NOT Do
- **Audience demographics:** Does not surface viewer demographics (seniority, industry, location). Uses same `r_member_postAnalytics` API scope as other tools, which returns engagement counts but not demographic breakdowns.
- **Client-facing reports:** No white-label reporting, no visual dashboard designed for sharing with clients
- **Turnkey agency tool:** Developer infrastructure, not a purpose-built ghostwriting/agency platform

### Pricing
| Plan | Price | Key Features |
|---|---|---|
| Free | $0/mo | 20 posts/month, 2 profiles |
| Build | $13/mo | More posts, API access |
| Accelerate | ~$33/mo | 50 profiles, higher limits |
| Analytics add-on | +$10/mo | Required for any analytics |

### Verdict
Useful for multi-platform publishing automation and programmatic impressions data. Not a solution for aggregated audience quality demographics. The "helpful connectors for ghostwriting" refers to the n8n/Make/Zapier integrations — powerful but requires building your own workflow.

---

## Blazel

**Website:** blazel.com | **Founded:** 2024 | **HQ:** Palo Alto, CA | **Funding:** $7.3M (Recursive Ventures, Scale Asia Ventures) | **Founder:** Zain Jaffer (prev. Vungle — $400M ARR, sold for $780M)

### Public Offering
Managed LinkedIn ghostwriting service. AI agents + human marketing managers create content on your behalf. Dedicated Slack channel, monthly interview, content calendar.

### Claimed Analytics Features (from DM, not publicly documented)
1. Pull engagement metrics, filter by ICP, surface in dashboard for outreach
2. Competitor analysis — see how competitor employees rank for social, surface ICP accounts competitors talk to publicly
3. Audience mix analysis — identify ICP breakdown, company-level penetration
4. Top engagers highlighted in dashboard

### Verification Status
**None of the analytics features above are publicly documented.** No screenshots, no product demos, no G2/Capterra reviews, no Product Hunt listing. Website positions Blazel as a content service, not an analytics platform.

**However:** With $7.3M in funding, 29 employees, and "shipping new analytics every 2 weeks," these features could be in private beta or unreleased. Worth requesting a live demo to verify before committing.

---

## Social Selling / Engagement Intelligence Tools

A category of tools that frame the problem differently — not "LinkedIn analytics" but "who is engaging with your content and do they match your ICP?" These are closer to what's actually needed.

### Trigify
- **Website:** trigify.io
- **Price:** $69-549/mo
- **What it does:** Real-time LinkedIn social listening with ICP filtering. Custom ICP criteria, engagement notifications, profile enrichment, CRM/Clay/Slack integration. Monitor competitor engagement.
- **Verdict:** Strong match for ICP-filtered engagement intelligence. Verified public documentation of features.

### Letterdrop
- **Website:** letterdrop.com
- **Price:** Contact for pricing
- **What it does:** Tracks who likes, comments, follows, connects. Built-in ICP filtering on engaged accounts. Historical engagement data dashboard. Social listening with AI intent filtering. HubSpot/Salesforce/Gong integration.
- **Verdict:** Claims 63% of their pipeline is LinkedIn-driven. Strong social selling angle with documented analytics features.

### Teamfluence
- **Website:** teamfluence.com
- **Price:** Contact for pricing
- **What it does:** Detects profile visits, post commentators, likes, shares, new connections. AI checks if engagers match ICP criteria, then enriches with email/phone. Tracks competitor posts and influencer activity. HubSpot/Clay/Slack integration.
- **Verdict:** Team-level LinkedIn signal tracking with ICP matching. Worth evaluating for agencies.

### Linkbound
- **Website:** linkbound.io
- **Price:** Chrome extension (pricing TBD)
- **What it does:** Engagement dashboard with ICP filtering by job title, company, industry, location, engagement level. Multi-offer ICP intelligence. Top engagers tracking. Kanban pipeline visualization. Track up to 10 profiles.
- **Verdict:** Lightweight, closest to a turnkey solution for the original problem. Claims full LinkedIn ToS compliance.

### Comparison

| Tool | ICP-Filtered Engagement | Competitor Intel | Audience Demographics | Top Engagers | Client Reports | Price |
|---|---|---|---|---|---|---|
| Trigify | Yes | Yes | Via enrichment | Yes (real-time alerts) | TBD | $69-549/mo |
| Letterdrop | Yes | Yes (social listening) | Yes (historical) | Yes | HubSpot/Salesforce | Contact |
| Teamfluence | Yes (AI-powered) | Yes | Yes (enriched) | Yes | CRM integration | Contact |
| Linkbound | Yes | Yes (10 profiles) | Yes | Yes (kanban) | TBD | TBD |
| Blazel | Claimed, unverified | Claimed, unverified | Claimed, unverified | Claimed, unverified | Unknown | Unknown |

---

## Updated Recommendations

### Best Path for Audience Quality Demographics (Personal Profiles)

1. **Trigify, Letterdrop, or Linkbound** — productized tools with ICP-filtered engagement intelligence, documented features, and audience demographic breakdowns. Evaluate all three.
2. **Blazel** — request a live demo to verify the analytics features. If real, potentially the most complete solution (content + analytics). But unverified.
3. **Apify pipeline** — extract engagers, enrich profiles, classify with LLM. Most flexible, works today, requires technical build-out.
4. **Shield CSV export → dashboard** — aggregate Shield's per-post demographics manually. Simpler but tedious.
5. **Wait for Metricool/Vista Social** — building on the new API. Demographic aggregation features likely coming.

### Best Path for Impressions/Engagement Reporting
- **Late** or **Metricool** — both provide aggregated engagement metrics via official API

### Best Path for Multi-Platform Ghostwriting
- **Late** — API-first, supports 11+ platforms, integrates with automation tools

### Key Reframe
The original problem was framed as "LinkedIn analytics" — but the real need is **engagement-qualified audience intelligence**: who is engaging, do they match your ICP, and can you share that with clients? The social selling tools (Trigify, Letterdrop, Teamfluence, Linkbound) are closer to solving this than traditional analytics tools (Shield, Sprout Social, Metricool).

---

## Sources
- [LinkedIn Member Post Statistics API](https://learn.microsoft.com/en-us/linkedin/marketing/community-management/members/post-statistics)
- [LinkedIn Help - Recent Changes to Demographics](https://www.linkedin.com/help/linkedin/answer/a1624090)
- [Shield Analytics](https://www.shieldapp.ai)
- [AgencyAnalytics LinkedIn Integration](https://agencyanalytics.com/integrations/linkedin)
- [Sprout Social LinkedIn Analytics](https://sproutsocial.com/insights/linkedin-analytics/)
- [Metricool LinkedIn Personal Profile Analytics](https://metricool.com/press-release-metricool-launches-linkedin-analytics-for-personal-profiles/)
- [Vista Social LinkedIn Reports](https://support.vistasocial.com/hc/en-us/articles/26935050400667)
- [Community Management App Review - Microsoft Learn](https://learn.microsoft.com/en-us/linkedin/marketing/community-management-app-review)
- [Increasing Access / Tier Upgrades - Microsoft Learn](https://learn.microsoft.com/en-us/linkedin/marketing/increasing-access)
- [LinkedIn Marketing API Program Tiers - Microsoft Learn](https://learn.microsoft.com/en-us/linkedin/marketing/integrations/marketing-tiers)
- [LinkedIn API Rate Limiting - Microsoft Learn](https://learn.microsoft.com/en-us/linkedin/shared/api-guide/concepts/rate-limits)
- [Data Storage Requirements - Microsoft Learn](https://learn.microsoft.com/en-us/linkedin/marketing/data-storage-requirements)
- [Restricted Use Cases - Microsoft Learn](https://learn.microsoft.com/en-us/linkedin/marketing/restricted-use-cases)
- [LinkedIn Marketing Developer Terms](https://www.linkedin.com/legal/l/marketing-api-terms)
- [LinkedIn API Terms of Use](https://www.linkedin.com/legal/l/api-terms-of-use)
