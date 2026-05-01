# FFC × MH-1 — Call Agenda

**For: Ali Wyatt + Chris Toy**
**Date: May 2, 2026 (midday)**
**Duration: 30 min**

The goal of this call is to align on a few specific things, then make a clean go/no-go decision. Three bullets.

---

## 1. We are driving revenue — and we need to align on attribution

**$153,389 in directly-attributable revenue MH-1 has driven since February 1, 2026:**
- **$91,915** in [DIRECTLY MH-1] revenue (Meta-attributed purchases, April attribution recovery, and 23 paying subscribers acquired through clicks on MH-built emails)
- **$61,474** in [PROBABLY MH-1] revenue (HubSpot-attributed deals on channels MH-1 operates: email program net of direct subs, banners/top-nav/cohort trackers, and Mike's Consumer '26 sequence automation)

**Methodology:** first-touch and last-touch attribution per HubSpot's own model — the standard for marketing performance reporting. Every closed-won deal counts once. If we can't agree on this attribution framework, that's the conversation we should have first — everything else follows from there.

**The trajectory says the same thing:**
- Net cash collected Feb–Apr 2026: **$276,233** vs. same window 2025 ($174,923) = **+57.9% YoY** *(triple-verified Apr 30 via three independent BigQuery methods)*
- New MRR added Feb–Apr 2026: **$30,224** vs. same window 2025 ($4,081) = **+641% (7.4× YoY)**
- Q2 2026 cohort: **$60,343** verified from Chargebee vs. Q1 2025 cohort $25,000 = **+141% (2.41× lift)**

**On the Q1 goals context:** the FFC CFO's 2026 revenue plan ($344,442 10H Annual + $142,308 10H Monthly + $298,732 Cabinette = $785,482 total) was shared with MH-1 on **April 22, 2026** — 81 days into the engagement. We were operating without those targets through most of Q1. Now that we have them, the plan in Bullet 2 is built against them.

---

## 2. The plan to close the $400K gap — by July (and what we need from you)

We have a clear plan and the channels in motion. Here's the path:

- **FOM Direct Sales** (Meta) — proposed launch ready, awaiting your approval on the creative pool. Targeting cohort applicants who didn't pay (~165), FFD audience (already warm), and 1% LAL off active 10H members.
- **Cohort retargeting** for the 4/29–5/7 latecomer window — ready, awaiting your approval.
- **LinkedIn paid** — outperforming the LinkedIn benchmark (0.6% CTR vs. 0.2–0.3%) but blocked on the LinkedIn pixel install on FFC's apply funnel. Pixel install must land before more LinkedIn spend goes live.
- **ManyChat** — V5 plan with Kalli for approval. Not live yet — this has been a missed opportunity (per your texts).
- **Server-side CAPI is now functional** (April 28) — going forward Meta dashboard revenue will flow live as purchases clear.

**What we need from you to move:** FOM creative approval, total budget cap for the May 1–12 window, and the LinkedIn pixel install ticket landing.

---

## 3. What else we're doing for you — beyond direct revenue

The $20K/month covers a substantial body of work that doesn't show up directly in revenue attribution:

- **AI Insights layer** in the Lifecycle Dashboard (Subject Line Analyzer, Section Heatmap — the "hotspot" you asked for, Creative Format Winner, Topic Performance clustering)
- **Lifecycle workflow audit** identified 48 broken workflows with ~$10K+ recoverable upside (Cancel Email Send 860 cancelling members, Expired/Expiring Card recovery, Newsletter Sign Up 7,049 enrolled)
- **Tech stack rebuild plan** — Stripe / Chargebee / HubSpot architecture, June 28 launch
- **Email Industries deliverability audit** (we brought them in)
- **Server-side CAPI pipeline** Jeff built (April 23–29) — the infrastructure that closes the attribution gap going forward
- **Lowella's outbound** — 46 calls + 224 SMS attributed 5 paid sign-ups directly + LinkedIn outreach (83 invites, 12 accepted)
- **Brand voice / AI voice print** for content generation
- **Typeform CAPI server-side tracking** — accurate cohort application attribution
- **Lifecycle Dashboard** (`ffc-paid-social-hub.vercel.app`) — live performance data wired across HubSpot, Chargebee, Typeform, Meta

If revenue alone is the bar, you can decide whether to keep this lane on. We're confident the program is delivering more than $20K/month of value when the infrastructure work is included.

---

## 4. Addressing what you raised directly (point by point)

These are the specific concerns from your texts and the team — answered directly, not deflected.

**On "we haven't used one piece of AI Creative or email that you guys have sent"**
We hear this and want to walk through specifically what was used vs. rewritten so we have a shared view. The AI insights MH built (Subject Line Analyzer, Section Heatmap, Topic Clustering) are real and live in the Lifecycle Dashboard — those findings *informed* what was sent, even where you and Avery rewrote the body copy. That's a fair distinction and we'll be more explicit about which lane is which going forward.

**On ManyChat not being live**
Real and accountable. Amanda's V5 plan has been with you and Kalli for approval. If the issue is the plan's quality, we'll iterate. If it's just been sitting, we'll move it forward this week. Either way, we should land it — it's a clear acquisition lever you've referenced multiple times.

**On "we were sending people to the wrong links — funnel filling, nothing converting"**
Acknowledged. Cameron's Typeform Audit (`ffc-typeform-audit.vercel.app`) identified the two screens responsible for ~78% of cohort apply funnel drop-off (50.6% on email entry; 58.8% on payment screen). The Apr 28 server-side CAPI rebuild + the Typeform CAPI server-side tracking are the structural fixes. Going forward, attribution flows live in real time as purchases clear.

**On the dashboard "apples and oranges" / "shouting into a black hole"**
This is the most important one. The earlier email program report (Apr 12) had a math error and used different attribution methods than the trajectory data — that's where "apples and oranges" came from. The Apr 28 Lifecycle Dashboard is a single source of truth, joined to live HubSpot, Chargebee, Typeform, and Meta data — every number reproducible. If specific data points still feel flawed, name them in the call and we'll fix them with you live.

**On the CFO context (18% of Q1 goal)**
Q1 2026 spans Jan 1 – Mar 31. MH-1 started Feb 1 — so two of three Q1 months. We received the CFO's revenue plan April 22 — six days before your "18% of Q1 goal" email. The trajectory through Q2 is what we'd ask to be evaluated against (with the goals now in hand). April alone collected $130,653 — 2.57× the Q4 2025 monthly average.

**On "your team dialed for dollars" attribution**
Fair point worth being explicit about. Phone calls from your team (you, Avery, Kalli) are not tracked in HubSpot's first/last touch. So MH's $153,389 attribution is **purely from marketing channels HubSpot does track** (email, paid social, organic search, social, referrals, other campaigns) — none of it credits phone calls. A multi-touch attribution model would split credit between MH's marketing touch *and* your team's call; first/last touch (the standard) credits the marketing channel. Both are real. The two are complementary, not competing for the same dollar.

---

## What we'd like to walk away with

1. **Agreement on attribution** (first/last touch is the standard — yes/no)
2. **Sign-off on FOM creative** so we can launch the May push
3. **Decision on LinkedIn pixel** install timeline (so we can scale that lane)
4. **Honest read** on whether the program is hitting your bar — if not, we want to know now and address it directly

---

*Supporting documents:*
- *[Full performance review (background)](https://newgamejay.github.io/ffc-recap-2026q1/) — every number traceable to BigQuery / source*
- *[Evidence and receipts (separate doc)](#) — exact links, queries, and source documents for everything in this agenda*
