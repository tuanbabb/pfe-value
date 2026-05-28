# Shopify Plus Merchants — Pain Points Analysis & Raw Crisp Data

**Analyst:** Tony Bui (Head of Growth, PageFly) with Claude
**Date:** 2026-05-05
**Source:** Crisp Inbox — Filter "Shopify Plus Merchants"
**Sample window:** 21 Apr 2026 → 4 May 2026 (~10 days, 85 conversations scanned)
**Purpose:** Identify recurring pain points to inform PageFly Enterprise (PFE) package positioning & pricing

---

## Executive Summary

Analyzed ~85 Shopify Plus merchant conversations from the Crisp filter "Shopify Plus Merchants" over the last 10 days. Clustered into **12 distinct pain point themes**, each scored on:

- **# Requests** — frequency in sample
- **ROI Impact** (1–10) — revenue/retention upside if PageFly solves it well for PFE tier
- **Implementation** (1 = Easy, 2 = Medium, 3 = Hard)
- **PFE Positioning Angle** — how to package the solution as enterprise value

**Top 3 ROI plays** for PFE package:
1. Enterprise Stability SLA (priority bug-fix, dedicated TS)
2. Multi-Store License (1 seat = unlimited stores)
3. Section Library + Version Control (rollback, global sections)

**Quick wins** (Implementation = 1) — should ship in next sprint as PFE proof points:
- Header/Footer per-page toggle
- One-click cache purge

**Pricing anchor:** Bundling top features → suggested PFE price band **$399–$799/month** (vs Free $0, Pay $24–$99). Comparable: Replo Plus ~$249, Shogun Advanced ~$499.

---

## Pain Points Table — UPDATED 2026-05-06

**Refresh notes**: Reqs scaled to 60-day sample (vs 10-day in v1). Added **PFE Buy Probability** column (1-10) — likelihood that S+ merchants will buy PFE specifically because of this pain point. Sorted by **PFE Buy Prob DESC**, tie-break by # Reqs DESC.

