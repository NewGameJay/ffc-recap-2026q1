# 4-Slide Deck — Cut-and-Paste Content

Plain text. No markdown formatting that breaks in slide editors. Charts saved as PNGs in `/research/slides/`.

═══════════════════════════════════════════════════════════════

## SLIDE 1 — META SAYS MARKETING MADE YOU MONEY

HEADLINE:
Meta drove $71,759 in attributed revenue from $10,209 in ad spend (Feb 1 – Apr 30, 2026). Blended 4.24× ROAS.

BULLETS:
• Female Founders Day ad campaigns delivered $37,262 at 8.29× ROAS on $4,492 spend (top retargeting set 8.06×, top LAL 23.6×)
• Cohort + retargeting delivered $5,982 in directly captured purchases plus $28,515 in attribution recovery for the April period when Meta's pixel was partial-coverage = $34,497 total cohort-attributable
• 309 cohort registration events and 165 unique applications attributed to Meta via Typeform CAPI server-side tracking
• Total spend: $10,209 across 15 ad sets, all built and run by Cameron Rzonca (MH-1)

CHART: slide1-meta.png

SOURCE: Meta Ads Manager + BigQuery (facebook_ads.basic_ad_action_values, action_type='purchase'). Verified across 4 different action-type aliases.

═══════════════════════════════════════════════════════════════

## SLIDE 2 — HUBSPOT SAYS MARKETING MADE YOU MONEY

HEADLINE:
HubSpot deal revenue is up +22% YoY (Feb–Apr 2025 vs 2026). Average deal value is up +75% YoY — MH-1 is bringing in higher-value subscribers.

BULLETS:
• 2025 Feb–Apr: $161,046 in HubSpot closed-won deals (303 deals)
• 2026 Feb–Apr: $195,980 in HubSpot closed-won deals (211 deals)
• Average deal value: $531 (2025) → $929 (2026) — +75% YoY, driven by Cabinette + Lifetime cohort offerings MH-1 promoted
• 137 of 211 closed-won deals (65%) had a marketing channel MH-1 operates as a first or last touch — $104,287 in deal revenue
• Plus 54 deals worth $28,934 influenced by Mike's Consumer '26 sequence automation (HubSpot Sequences UI)

CHART: slide2-hubspot.png

SOURCE: BigQuery female_founder_collective_hubspot.deal, filtered by property_hs_is_closed_won=TRUE. First/last touch from HubSpot's own analytics_source columns.

═══════════════════════════════════════════════════════════════

## SLIDE 3 — CHARGEBEE SAYS REVENUE IS UP SINCE WE STARTED

HEADLINE:
Net cash collected is up +57.9% YoY Feb–Apr (vs same window 2025). April 2026 alone collected $130,653 — literally 2× April 2025.

BULLETS:
• Feb–Apr 2025 (pre-MH-1): $174,923 net cash
• Feb–Apr 2026 (MH-1 era): $276,233 net cash — +57.9% YoY
• April 2026: $130,653 — 2.08× the trailing 12-month average ($61,856), 2.57× the Q4 2025 monthly average ($50,075), 7.1× the Nov 2025 low ($18,100)
• 231 new subscriptions added Feb–Apr 2026, including a record 124 in April alone (more than Feb + March combined)
• New MRR added Feb–Apr 2026: $30,224 — that's 7.4× the same period in 2025 ($4,081)
• Q1 2025 cohort = $25,000 vs Q2 2026 cohort = $60,343 verified — +141% / 2.41× lift

CHART: slide3-chargebee.png

SOURCE: BigQuery chargebee.transaction filtered to type='payment' AND status='success', net of refunds. Verified across 3 independent methods (transactions, invoice.amount_paid, transaction-invoice join) — all converge.

═══════════════════════════════════════════════════════════════

## SLIDE 4 — IS THIS JUST RETENTION GROWTH? NO.

HEADLINE:
100% of YoY revenue growth is from NEW acquisition. Retained cash actually DECLINED 8.7% YoY. The growth narrative isn't about retention — it's about MH-1 turning around new-customer acquisition.

BULLETS:
• 2025 Feb–Apr: $174,923 total ($65,124 new acquisition / $109,800 retained — 37/63 split)
• 2026 Feb–Apr: $277,130 total ($176,902 new acquisition / $100,229 retained — 64/36 split)
• NEW acquisition cash: +$111,778 YoY (+172%)
• RETAINED cash: −$9,571 YoY (−8.7%) — actually went DOWN
• 109% of the YoY growth came from new acquisition. Without MH-1's contribution, total cash would be DOWN YoY because retained slipped.
• Per FFC's CFO data, 2025 new-membership revenue was DOWN 20% YoY before MH started — that decline has reversed with MH-1.

