# PFE Pricing Framework v1

> **Purpose:** Khi merchant click "Talk to us about Empire" → fill email template → Tony (hoặc agent) parse câu trả lời → compute custom offer + breakdown → reply email với số tiền cụ thể.
> **Output:** Một con số `quote_monthly` + breakdown từng dòng + recommended next step.
> **Owned by:** Tony (Head of Growth · PageFly).
> **Last updated:** 2026-05-11.

---

## 1. Email template merchant fills

**Subject:** `Empire plan inquiry | {shop_domain}` (auto-fill, ví dụ `tuanba.myshopify.com`)

**Body:**

```
Hi Tony,

I'm interested in PageFly Enterprise (PFE) Empire plan for my brand. Please use the inputs below to put a custom offer (with breakdown) in your reply.

—— ABOUT US ——
• Store URL: {shop_domain}
• Category / niche:
• Monthly revenue range:
  □ $50k–$200k   □ $200k–$1M   □ $1M–$5M   □ $5M+
• Stores you operate: __ now / __ planned in next 6 months

—— VOLUME WE NEED ——
• Pages or sections published per month:
  □ <5   □ 5–20   □ 20–50   □ 50+
• AI credits per month (1,600 = ~1 store baseline):
  □ 1,600   □ 3–5k   □ 5–10k   □ 10k+
• Ready-to-use templates / custom design help per month:
  □ None   □ 1–5   □ 5–15   □ 15+

—— SERVICE LEVEL ——
• Founder's Office Hours (async review by Tony — 45-min review, email + Loom, no call):
  □ 1/mo   □ 2/mo   □ 4/mo   □ Weekly
• Tech support level:
  □ ASAP queue   □ 1:1 named owner   □ Dedicated team   □ 24/7 SLA
• AI Audit cadence:
  □ Monthly   □ Bi-weekly   □ Weekly   □ On-demand

—— TECHNICAL ——
• Credit pool model: □ Shared across stores   □ Separate per-store
• API access needed: □ Yes   □ Maybe   □ No
• White-label / agency mode: □ Yes   □ Maybe   □ No
• Custom integrations (CRM, ERP, headless, …):

—— COMMERCIAL ——
• Preferred contract: □ Monthly   □ Annual (~15% off)   □ Multi-year
• Monthly budget ceiling:
  □ $500–1k   □ $1k–3k   □ $3k–10k   □ $10k+   □ Open
• Start timeline:
  □ ASAP   □ Within 30 days   □ Within 90 days   □ Exploring

—— ANYTHING ELSE ——
<Free-form: specific outcome, compliance needs, anything you want me to dig into>

Best,
[Your name] / [Your role]
```

> **Note:** Câu hỏi về current Shopify plan + current PageFly plan KHÔNG hỏi — Tony tự check qua AC2 / Mantle khi có `shop_domain`.

---

## 2. Pricing formula

```
quote_monthly =
  ( BASE
    × VOLUME_MULT
    × SERVICE_MULT
    × TECH_MULT
    + CREDIT_ADDON
    + TEMPLATE_ADDON
    + AUDIT_ADDON
    + INTEGRATION_ADDON
  )
  × STORE_MULT
  × CONTRACT_DISCOUNT
```

Output: 1 con số cuối + breakdown từng dòng + so sánh với merchant's stated budget ceiling.

---

## 3. Lookup tables (1-1 với câu hỏi email)

| Câu hỏi merchant trả lời | Giá trị | Variable / coefficient |
|---|---|---|
| **Revenue range** | $50k–$200k | `BASE = $299` (Scale floor) |
| | $200k–$1M | `BASE = $499` (Dominate floor) |
| | $1M–$5M | `BASE = $999` |
| | $5M+ | `BASE = $1,999` |
| **Pages/mo** | <5 | `VOLUME_MULT = 1.0` |
| | 5–20 | `1.2` |
| | 20–50 | `1.5` |
| | 50+ | `2.0` |
| **AI credits/mo** | 1,600 | `CREDIT_ADDON = $0` (included) |
| | 3–5k | `$200` |
| | 5–10k | `$500` |
| | 10k+ | `$1,000` |
| **Templates / custom design help/mo** | None | `TEMPLATE_ADDON = $0` |
| | 1–5 | `$150` |
| | 5–15 | `$400` |
| | 15+ | `$900` |
| **Founder's Office Hours** *(async review by Tony, 5/wk capacity = 20/mo total)* | 1/mo | `SERVICE_MULT = 1.0` |
| | 2/mo | `1.3` |
| | 4/mo | `1.6` |
| | Weekly (cap 4/mo) | `2.0` |
| **Tech support level** | ASAP queue | `TECH_MULT = 1.0` |
| | 1:1 named owner | `1.3` |
| | Dedicated team | `1.8` |
| | 24/7 SLA | `2.5` |
| **AI Audit cadence** | Monthly | `AUDIT_ADDON = $0` (included) |
| | Bi-weekly | `$150` |
| | Weekly | `$400` |
| | On-demand | `$700` |
| **Stores count** | 1 | `STORE_MULT = 1.0` |
| | 2–3 | `1.0 + 0.3 × (n−1)` → 1.3–1.6 |
| | 4–10 | `1.6 + 0.2 × (n−3)` |
| | 10+ | quote per-store $80–120 manual |
| **Credit pool model** | Shared | (no change) |
| | Separate per-store | `STORE_MULT × 1.2` |
| **API access** | Yes | `INTEGRATION_ADDON += $500` |
| | Maybe | `+ $250` |
| | No | `+ 0` |
| **White-label / agency mode** | Yes | `INTEGRATION_ADDON += $300` |
| | Maybe | `+ $150` |
| | No | `+ 0` |
| **Custom integrations** *(free-form)* | per item | `+ $200–500 each` (Tony manual review) |
| **Contract** | Monthly | `CONTRACT_DISCOUNT = 1.0` |
| | Annual | `0.85` (~15% off) |
| | Multi-year | `0.75` (~25% off) |