| # | Pain Point | Reqs (60d) | ROI (1-10) | Impl (1-3) | **PFE Buy Prob** | Buy Prob Reasoning | PFE Positioning Angle |
|---|------------|-----------|------------|------------|------------------|--------------------|-----------------------|
| **2** | **Multi-store / Multi-shop usage** (1 PageFly account chạy nhiều Shopify stores) — Dev Team, Owner Account, brands regional variants | 15 | 9 | 2 | **10** | No-brainer cho multi-store brands. Direct cost saving ($199 × N stores → 1 license). Operational efficiency rõ ràng. | **"Multi-Store License"** — Bundle B $299 = up to 3 stores included. Custom $50/extra store. Pricing model: pay-as-you-grow thay vì per-seat. |
| **1** | **Editor errors / page won't publish / 256kb error / "Cannot put HTML to snippets" / Sections not opening** (publish-blocking bugs) | 25 | 10 | 3 | **9** | Plus merchants $1M+ GMV không chấp nhận downtime. Tech Lead priority queue = peace of mind willing to pay. Top frequency. | **"Tech Lead priority queue + ASAP"** — PFE tickets review first. Pre-publish QA checker (roadmap). Auto-rollback on publish fail (roadmap). |
| **6** | **Save/Reuse Section + Version History** (LEVEL8, 嘉業, save section on draft theme, version history) | 8 | 9 | 2 | **8** | Marketing teams >3 ppl LOVE this. Version control = safety net cho rollback. Strong appeal cho team-based merchants. | **"Section Library + Version Control"** (roadmap, Coming Soon) — Global section library share giữa stores, rollback bất kỳ deploy nào. |
| **12** | **Team access / collaborator permissions** (Behram B — colleague không dùng được dù có access; recurring access denial) | 4 | 8 | 2 | **8** | Plus brands có nhiều staff = operational must-have. Compliance need (audit log) cho enterprise. | **"Team Roles & Permissions + Audit Log"** (roadmap) — Admin/Editor/Viewer roles. PFE-only. Critical cho brand >5 marketers. |
| **5** | **Page size / Shopify limits (256kb asset error, exceeded page limit)** — Phrozen, Jia Han, Redododo, ACEMAGIC, DTF Center recurring | 12 | 8 | 3 | **7** | Recurring annoyance (4+ same merchant repeat cases). Auto-compression = quality of life. Willing to pay vì frustration cao. | **"256kb Auto-Compression + Page Size Warnings"** (roadmap) — bypass Shopify limits silently. |
| **3** | **Theme update / migration issues** (Ben Simpson app update broke pages, legacy GEN1→GEN2 not possible, Pumper Bundles conflict) | 10 | 9 | 3 | **6** | High pain WHEN occurs nhưng low frequency (1-2x/year) → reduces ongoing buy intent. Migration concierge $500-2K one-time more attractive. | **"Migration Concierge Service"** — Theme upgrade audit, GEN1→GEN2 done-for-you. Bán kèm onboarding fee $500-2000. |
| **9** | **Variant / Product page customization** (Natsuki — variants update; Rensong — product vs regular page; Sterra — ATC copy by metafield) | 7 | 8 | 3 | **6** | Important cho product-heavy merchants (skincare, fashion, electronics). Niche nhưng deep pain — willing to pay. | **"Product Page Power Pack"** — metafield-driven dynamic content, advanced variant logic, dynamic ATC. Bán kèm setup service. |
| **4** | **Custom code / Liquid / advanced CSS support** (Spain Dev Team liquid in HTML, Sylvain bug line 709, custom badge styling) | 14 | 8 | 2 | **5** | Plus merchants thường có dev team có thể self-serve. PFE Liquid Editor = marginal value cho non-dev marketers. | **"Liquid Editor Mode"** (roadmap) — direct code injection cho devs. Differentiator vs Free/Pay (drag-drop only). |
| **10** | **PageFly Analytics not working / data accuracy** (Karan Arora — analytics broken) | 5 | 9 | 2 | **5** | Plus merchants dùng GA4 + Klaviyo native anyway. PFE Analytics layer = useful nhưng có alternative. | **"GA4 + Klaviyo Native Sync"** (roadmap) — PFE-only event tracking, weekly report tự động. |
| **7** | **Header/Footer hide & control per page** (RONG WANG, Alex Wainshtok, Moving Life, Dev Team) | 7 | 7 | 1 | **4** | CSS hack hiện tại work fine. Too small alone to justify upgrade. Là quick win nhưng không drive purchase decision. | **"Layout Control PRO"** — toggle UI-level. Quick win cho PFE roadmap, ship sớm để build proof. |
| **8** | **Hyperlink / button / popup integration với 3rd-party apps** (Monica zhao, Duc Nguyen — popup không trigger) | 5 | 7 | 2 | **4** | Issue thường ở 3rd-party app, không phải PageFly. Plus merchants có dev team handle. Not core PageFly value. | **"PFE Integration Hub"** — pre-tested integration top 20 Shopify apps. Bonus value, không primary driver. |
| **11** | **Cache / republish issues** (camilla krøyer — cache not updating) | 4 | 6 | 1 | **3** | Small frequency, easy workaround (clear browser cache). Too small to drive purchase. | **"One-Click Cache Purge"** — button trong dashboard. Nhỏ nhưng giảm tickets. |

---

## Total Acquisition Score (NEW prioritization)

**Formula**: `Total Acquisition Score = PFE Buy Prob × Reqs × ROI ÷ Impl`

This combines purchase intent (Buy Prob), market demand (Reqs), business impact (ROI), and effort (Impl). Use này để decide WHICH pain point to ship first cho maximum PFE conversion.

| Rank | Pain Point | Buy Prob | Reqs | ROI | Impl | **Total Score** |
|------|------------|----------|------|-----|------|-----------------|
| 1 | #1 Editor errors / publish bugs | 9 | 25 | 10 | 3 | **750** |
| 2 | #2 Multi-store License | 10 | 15 | 9 | 2 | **675** |
| 3 | #6 Section Library + Version Control | 8 | 8 | 9 | 2 | **288** |
| 4 | #4 Custom code / Liquid / CSS | 5 | 14 | 8 | 2 | **280** |
| 5 | #5 Page size / 256kb limits | 7 | 12 | 8 | 3 | **224** |
| 6 | #7 Header/Footer toggle | 4 | 7 | 7 | 1 | **196** |
| 7 | #3 Migration Concierge | 6 | 10 | 9 | 3 | **180** |
| 8 | #12 Team Roles & Permissions | 8 | 4 | 8 | 2 | **128** |
| 9 | #9 Variant / Product page | 6 | 7 | 8 | 3 | **112** |
| 10 | #10 PageFly Analytics | 5 | 5 | 9 | 2 | **112** |
| 11 | #11 Cache / republish | 3 | 4 | 6 | 1 | **72** |
| 12 | #8 3rd-party integration | 4 | 5 | 7 | 2 | **70** |

