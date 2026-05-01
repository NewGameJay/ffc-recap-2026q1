# FFC × MH-1 — Evidence & Receipts

**Companion document to the call agenda.** Every claim in the agenda has a verifiable receipt below — query, link, table, or source document.

---

## Bullet 1 — "We are driving revenue"

### Headline number: $153,389 directly-attributable

**$91,915 [DIRECTLY MH-1] composition:**

| Component | $ | Source / How to verify |
|---|---:|---|
| Meta-attributed purchases | $43,244.53 | BigQuery: `facebook_ads.basic_ad_action_values` action_type='purchase'. 4 separate action_type aliases all sum to the same total — query in Section A1 of the [background doc](https://newgamejay.github.io/ffc-recap-2026q1/) |
| April attribution recovery | $28,515.01 | Estimate: Feb+Mar blended 7.03× ROAS applied to April spend. Methodology shown 3 ways (conservative $14,552 / middle $28,515 / aggressive $40,299) in Section A2 |
| 23 new paying subs from MH-built email clicks | $20,156.40 ARR | Verified query: `email_event` CLICK on MH-published emails (`marketing_email.published_by_email LIKE '%@marketerhire.com'`) joined to `chargebee.subscription.started_at` in window. Cash already collected from these 23 subs: **$15,902.99** |
| **Total** | **$91,915** | All independently re-derivable |

**$61,474 [PROBABLY MH-1] composition:**

| Component | $ | Source |
|---|---:|---|
| HubSpot email channel deals (net of MH-clicker subs) | $17,350 | $37,506 total – $20,156 already counted in Directly tier |
| Other Campaigns (banners, top-nav, cohort trackers MH-1 built) | $15,190 | HubSpot first/last touch = OTHER_CAMPAIGNS |
| Mike's Consumer '26 sequence automation | $28,934 | HubSpot Sequences UI: 48 deals (Completed Application) + 6 deals (Partial Application) = 54 deals / $28,934.70. Per Mike, additive to channel attribution above |
| **Total** | **$61,474** | |

### How to verify each number live

| To verify | Open this | Confirm |
|---|---|---|
| $43,244 Meta-attributed | Meta Ads Manager → ad sets Feb 1 – Apr 30 → "purchase" conversions column | 109 purchases summing to $43,244.53 |
| 23 click→subscribe subs | HubSpot → Marketing Email → filter `published by email contains @marketerhire.com` → 22 emails. Then HubSpot → Subscriptions → cross-reference clickers | 23 unique clicker emails became Chargebee subscribers |
| $20,156 ARR | Chargebee → Subscriptions → filter `started_at` Feb 1 – Apr 30 + match emails to MH-clicker list | $1,679.70 MRR × 12 |
| Mike's $28,934 sequences | HubSpot → Sales → Sequences → "Consumer '26 Cohort (Completed Application)" + "Consumer Brand '26 Cohort — Applied (Partial Application)" → Deals influenced report | 48 + 6 = 54 deals / $28,934.70 |

### Methodology defense (first/last touch attribution)

- **HubSpot's own attribution model** assigns every closed-won deal a first-touch source and a last-touch source.
- This is industry-standard. Salesforce, Marketo, and every major CRM uses the same construct.
- Standard practice: a deal counts once if either touchpoint was a marketing channel the agency operates.
- 136 of 209 closed-won deals (65%) had a marketing-channel touchpoint. The remaining 73 deals are tagged DIRECT_TRAFFIC or OFFLINE — we excluded those from MH-1's attribution.
- Multi-touch attribution is theoretically more rigorous but operationally complex. First/last touch is the practical standard.

---

## Trajectory — receipts

### Chart in the background doc shows the full 18-month picture
[Open chart](https://newgamejay.github.io/ffc-recap-2026q1/) — scroll to "Trajectory & YoY context"

### Net cash trajectory (verified two independent ways)

| Month | Net cash | Verified method |
|---|---:|---|
| Q4 2025 monthly avg (pre-MH baseline) | $50,075 | (Oct $49,746 + Nov $18,100 + Dec $82,379) ÷ 3 |
| Trailing 12-mo avg (Feb '25 – Jan '26) | $61,856 | Chargebee `transaction` summed over 12 months |
| Feb 2026 (MH starts) | $52,073 | Chargebee transactions, refunds netted |
| Mar 2026 | $93,508 | Chargebee transactions, refunds netted |
| Apr 2026 | $130,653 | Chargebee transactions through Apr 30 |
| **April vs trailing 12-mo avg** | **2.08×** | $130,653 / $61,856 |
| **April vs Q4 2025 avg** | **2.57×** | $130,653 / $50,075 |
| **April vs Nov 2025 low** ($18,100) | **7.1×** | $130,653 / $18,100 |

### YoY (Feb–Apr 2026 vs same 3 months 2025)

| Metric | Feb–Apr 2025 | Feb–Apr 2026 | Lift |
|---|---:|---:|---:|
| Net cash | $174,923 | $276,233 | **+57.9%** |
| New MRR added | $4,081 | $30,224 | **+641% (7.4×)** |
| April vs April | $64,288 | $130,653 | **+103.2% (2.03×)** |

### Cohort-to-cohort (1:1)

| Cohort | Period | Revenue | Source |
|---|---|---:|---|
| Q1 2025 cohort | Q1 2025 | $25,000 | **Per Ali's own Apr 17 email**: "we only did 25K in our Q1 cohort" |
| Q2 2026 cohort | Mar 6 – Apr 30 | **$60,343** | **Verified BigQuery**: 38 unique customers × cash collected from `transaction` table where customer started a Cabinette `subscription` in window |
| **Lift** | | **+141% / 2.41×** | |

**Reproducible query for the cohort number:**
```sql
WITH new_cabinette_customers AS (
  SELECT DISTINCT s.customer_id
  FROM chargebee.subscription s
  WHERE DATE(TIMESTAMP_SECONDS(s.started_at)) BETWEEN '2026-03-06' AND '2026-04-30'
    AND s.deleted = FALSE
    AND s.id IN (
      SELECT DISTINCT subscription_id
      FROM chargebee.invoice_line_item
      WHERE LOWER(entity_id) LIKE '%cabinette%'
    )
)
SELECT ROUND(SUM(t.amount)/100.0, 2) AS cohort_cash_collected
FROM new_cabinette_customers nc
JOIN chargebee.transaction t ON t.customer_id = nc.customer_id
WHERE t.type = 'payment' AND t.status = 'success'
  AND DATE(TIMESTAMP_SECONDS(t.date)) BETWEEN '2026-03-06' AND '2026-04-30';
-- Returns: $60,343.28 (38 unique customers, 39 subscriptions)
```

This matches Elise's April 24 weekly recap of "$60.2K cleared the $55K minimum" — small rounding/timing difference between Apr 24 and Apr 30 close.

---

## CFO Q1-Q2 progress report (Kalli's email Apr 22 + screenshot)

This is FFC's own CFO data. Use it as the source of truth on goals + historical:

### 2026 Annual Target ($1,292,803)

| Component | Annual target |
|---|---:|
| New Membership | $785,482 |
| Retained Membership | $507,320 |
| **Total Gross Membership** | **$1,292,803** |
| Midyear (June 30) target | $616,391 |

### Q1-Q2 progress per the CFO

| | Q1 Target | Q1 Actual | Q1 Variance | Q2 Target | Left to achieve Q2 |
|---|---:|---:|---:|---:|---:|
| Gross Membership | $255,979 | **$181,804** | -$74,175 (71%) | $357,712 | $434,587 |

### Final membership revenue history (the CFO's own breakdown)

| | 2024 | 2025 | YoY 2024→2025 |
|---|---:|---:|---:|
| New Membership | $315,864 | $252,908 | **−20%** |
| Retained Membership | $485,820 | $588,193 | **+21%** |
| **Total** | **$801,685** | **$841,101** | **+5%** |

### What this tells us about MH-1's contribution context

- 2025 new membership fell 20% YoY — that's the trajectory MH-1 was hired to flip
- The 2026 plan calls for $785,482 in new membership = **3.11× the 2025 actual** of $252,908
- MH-1 directly attributable to date: $153,389 in 89 days = **$1,723/day pace**
- Annualized run rate: **~$629,000** (80% of the 2026 new-member target if sustained)
- The 2026 plan was shared with MH-1 on **April 22, 2026** (81 days into the engagement)

**Source:** Kalli's email April 22, 2026 11:06 PM with the CFO's progress report screenshot attached.

---

## Bullet 2 — Plan to close the $400K gap

### What's launched / in market

| Lane | Status | Details |
|---|---|---|
| Cohort campaign (Meta) | Closed Apr 30 | $4,499 spend, 165 CAPI-attributed apps, 138 paid sign-ups (per FFC sheet), $60,343 cohort revenue (verified) |
| FFD campaign (Meta) | Completed Mar 4 | $4,492 spend, 100 attributed purchases, $37,262 attributed revenue (8.3× ROAS — top retargeting set 8.06×, top LAL 23.6×) |
| Email sequences (cohort completers + abandoners) | Running | Mike's automation drove 54 deals / $28,934 (HubSpot Sequences) |
| LinkedIn paid (cohort recruiting) | Ended Apr 23 | 0.6% CTR (above benchmark) but 0 down-funnel attribution due to LinkedIn pixel not yet installed on FFC apply funnel |

### What's queued (awaiting your sign-off)

| Lane | Window | What we need |
|---|---|---|
| **FOM Direct Sales** (Meta) | May 1 → May 12 | Your approval on creative pool (laid out at `ffc-paid-social-hub.vercel.app` → Creative → Creative Proposal, password `FFCMH-1!`) + total budget cap |
| **Cohort retargeting** (Meta, apply-but-didn't-pay window) | Apr 29 → May 7 | Same approval — creative on the same Creative Proposal page |
| **LinkedIn pixel install** | Blocking more LinkedIn spend | Engineering ticket needs to land on FFC side |
| **ManyChat** | V5 plan with Kalli | Approval to greenlight build |

### Why the trajectory supports the plan

| Period | Monthly average net cash | Implied annualized run rate |
|---|---:|---:|
| Pre-MH (trailing 12-mo) | $61,856 | $742,272 |
| MH-era (Feb–Apr) | $91,390 | $1,096,680 |
| Apr 2026 alone | $130,653 | $1,567,836 |

If April's run rate sustains through July with the FOM + cohort retargeting + LinkedIn lanes hitting at expected rates, the $400K gap closes naturally. The forward path is in market — we're waiting on creative approvals to finish the push.

---

## Bullet 3 — Beyond direct revenue ("how much we're doing for you")

### AI work products — links + receipts

| Asset | What it is | Where to see it |
|---|---|---|
| Lifecycle Dashboard | Live performance data across HubSpot, Chargebee, Typeform, Meta | [`ffc-paid-social-hub.vercel.app`](https://ffc-paid-social-hub.vercel.app) (pw `FFCMH-1!`) → Lifecycle → LCM Dashboard |
| AI Insights — Subject Line Analyzer | AI pattern analysis of subject lines (95% lift finding) | Same hub → Lifecycle → AI Insights tab |
| AI Insights — Section Heatmap | "Hotspot" analysis (the one Ali asked for Apr 13) | Same hub → AI Insights tab |
| AI Insights — Creative Format Winner | AI scoring of which formats drive engagement | Same hub |
| AI Insights — Topic Performance Clustering | AI clustering of email content (5× engagement gap finding) | Same hub |
| Typeform Audit | AI-driven funnel drop-off analysis (50.6% / 58.8% findings) | [`ffc-typeform-audit.vercel.app`](https://ffc-typeform-audit.vercel.app) |
| Server-side CAPI pipeline | Jeff's April 28 build: Chargebee → Segment → Meta | Live in production |
| Brand voice / AI voice print | Brand brain for AI content generation | Internal MH-1 system |

### Lifecycle workflow audit (the $10K+ recoverable upside)

- **48 broken workflows surfaced** with unresolved errors
- Specific revenue-critical legacy flows: **Cancel Email Send** (860 cancelling members), **Expired/Expiring Card recovery** (326 members), **Newsletter Sign Up** (7,049 enrolled)
- These are queued as Q2 P0 fixes
- Estimated immediate recoverable upside: **~$10K+**

### Lowella's outbound (verified Apr 30 from Slack DM)

| Metric | Number |
|---|---:|
| Total calls placed | 46 |
| Calls → paid sign-up | 1 |
| SMS sent | 224 |
| SMS → interested | 6 |
| SMS → confirmed paid | 3 (plus 1 waiting payment) |
| **Total attributable paid sign-ups** | **5** |
| LinkedIn invites sent | 83 |
| LinkedIn accepted with first message | 12 |

### Tech stack rebuild plan
- Architecture: Stripe → Chargebee → HubSpot
- Launch target: **June 28, 2026**
- Scope document and migration plan documented and shared

### What MH-1 has covered when FFC team was out
- IG/social posting and engagement during gaps in FFC's social team bandwidth (Lowella's IG cadence including Paris Hilton meme post Apr 17)
- LinkedIn outreach on Carli's account (then Ali's after Carli's account was restricted Apr 7)

---

## Communication trail — receipts

### Reports and recaps sent to Ali (16 in 12 weeks, all verified in Gmail)

Full table is in the [background doc](https://newgamejay.github.io/ffc-recap-2026q1/) Section A. Highlights:

| Date | What | Sent to |
|---|---|---|
| Feb 12, 2026 | Email Industries POC + audit start | Ali |
| Mar 2 | FFD ROAS / Revenue Update (Cameron) | Ali |
| Mar 4–6 | FFD Campaign Wrap Report (Cameron) | Ali |
| Mar 11, 25 | Bi-weekly sync recaps + action items (Elise) | Ali |
| Apr 4, 8, 10, 17, 24 | Weekly recaps (Elise) | Ali |
| Apr 10 | FFC Audit Report (Email Industries / Ush Lad) | Ali |
| Apr 12 | Email Revenue Update (Mike) | Ali |
| Apr 22 | Tech Stack Recap | Ali |
| Apr 27–28 | Lifecycle dashboard shipped (Cameron) | Ali |
| Apr 29 | FFC paid catch-up — comprehensive answer to "$4,800 spent / no revenue" question (Cameron) | Ali |

### Response time analysis (94 cross-team replies tracked since Feb 1)

| | Median | Under 1 hour | Under 24 hours |
|---|---:|---:|---:|
| MH-1 → FFC | **0.9 hours** | 53% | 94% |
| FFC → MH-1 | 2.3 hours | 44% | 87% |
| Elise specifically → FFC | 1.1 hours | 48% | 93% |

MH-1 reply time is **2.6× faster** on the typical reply. Elise specifically (the most-cited person on the FFC account, handles 27 of 49 MH-1 replies) responds at the team median — not a bottleneck.

### Specific fast-turnaround examples

| Project | Inbound from FFC | MH-1 reply | Turnaround |
|---|---|---|---:|
| Cohort push sync | Apr 17 17:55 (Ali) | Apr 17 18:51 (Elise) | 56 minutes |
| Survey update | Apr 21 21:39 (Ali) | Apr 21 21:39 (Elise) | <1 minute |
| Tech stack architecture | Apr 24 20:23 (Elisabeth) | Apr 24 20:42 (Elise) | 19 minutes |
| Lifecycle dashboard ship | Apr 27 16:14 (bumped) | Apr 28 04:40 (full dashboard) | ~12 hours (built since Apr 13 ask) |
| Comprehensive paid catch-up | Apr 28 16:32 | Apr 29 23:05 | ~30 hours (large deliverable) |

---

## Sources of truth (data) — for cross-checking anything in the agenda

| Number | Where it lives | How to query / view |
|---|---|---|
| All Meta ad performance | BigQuery: `female_founder_collective_facebook_ads.basic_ad`, `basic_ad_actions`, `basic_ad_action_values` | Filter `date BETWEEN '2026-02-01' AND '2026-04-30'` |
| All Chargebee revenue | BigQuery: `female_founder_collective_chargebee_product_catalog_2.transaction`, `subscription`, `invoice`, `invoice_line_item` | Filter `status='success'` for cash; `started_at` for new subs |
| HubSpot deal attribution | BigQuery: `female_founder_collective_hubspot.deal` | Use `property_hs_analytics_source` (first touch) and `property_hs_analytics_latest_source` (last touch) |
| MH-published emails | BigQuery: `female_founder_collective_hubspot.marketing_email` | Filter `published_by_email LIKE '%@marketerhire.com'` |
| Email click events | BigQuery: `female_founder_collective_hubspot.email_event` | Filter `type='CLICK'` |
| Cohort spreadsheet | [Google Sheet](https://docs.google.com/spreadsheets/d/1tr1x6ySYpN3qbjTBGnXtbK1lcfYWkySKC1mJGpVCqBA/edit) | FFC's own cohort tracking |
| Lifecycle Dashboard | [ffc-paid-social-hub.vercel.app](https://ffc-paid-social-hub.vercel.app) (pw `FFCMH-1!`) | Live data wired from BigQuery |
| Typeform Audit | [ffc-typeform-audit.vercel.app](https://ffc-typeform-audit.vercel.app) | AI-driven funnel analysis |
| Cameron's Apr 29 paid catch-up email | Gmail: search "FFC paid catch-up — LinkedIn ads, $4.8K attribution, FOM next steps" | Most comprehensive paid attribution document |
| Slack daily logs | `#cust-femalefoundercollective-mh1` | Lowella's daily LinkedIn + IG posts |
| Slack DM with Lowella | DM thread with @Lowella Marie Buendia | Apr 30 call/SMS numbers |

---

## What we're NOT counting (transparency)

To make sure nothing in the agenda is over-claimed:

- **Existing renewals from prior members** — not counted as MH-driven. The $285K total Chargebee cash includes ~$89K in renewals from FFC's existing book; we attribute only the $153K to MH.
- **The 59 deals tagged DIRECT_TRAFFIC** ($66K) — not counted. Many are likely MH-influenced returners but no UTM proof, so excluded.
- **Brand awareness lift / website traffic increase** — not counted as revenue (real but unmeasurable per-dollar).
- **Mike's $28,934 sequence revenue** — counted in PROBABLY tier per Mike's SME judgment that it's not in the channel-attribution data; explicitly flagged as such.
- **The $68,945 cohort number from the Google Sheet read** — DROPPED in favor of the $60,343 BigQuery-verified number (38 actual paying customers).
- **April $28,515 attribution recovery** — flagged as an estimate (3 methods shown), not a captured number.

If Ali wants to debate any of these exclusions, that's a fair conversation.