---

## 4. Sanity rules (cross-check trước khi gửi quote)

| Check | Action |
|---|---|
| Final quote > merchant budget ceiling × 1.5 | Anchor lower tier (Scale/Dominate) hoặc strip 1–2 add-on, re-quote |
| Final quote < $299 | Quote Scale plan, không phải Empire — đừng force Empire vào lead nhỏ |
| Revenue < $50k và budget > $3k | Fishing / unrealistic → low priority, polite no, send Scale info |
| Revenue > $1M và budget < $1k | Budget-constrained nhưng real → Scale + upsell path, không Empire |
| Stores > 10 và shared pool | Cảnh báo merchant về credit-burn risk, push separate-pool, re-quote `× 1.2` |
| 24/7 SLA + revenue < $1M | Mismatch — explain SLA cost không justify ROI ở scale này |
| Weekly Office Hours + revenue < $1M | Tony's capacity quá đắt với scale này, suggest 2/mo |
| AI credits 10k+ + Pages <5 | Inconsistent → ask follow-up: are credits for non-page AI features? |

---

## 5. Action mapping (info A → take action B)

Mỗi field merchant trả lời mở ra action Tony làm ngay khi reply hoặc trong custom proposal.

| Info merchant fill | Tự verify qua | Action Tony take |
|---|---|---|
| **Store URL** (`xxx.myshopify.com`) | AC2 + Mantle → current Shopify plan, current PageFly plan, plan age, MRR contribution, churn risk, last seen | Pre-check trước khi reply: tier nào, đã trial chưa, có cancel/restart cycle nào không, credit usage pattern (cao/thấp) |
| **Category / niche** | View live storefront → brand maturity, design quality | **Bundle ready-to-use templates fit niche**: fashion → 5 fashion landing pages curated từ Smart Pages catalog. Electronics → spec-comparison templates. B2B → quote-request flow. Propose template seed pack as Empire bonus |
| **Monthly revenue range** | AC2 revenue tracking nếu có | **Pricing anchor:** map sang BASE column |
| **Stores (current + 6mo)** | Mantle multi-store linking | **Multi-store credit pool config:** 1 store → Scale default, 2–3 → Dominate, 4+ → quote per-store $50–100/mo addon. Pre-calculate pool size |
| **Team size + PF users** | — | **Onboarding scale:** 1–2 users → standard onboarding, 3+ → train-the-trainer session. Decide if Empire bundle needs custom training material |
| **Pages/mo + Credits/mo + Templates/mo** | — | **Volume bundle:** decide on credit topup tier + template seed pack + design hours buffer |
| **Office Hour booking** *(async)* | — | **Calendar block:** reserve Tony's review slots, set submission deadline (e.g. submit by Mon → Loom by Fri) |
| **Tech support level** | — | **Tech Lead assignment:** ASAP queue → general pool, 1:1 named → assign specific Tech Lead, Dedicated team → carve out team capacity, 24/7 SLA → contract addendum required |
| **AI Audit cadence** | — | **AI Audit subscription:** schedule monthly/bi-weekly/weekly automated runs + Loom review |
| **API / White-label / Integrations** | — | **Technical scoping:** if Yes → schedule 1 tech discovery call (15 phút) before quote, parse "Custom integrations" free-form for scope |
| **Timeline** | — | **Priority queue:** ASAP → reply within 24h + Calendly. 30 days → reply within 3 days + 1 nurture deliverable. 90 days → drip nurture sequence. Exploring → low priority, send PFE case study email |
| **Budget ceiling** | Validate vs revenue range answer | **Quote framing:** sanity rules apply |
| **Free-form (Anything else)** | — | **First-touch agenda:** parse hidden requirements (compliance, GDPR, deadline). Use as qualifier — vague = low intent; specific = high intent |