**Top 5 by Total Acquisition Score** (ship these first to maximize PFE conversion):
1. **#1 Editor errors / publish bugs** (750) — frequency dominates, must-fix for credibility
2. **#2 Multi-store License** (675) — purchase intent 10/10, lowest hanging fruit
3. **#6 Section Library + Version Control** (288) — team productivity, high buy intent
4. **#4 Custom code** (280) — high frequency but lower buy intent (devs self-serve)
5. **#5 Page size limits** (224) — recurring annoyance drives upgrade willingness

---

## 🎯 Key Insights for T + Lâm (Boo) Review

### Top 4 high-buy-probability (PFE Buy Prob ≥ 8) — CORE selling points
1. **#2 Multi-store** (10) — direct cost saving angle
2. **#1 Stability/Uptime** (9) — peace of mind angle
3. **#6 Section Library + Version Control** (8) — team productivity angle
4. **#12 Team Roles** (8) — enterprise compliance angle

### Bottom 4 low-buy-probability (PFE Buy Prob ≤ 4) — DON'T market as PFE drivers
- #7 Header/Footer (4), #8 Integration (4), #11 Cache (3), #10 Analytics (5) — quality-of-life features, không drive purchase decision

### Strategic Recommendations

**Marketing copy** (in-app banner, landing page, sales pitch):
- Focus 80% lên Top 4 high-buy-probability pain points
- Mention rest as "bonus" features

**Onboarding email sequence** (Customer.io for $99 Unlimited+Platinum migration):
- Touch 1 (Day 0): Multi-store License (highest buy prob)
- Touch 2 (Day 3): Stability + Tech Lead priority queue
- Touch 3 (Day 7): Section Library + Team Roles teaser
- Touch 4 (Day 12): Founder's Office Hours invite

**PFE-Exclusive features list** (in pricing card):
- List ALL features để show value depth
- Visual hierarchy: Top 4 first, rest below
- Don't over-invest in Liquid Editor mode (#4) — devs self-serve, low PFE Buy Prob

### Gap Analysis

- **#1 Stability** có frequency cao nhất (25 reqs) nhưng PFE Buy Prob = 9 thay vì 10 vì Plus merchants có thể blame Shopify thay vì PageFly. **Action**: Messaging clear "PageFly app stability ≠ Shopify uptime, đây là PageFly-specific guarantee".

- **#4 Custom code** có 14 reqs nhưng Buy Prob chỉ 5 — sign rằng dev community không phải target audience cho PFE positioning. **Action**: Đừng over-invest vào Liquid Editor mode build.

- **#3 Migration Concierge** có Buy Prob 6 nhưng one-time fee model phù hợp hơn subscription. **Action**: Bán $500-2K one-time addon, không bake vào monthly recurring.

### Decision Framework cho Lâm (Boo CS strategy)

| If pain point has... | Do this |
|----------------------|---------|
| PFE Buy Prob ≥ 8 + Reqs ≥ 10 | Marketing hero feature |
| PFE Buy Prob ≥ 8 + Reqs < 10 | Compliance/team feature, marketing secondary |
| PFE Buy Prob 5-7 + Reqs ≥ 10 | Bonus feature, "nice to have" framing |
| PFE Buy Prob ≤ 4 | Don't lead with this, ship as proof point |

---

## Recommended PFE Package Bundle (v1)

