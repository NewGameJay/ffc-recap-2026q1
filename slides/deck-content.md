# 4-Slide Deck — Content (Copy/Paste Ready)

All numbers verified directly from BigQuery / source-of-truth platforms. All charts saved as PNGs in `/research/slides/`.

---

## SLIDE 1 — Meta says marketing made you money

**Headline:**
> Meta drove **$71,759 in attributed revenue** from $10,209 in ad spend (Feb 1 – Apr 30, 2026) — a blended **4.24× ROAS**.

**Bullet:**
- **Female Founders Day ad campaigns** alone delivered **$37,262 in Meta-attributed purchases** at **8.29× ROAS** on $4,492 spend (top retargeting set 8.06×, top LAL prospecting set 23.6×)
- **Cohort + other paid lanes** delivered $5,982 in directly captured revenue (plus 165 cohort applications attributed via CAPI server-side)
- **April attribution-recovery estimate: +$28,515** (the period before Jeff's CAPI rebuild went live April 28; methodology applied prior-month blended ROAS to April spend)

**Chart:** `slide1-meta.png`

**Source of truth:** Meta Ads Manager + BigQuery `facebook_ads.basic_ad_action_values` (action_type = 'purchase'); 4 different action-type aliases all sum to identical totals.

---

## SLIDE 2 — HubSpot says marketing made you money

**Headline:**
> Per HubSpot's own attribution: deal revenue is **+22% YoY** (Feb–Apr 2025 → 2026), and the **average deal value is up 75%** — MH-1 is bringing in higher-value subscribers.

**Bullet:**
- **Total HubSpot closed-won deals Feb–Apr 2026: $195,980** (up from $161,046 in 2025) — **+22% YoY**
- **Average deal value: $929** (up from $531 in 2025) — **+75% YoY**, driven by Cabinette + Lifetime cohort offerings MH-1 promoted
- **137 of 211 closed-won deals (65%) had a marketing channel MH-1 operates as a first or last touch**, totaling **$104,287** in deal revenue
- Plus **$28,934 from 54 deals** influenced by Mike's Consumer '26 sequence automation (HubSpot Sequences UI)

**Chart:** `slide2-hubspot.png`

**Source of truth:** BigQuery `female_founder_collective_hubspot.deal` filtered by `property_hs_is_closed_won = TRUE`; first/last touch attribution from HubSpot's own `property_hs_analytics_source` and `property_hs_analytics_latest_source` columns.

---

## SLIDE 3 — Chargebee says revenue is up since we started

**Headline:**
> FFC's monthly net cash collected is **up 57.9% YoY** Feb–Apr (vs. same window 2025). **April 2026 alone: $130,653 — literally 2× April 2025.**

**Bullet:**
- **Feb–Apr 2025 (pre-MH):** $174,923 net cash collected
- **Feb–Apr 2026 (MH-era):** $276,233 net cash collected — **+57.9% YoY**
- **April 2026:** **$130,653** — **2.08× the trailing-12-month average** before MH started ($61,856), **2.57× the Q4 2025 monthly average** ($50,075), **7.1× the Nov 2025 low** ($18,100)
- **231 new subscriptions** added Feb–Apr 2026, including a record **124 new subs in April alone** (more than Feb + March combined)
- **New MRR added Feb–Apr 2026: $30,224** — that's **7.4× the same period in 2025** ($4,081)
- **Cohort comparison:** Q1 2025 cohort = $25,000 vs Q2 2026 cohort = $60,343 verified — **+141% (2.41×)**

**Chart:** `slide3-chargebee.png`

**Source of truth:** BigQuery `chargebee.transaction` filtered to `type='payment' AND status='success'`, less successful refunds. Verified across 3 independent methods (transactions, invoice.amount_paid, transaction-invoice join) — all converge.

---

## SLIDE 4 — Look at this giant list of things we did for you

**Headline:**
> Beyond direct revenue, here's what's been built into FFC's program since February 1, 2026 — running for $20K/month.

**The big things (organized by impact):**

### Paid acquisition infrastructure (built by Cameron Rzonca)
- **Every Meta ad campaign** in the window — 15 ad sets across FFD, cohort, retargeting, prospecting (4.24× blended ROAS)
- **First paid LinkedIn lane** in FFC's history (CTR 0.6% — above LinkedIn benchmark of 0.2–0.3%)
- **Server-side CAPI pipeline** — Chargebee → Segment → Meta direct purchase events (Jeff Raybould, live April 28)
- **Typeform CAPI server-side tracking** — accurate cohort application attribution

### Email + lifecycle program (built by Michael DiLillo)
- **22 published marketing emails** — 151,167 sends, 11,774 opens, 311 unique clickers
- **23 new paying subscribers** acquired through clicks on MH-built emails ($15,903 cash to date / $20,156 ARR)
- **297 active workflows / 118 enabled** in the lifecycle layer (newly unblocked April 29)
- **133 automation campaigns** running in the workflow layer — onboarding, renewal nudges, re-engagement
- **Mike's Consumer '26 sequence automation** influenced 54 deals worth $28,934 (HubSpot Sequences)
- **April 27 retention email** reached 863 paying members representing $538K ARR
- **48 broken workflows audited** with ~$10K+ recoverable upside — Cancel Email Send (860 cancelling members), Expired Card recovery, Newsletter Sign Up (7,049 enrolled)

### AI-powered insights (Cameron's Lifecycle Dashboard, ffc-paid-social-hub.vercel.app)
- **Subject Line Analyzer** — found 95% open-rate lift from "Your" or first-name openers (36.94% vs 18.9%)
- **Section Heatmap** ("hotspot" analysis you asked for April 13)
- **Creative Format Winner** — AI scoring of formats
- **Topic Performance Clustering** — found 5× engagement gap between lifecycle automation and broadcast
- **AI-driven Typeform Audit** — identified 50.6% / 58.8% drop-off screens (78% of cohort funnel loss)
- **Brand voice "voice print"** for AI content generation
- **Tech stack recommendation** built leveraging AI

### 1:1 outbound (Lowella Buendia)
- **46 sales calls + 224 SMS = 5 attributable paid sign-ups** (verified Apr 30)
- **LinkedIn outreach: 83 invites, 12 accepted with first message**
- IG/social coverage when FFC team was out

### Strategy + foundational work
- **Email Industries deliverability audit** — MH brought them in (February)
- **ICP survey design + launch**
- **Brand audit + lifecycle architecture**
- **Tech stack rebuild plan** — Stripe / Chargebee / HubSpot, June 28 launch target
- **ManyChat audit + V5 plan** (Amanda)
- **Founder's Operating Manual repositioning push**

### Reporting cadence (16 written reports / recaps to Ali in 12 weeks)
- 8 weekly / bi-weekly recaps
- FFD Wrap Report + ROAS update (Cameron)
- FFC Audit Report (Email Industries)
- Tech Stack recap + follow-up
- Lifecycle dashboard shipped April 27–28
- Comprehensive paid catch-up email April 29 (Cameron)

**Link out for the full detail:** https://newgamejay.github.io/ffc-recap-2026q1/value-recap.pdf