---

## 6. Example reply (after parsing merchant email)

**Merchant filled:**
- Revenue $200k–$1M, 2 stores now (+1 planned), Fashion niche
- 20–50 pages/mo, 5–10k credits/mo, 1–5 templates/mo
- Office Hours 2/mo, Tech support 1:1 named, AI Audit bi-weekly
- Shared pool, API Maybe, White-label No
- Annual contract, Budget $1k–3k, Timeline 30 days

**Compute:**
- BASE = $499 (revenue $200k–$1M)
- VOLUME_MULT = 1.5 (20–50 pages)
- SERVICE_MULT = 1.3 (2 Office Hours/mo)
- TECH_MULT = 1.3 (1:1 named)
- CREDIT_ADDON = $500 (5–10k)
- TEMPLATE_ADDON = $150 (1–5 templates)
- AUDIT_ADDON = $150 (bi-weekly)
- INTEGRATION_ADDON = $250 (API Maybe)
- STORE_MULT = 1.3 (2 stores)
- CONTRACT_DISCOUNT = 0.85 (annual)

`((499 × 1.5 × 1.3 × 1.3) + 500 + 150 + 150 + 250) × 1.3 × 0.85`
= `(1265 + 1050) × 1.3 × 0.85`
= `2315 × 1.105`
= **~$2,558/mo (annual)**

**Reply template:**

```
Hi <name>,

Based on your inputs, here's a custom Empire proposal:

  $2,558 / mo  (annual contract, locked in — saves ~$450/mo vs monthly)

Breakdown:
- Base (revenue $200k–$1M):                $499
- Volume (20–50 pages × 1.5 multiplier):   + $250
- Service (2 Office Hours × 1.3 multiplier): + $200
- Tech support (1:1 named owner × 1.3):    + $200
- AI credits buffer (5–10k):               + $500
- Template seed pack (1–5/mo):             + $150
- AI Audit bi-weekly:                      + $150
- API access (Maybe → reserved):           + $250
- Multi-store premium (2 stores):           × 1.3
- Annual contract:                          × 0.85

Bonus included for Fashion niche:
- Curated fashion landing page seed pack (5 templates)
- AI prompt presets for product-hero, lookbook, size-guide pages

Next step — pick one:
1. Book 45-min async review with me (Loom + email): <Calendly link>
2. Request a tweaked package (e.g. drop API, add stores)
3. Ready to start — send contract & onboard

Reply by <date> to lock in the 30-day timeline.

Best,
Tony
```

---

## 7. Future: agentify

Khi merchant follow-up qua email/chat về bundle, agent có thể:
1. Parse reply → identify which field merchant wants to change
2. Re-run formula với new inputs → output new quote
3. Auto-reply hoặc draft for Tony review

**Skill input contract:**
```ts
type EmpireInquiryInput = {
  shop_domain: string
  category?: string
  revenue: '50k-200k' | '200k-1M' | '1M-5M' | '5M+'
  stores_now: number
  stores_planned: number
  pages_per_month: '<5' | '5-20' | '20-50' | '50+'
  credits_per_month: '1600' | '3-5k' | '5-10k' | '10k+'
  templates_per_month: 'none' | '1-5' | '5-15' | '15+'
  office_hours_per_month: 1 | 2 | 4 | 'weekly'
  tech_support: 'asap' | '1to1' | 'dedicated' | 'sla24x7'
  ai_audit_cadence: 'monthly' | 'biweekly' | 'weekly' | 'ondemand'
  credit_pool: 'shared' | 'separate'
  api_access: 'yes' | 'maybe' | 'no'
  white_label: 'yes' | 'maybe' | 'no'
  custom_integrations?: string[]
  contract: 'monthly' | 'annual' | 'multi-year'
  budget_ceiling: '500-1k' | '1k-3k' | '3k-10k' | '10k+' | 'open'
  timeline: 'asap' | '30-days' | '90-days' | 'exploring'
  free_form?: string
}

type EmpireQuoteOutput = {
  quote_monthly: number
  breakdown: { line: string; amount: number }[]
  budget_ceiling_check: 'within' | 'over' | 'way-over'
  niche_bundle?: string[]
  warnings: string[]      // from sanity rules
  next_steps: string[]
}
```

---

## Changelog

- **v1 (2026-05-11)** — Initial framework. Email template, formula, lookup tables, sanity rules, action mapping, example reply.