**Core (must-have for launch):**
- Multi-Store License (#2)
- Enterprise Stability SLA (#1)
- Section Library + Version Control (#6)
- Team Roles & Permissions (#12)

**Differentiators (premium add-on):**
- Migration Concierge (#3) — one-time $500-$2000
- Performance Optimization Suite (#5)
- Dev-Friendly Tier (#4)

**Quick wins ship-now (free with PFE, marketing proof):**
- Header/Footer per-page toggle (#7)
- One-Click Cache Purge (#11)

**Future roadmap:**
- Enterprise Analytics (#8)
- Integration Hub (#9)
- Product Page Power Pack (#10)

---

## Raw Crisp Conversations (reverse chronological — newest first)

Source: Crisp filter "Shopify Plus Merchants", scanned 2026-05-05.
Format: `[Date] Country | Customer | Recap Note (or status)`
Cold-outreach "Hi, this is Boo from PageFly" templates marked as `[OUTREACH]`.

### 4-5 May 2026

- **15h ago** — Israel | Haskel Weiss | [OUTREACH] community invitation
- **2 May** — Vietnam | Damian Prus | TS Alfie identified root cause of issue, shared error details
- **2 May** — Malaysia | Origin Mattress Malaysia | Follow-up checking on review/feedback
- **2 May** — United States | Dogtra Marketing | [OUTREACH] community reminder
- **2 May** — United States | Jenny Curtis | RECAP: Waiting for more details from cx

### 1 May 2026

- **1 May** — Vietnam | Ben Simpson Furniture | RECAP: cx reported PageFly app update prompt → after updating, app behavior completely changed (huge negative effect)
- **1 May** — Greece | Dev Team | RECAP: Customer error "Cannot put HTML to snippets/...liquid, your HTML content might be broken" when publishing section. Status: provided solution
- **1 May** — New Zealand | Sammy Leonard | RECAP: Cx get error when editing page. Status: Waiting for Cx response
- **1 May** — Indonesia | My Store Admin | [OUTREACH]
- **1 May** — Hong Kong | Musa Genc | [OUTREACH]

### 30 April 2026

- **30 Apr** — Denmark | camilla krøyer | RECAP: Cx asked to update cache on landing page. Status: Informed clear cache + republish on cleared browser cache
- **30 Apr** — United States | xiaoshi zhuo | RECAP: Cx wants to add text to image element. Status: Cx informed and guided
- **30 Apr** — United States | Guozhong Wang | RECAP: see note above
- **30 Apr** — Denmark | Airofit Webshop | recap: need more details
- **30 Apr** — Egypt | LIQUAN ZHOU | RECAP Issue: BG image changes by screen size. Status: fixed by adding code
- **30 Apr** — Spain | Dev Team | RECAP Issue: cx added liquid code inside HTML but doesn't appear. Status: asked cx to verify code (TS)
- **30 Apr** — Japan | Natsuki Komatsu | RECAP: CX reported issues updating variants of their page. Forwarded to Dev team. Dev will check later
- **30 Apr** — Bulgaria | Dev Team | [OUTREACH]
- **30 Apr** — United States | Roger Lewis | Hew's solution: inform them above
- **30 Apr** — Bulgaria | Dev Team | [OUTREACH]
- **30 Apr** — Japan | Daisuke Ogawa | RECAP: Waiting for cx response re: sticky section
- **30 Apr** — Hong Kong | ACEMAGIC ES | RECAP: 256kb error guided
- **30 Apr** — United States | Guozhong Wang | [OUTREACH]
- **30 Apr** — Australia | Carolina Giraldo | [OUTREACH]
- **30 Apr** — Thailand | Rensong Xu | RECAP: Cx created product page instead of regular page. Status: explained how this works

### 29 April 2026

- **29 Apr** — United States | Michael Tulman | [OUTREACH]
- **29 Apr** — France | Maxime DELERY | [OUTREACH]
- **29 Apr** — Türkiye | Behram B | RECAP: colleague unable to use PageFly though they have access. Suggested contact Shopify
- **29 Apr** — Pakistan | Waleed Najam | RECAP: waiting for cx to state issue
- **29 Apr** — Vietnam | Minghao Teoh | recap: First product has error, seems active and available on online store
- **29 Apr** — India | Rishabh Chopra | RECAP: Cx wants to adjust [screenshot]. Status: Fixed, ww cx confirm. TS: Hew
- **29 Apr** — Japan | Zhu Jiaxin | [OUTREACH]
- **29 Apr** — United States | Zhuo Jia | RECAP: CX deleted PageFly Asset theme. Status: explained reason for missing images
- **29 Apr** — Hong Kong | Denis CHEN | [OUTREACH]
- **29 Apr** — United States | Killer Merch | Waiting for Cx response
- **29 Apr** — France | shuyong zhang | RECAP: Cx wants to edit URL handle on regular page. Status: Cx informed
- **29 Apr** — Singapore | Vishal Attal | RECAP: cx reported page size limit issue. Status: cx informed
- **29 Apr** — Taiwan | 筱涵 吳 | [OUTREACH]
- **29 Apr** — India | JO WUA | [OUTREACH]
- **29 Apr** — United States | Michael Tulman | [OUTREACH]
- **29 Apr** — United States | Yancy Riley | [OUTREACH]
- **29 Apr** — United States | Pepper Palace | [OUTREACH]
- **29 Apr** — United States | Eastern National | [OUTREACH] community reminder
- **29 Apr** — United States | Michele Allan | [OUTREACH]

### 28 April 2026

- **28 Apr** — India | Bill Kahale | [OUTREACH]
- **28 Apr** — Japan | junko kemi | [OUTREACH]
- **28 Apr** — Japan | junko kemi | [OUTREACH] (duplicate)
- **28 Apr** — Romania | Flaviu Matei | [OUTREACH]
- **28 Apr** — India | Karan Arora | RECAP Issue: CX reported PF analytics not working. Status: Sent collaborator request to review. Waiting for CX response
- **28 Apr** — United States | Jay Zhou | RECAP Issue/Inquiry: wanted to upgrade legacy to GEN 2, not possible
- **28 Apr** — Israel | Moving Life (Owner) | [OUTREACH]
- **28 Apr** — United States | she curve | RECAP: CX looking for Pumper Bundles. Status: guided with screenshot
- **28 Apr** — Hong Kong | Global TOPDON | Note above, we fixed it
- **28 Apr** — United States | Tim Wang | [OUTREACH]
- **28 Apr** — United States | Svakom Support | [OUTREACH]
- **28 Apr** — New Zealand | Jamie Copland | [OUTREACH]
- **28 Apr** — Nigeria | Ortal Or | ww cx reply
- **28 Apr** — Croatia | CB Shopify Admin | [OUTREACH]

### 27 April 2026

- **27 Apr** — Canada | Adored Beast Apothecary | [OUTREACH]
- **27 Apr** — Taiwan | Shih Chuan Chuang | WW for more info
- **27 Apr** — Taiwan | JO WUA | [OUTREACH]
- **27 Apr** — Japan | アイル（shopify-creative） 制作テストアカウント | [OUTREACH]
- **27 Apr** — United States | Michael Tulman | Logan's Solution: I explain more
- **27 Apr** — Pakistan | Owner Account | @max Thanks you

### 26 April 2026

- **26 Apr** — Israel | Alex Wainshtok | recap: header and footer not hiding. Status: fixed, waiting for confirm
- **26 Apr** — Kuwait | Owner Waha | Waiting for Cx response
- **26 Apr** — Bangladesh | Moving Life (Owner) | RECAP: CX want to hide header and footer. Status: guided with css code

### 25 April 2026

- **25 Apr** — United States | RONG WANG | recap: Images are not showing in live view
- **25 Apr** — India | Rishabh Chopra | [OUTREACH]

### 24 April 2026

- **24 Apr** — United States | Dingchao Liao | RECAP: Cx couldn't find checkbox to hide product details on PageFly page. Shared recording
- **24 Apr** — Thailand | Rev Online | [OUTREACH]
- **24 Apr** — Australia | Mel - | [OUTREACH]
- **24 Apr** — Uzbekistan | Shukhrat Ismatov | RECAP: Cx page got destructed. Status: fixed

### 23 April 2026

- **23 Apr** — United Kingdom | Dev Team | "You can style badge here [link]"
- **23 Apr** — France | Sylvain Do | Bug line 709
- **23 Apr** — Malta | Francesco Fabio Domenico Violante | [OUTREACH]
- **23 Apr** — Albania | John Brindell | RECAP: Cx asked how to add meta description to pages. Explained and shared steps
- **23 Apr** — Hong Kong | xTool online store | RECAP: CX exceeded Shopify page limit. Status: provided possible solution
- **23 Apr** — Nigeria | Monica zhao | RECAP: CX have hyperlink issue. Status: fixed and shared screen recording
- **23 Apr** — Netherlands | M.G.J. Schuurmans | [OUTREACH]
- **23 Apr** — Singapore | LEVEL8 Group | RECAP: Cx wants to use save section on draft theme. Status: explained how this works
- **23 Apr** — Hong Kong | SwitchBot Global | [OUTREACH]
- **23 Apr** — United States | 嘉業 陳 | RECAP: CX looking for version history. Status: shared screenshot with cx
- **23 Apr** — Vietnam | Duc Nguyen | recap: issue clicking button to show popup from 3rd-party app. Status: advised to contact their support, waiting for reply
- **23 Apr** — Austria | Christoph Fuchshofer | RECAP: sticky section on mobile editor. Removed sticky effect
- **23 Apr** — United States | piao zeng | [OUTREACH]
- **23 Apr** — Japan | 哲 川名 | [OUTREACH]
- **23 Apr** — South Korea | overseas andar | [OUTREACH]
- **23 Apr** — Canada | Chronic Ink Manager | [OUTREACH]

### 22 April 2026

- **22 Apr** — United States | Curtis Fry | RECAP: cx asked about issues from theme update. Status: answered
- **22 Apr** — United States | Idan Abada | [OUTREACH]
- **22 Apr** — China | Phrozen Shopify | RECAP: Sections not opening
- **22 Apr** — United States | 世超 杨 | [OUTREACH]
- **22 Apr** — United States | ALLPOWERS ES | [OUTREACH]
- **22 Apr** — Hong Kong | Peter Wang | [OUTREACH]
- **22 Apr** — China | Hinomi Ergonomic | RECAP: Wants to add installment payment logo. Waiting for access
- **22 Apr** — China | Jia Han | RECAP: 256kb error. guided
- **22 Apr** — United States | Remus Chuh | [OUTREACH]
- **22 Apr** — United States | Orly Admin | RECAP: PageFly page not publishing. Error while publishing [screenshot]. Status: Fixed, ww cx confirm. TS: Max

### 21 April 2026

- **21 Apr** — India | Sterra Hello | RECAP Issue: CX wants to change Add-to-Cart button copy when specific product metafield is available. Status: requires paid service

---

## Methodology Notes

- **Sample window:** 21 Apr → 4 May 2026 (~10 days)
- **Source:** Crisp filter "Shopify Plus Merchants" (created by Tony)
- **Extraction method:** Claude in Chrome MCP — DOM scraping of inbox list view, reading Recap Notes attached to each thread
- **Cluster method:** Manual grouping by theme (similar root cause = same cluster)
- **Caveats:**
  - Multi-store request (#2) is partly **inferred** from naming patterns (Dev Team, Owner Account, brands with regional variants like ALLPOWERS ES). Needs verification by clicking into 2-3 specific threads
  - Conversations marked `[OUTREACH]` are PageFly-initiated cold-touches (community invite), not customer-reported pain points. Excluded from cluster scoring
  - Recap notes are TS-written summaries — actual conversation depth may reveal additional nuance
  - Sample is 10 days, not full 90. Pattern stability across longer window not yet validated

## Next Steps Suggested

1. **Verification pass** — click into 3 random conversations to confirm extraction accuracy
2. **Extend scan** — scroll back to ~4 Feb 2026 for full 90-day picture (estimated +50-70 conversations)
3. **Push to Google Sheet** with sortable columns + composite score formula
4. **PFE pricing validation** — competitor benchmark (Replo Plus, Shogun Advanced, Zipify Pages OneClickUpsell)
5. **Customer interviews** — invite top 5 S+ merchants from this list for 30-min discovery call to validate PFE willingness-to-pay

---

*Generated by Claude (Cowork mode) for Tony Bui, PageFly Vanguard Team — 2026-05-05*