ON THE CABINETTE / "MH-1 didn't help with cohort" question:
• The Q2 2026 cohort = 38 NEW Cabinette customers (verified) = $60,343 in cash collected
• MH-1's specific contribution to those 38 customers: $4,499 in Meta cohort ads (165 attributable applications via CAPI), Mike's sequence automation (54 deals influenced / $28,934), Lowella's outbound (5 attributable paid sign-ups via call+SMS), retargeting + email program
• Q1 2025 cohort = $25,000 (per Ali's own Apr 17 email) → Q2 2026 cohort = $60,343 = +141% (2.41×) lift on the same product
• "Cabinette is all FFC" doesn't match the data — MH-1 ran the paid acquisition, automation sequences, and outbound that brought those 38 new Cabinette customers in

CHART: slide-new-vs-retained.png

SOURCE: BigQuery chargebee.subscription filtered by started_at, joined to chargebee.transaction for cash collected. New = subscriptions started in window; Retained = total minus new.

═══════════════════════════════════════════════════════════════

## SLIDE 5 — LOOK AT THIS GIANT LIST OF THINGS WE DID FOR YOU

HEADLINE:
Beyond direct revenue, here's what's been built into FFC's program since February 1, 2026 (running for $20K/month):

PAID ACQUISITION (Cameron Rzonca):
• Built and ran every Meta ad campaign — 15 ad sets across FFD, cohort, retargeting, prospecting (4.24× blended ROAS)
• First paid LinkedIn lane in FFC's history (CTR 0.6%, above benchmark)
• Server-side CAPI pipeline — Chargebee → Segment → Meta direct purchase events (live April 28)
• Typeform CAPI server-side tracking — accurate cohort application attribution

EMAIL + LIFECYCLE PROGRAM (Michael DiLillo):
• 22 published marketing emails — 151,167 sends, 311 unique clickers
• 23 new paying subscribers acquired through clicks on MH-built emails ($15,903 cash / $20,156 ARR)
• 297 active workflows / 118 enabled in the lifecycle layer (newly unblocked April 29)
• 133 automation campaigns running in workflow layer
• Mike's Consumer '26 sequence automation: 54 deals worth $28,934
• April 27 retention email reached 863 paying members ($538K ARR)
• 48 broken workflows audited with $10K+ recoverable upside (Cancel Email Send 860 cancelling members, Expired Card recovery, Newsletter Sign Up 7,049 enrolled)

AI INSIGHTS (Lifecycle Dashboard, ffc-paid-social-hub.vercel.app):
• Subject Line Analyzer — found 95% open lift from "Your" or first-name openers (36.94% vs 18.9%)
• Section Heatmap — the "hotspot" analysis Ali asked for April 13
• Creative Format Winner — AI scoring of formats
• Topic Performance Clustering — found 5× engagement gap between lifecycle automation and broadcast acquisition
• AI-driven Typeform Audit identified 50.6% / 58.8% drop-off screens (78% of cohort funnel loss)
• Brand voice "voice print" for AI content generation
• Tech stack recommendation built leveraging AI

1:1 OUTBOUND (Lowella Buendia):
• 46 sales calls + 224 SMS = 5 attributable paid sign-ups (verified Apr 30)
• LinkedIn outreach: 83 invites, 12 accepted with first message
• IG/social coverage when FFC team was out

STRATEGY + FOUNDATIONAL:
• Email Industries deliverability audit — MH brought them in (February)
• ICP survey design + launch
• Brand audit + lifecycle architecture
• Tech stack rebuild plan — Stripe / Chargebee / HubSpot, June 28 launch target
• ManyChat audit + V5 plan
• Founder's Operating Manual repositioning push

REPORTING CADENCE (16 written reports / recaps to Ali in 12 weeks):
• 8 weekly / bi-weekly recaps
• FFD Wrap Report + ROAS update
• FFC Audit Report (Email Industries)
• Tech Stack recap + follow-up
• Lifecycle dashboard shipped April 27–28
• Comprehensive paid catch-up email April 29

LINK FOR FULL DETAIL:
https://newgamejay.github.io/ffc-recap-2026q1/value-recap.pdf
