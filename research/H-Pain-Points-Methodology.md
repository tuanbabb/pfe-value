# Pain Points Analysis — Methodology & Framework

**Audience:** Hưng (H) — for building Claude Skill that analyzes PageFly feedback requests
**Author:** Tony Bui (T) with Claude (Cowork)
**Date:** 2026-05-07
**Source:** Crisp filter "Shopify Plus Merchants" (60-day sample, ~150 conversations) + PageFly Feedback Form (Google Sheet)

---

## Purpose of this document

Tony đã build được **taxonomy + scoring framework** từ phân tích 150 conversations Crisp của Shopify Plus merchants. H sẽ dùng framework này để build Claude Skill auto-analyze feedback requests từ Google Sheet **PageFly Feedback Form (Responses)**.

Document này là **methodology reference** — không có recommendations về pricing hay product strategy. Chỉ cách phân tích.

---

## 1. Pain Point Taxonomy (12 themes)

Đã categorize 150 raw conversations thành 12 distinct pain point themes. Sử dụng đây làm starting taxonomy. Skill có thể discover thêm themes mới khi scan feedback Sheet.

| # | Pain Point Theme | Keywords / Indicators | Example Customer Quotes |
|---|------------------|----------------------|------------------------|
| 1 | **Editor errors / publish-blocking bugs** | "Cannot put HTML to snippets", "256kb error", "Sections not opening", "page won't publish", "editor not loading" | "Cannot put HTML to snippets/...liquid", "256kb error guided", "Page editor not loading" |
| 2 | **Multi-store / Multi-shop usage** | "multiple stores", "expansion store", "Dev Team" naming pattern, regional brand variants (e.g., "ALLPOWERS ES", "xTool Europe Store") | Implied via shop URL patterns + naming |
| 3 | **Theme update / migration issues** | "theme update", "GEN1 → GEN2", "legacy", "app update broke", "Pumper Bundles conflict" | "wanted to upgrade legacy to GEN 2, not possible", "App update broke their pages" |
| 4 | **Custom code / Liquid / advanced CSS** | "liquid in HTML", "custom CSS", "code injection", "bug line XXX", "snippet code" | "added liquid code inside HTML but doesn't appear", "Bug line 709" |
| 5 | **Page size / Shopify limits** | "256kb error", "page size limit", "exceeded Shopify page limit", "asset size" | "exceeded Shopify page limit", "page size limit issue" |
| 6 | **Save/Reuse Section + Version History** | "save section", "draft theme", "version history", "rollback", "template library" | "wants to use save section on draft theme", "version history" |
| 7 | **Header/Footer per-page hide** | "hide header", "hide footer", "remove header on landing", "header conflict" | "header and footer not hiding", "want to hide header and footer" |
| 8 | **Hyperlink / popup / 3rd-party integration** | "popup not working", "Klaviyo integration", "Yotpo", "button click", "3rd party app" | "issue clicking a button to show a popup from 3rd party app" |
| 9 | **Variant / Product page customization** | "variants", "metafield", "ATC button", "swatch", "product page conditional logic" | "wants to change Add-to-Cart button copy when specific product metafield is available" |
| 10 | **PageFly Analytics not working** | "analytics broken", "data accuracy", "tracking", "conversion attribution" | "PF analytics is not working" |
| 11 | **Cache / republish issues** | "cache", "force refresh", "page not reflecting changes", "CDN" | "Cx asked if they can update cache on their landing page" |
| 12 | **Team access / collaborator permissions** | "colleague unable to use", "access denied", "team member", "admin permission" | "colleague was unable to use PageFly though they have access" |

**Categorization rule for the skill**:
- Each request maps to **1 primary theme** + optionally **1-2 secondary themes** if cross-cutting
- If a request doesn't fit any theme, create new theme (track for taxonomy expansion)
- Use semantic similarity, not just keyword match (LLM strength)

---

## 2. Scoring Framework (4 dimensions)

Mỗi pain point được score trên 4 dimensions. Skill output should populate all 4 cho mỗi theme.

### 2a. # Requests (count)
- Đếm raw count các requests fall vào theme này trong sample window
- Sample window: configurable (60 days default cho conversations Crisp; toàn bộ Sheet với feedback form)
- **Rule**: 1 customer = N requests (cùng customer multiple touches = N counts)
- **Why this dimension**: frequency = market demand signal

### 2b. ROI Impact (1-10)
Ước lượng business value nếu PageFly fix tốt pain point này. Subjective scoring, dựa vào:
- **10**: Direct GMV impact (publish blocked = sales lost). Ví dụ: editor errors.
- **8-9**: Strong revenue/retention upside (multi-store, analytics)
- **6-7**: Quality of life, indirect impact (cache purge, header toggle)
- **1-5**: Nice-to-have, low commercial impact

**Skill prompt example**:
> "Given this pain point: [X], rate ROI Impact 1-10 based on: (1) frequency × severity, (2) does it block revenue actions, (3) typical customer GMV affected. Justify briefly."

### 2c. Implementation (1=Easy, 2=Medium, 3=Hard)
Engineering effort estimate:
- **1 (Easy)**: UI toggle, button, copy change. < 1 sprint.
- **2 (Medium)**: New feature build, but uses existing infra. 1-3 sprints.
- **3 (Hard)**: New infra, cross-team coordination, complex logic. > 3 sprints.

### 2d. PFE Buy Probability (1-10) ⭐ KEY METRIC
**Definition**: Likelihood that a Shopify Plus merchant currently using PageFly will UPGRADE to PFE specifically because this pain point gets solved.

This is the **purchase intent** dimension. Different from ROI Impact (business value) — this is about whether merchants will pay.

**Scoring rubric**:
- **10**: No-brainer purchase. Direct cost saving + operational efficiency. Ex: multi-store license saves $199 × N stores.
- **8-9**: High intent. Critical pain that's hard to live with. Plus merchants $1M+ GMV cannot accept downtime.
- **5-7**: Moderate intent. Pain exists but có alternative (workaround, dev team, 3rd-party tool).
- **1-4**: Low intent. Quality of life only, không drive purchase decision.

**Skill prompt example for PFE Buy Prob**:
> "Score 1-10 the probability that a Shopify Plus merchant on PageFly Power $199 will upgrade to PFE if this pain point gets solved. Consider: (1) Do alternatives exist? (2) Is the pain blocking revenue? (3) Is this a recurring pain or one-time? (4) Would a dev/marketer/CMO be the decision maker — and which would buy? Justify with 1-2 sentences."

### 2e. Total Acquisition Score (computed)
**Formula**: `Total Acquisition Score = PFE Buy Prob × # Requests × ROI Impact ÷ Implementation`

This combines purchase intent (Buy Prob), market demand (Reqs), business impact (ROI), and effort (Impl). Use này để rank features by "ship priority for max conversion".

**Interpretation**:
- Score > 500 = ship first
- Score 200-500 = ship next sprint
- Score 100-200 = backlog
- Score < 100 = deprioritize unless dependency for higher-scored item

---

## 3. Sample Output (from 150 Crisp conversations)

H có thể dùng output dưới đây như **golden example** cho skill — verify skill output matches general pattern.

### Sorted by PFE Buy Prob DESC

| # | Pain Point | Reqs | ROI | Impl | PFE Buy Prob | Total Score |
|---|------------|------|-----|------|--------------|-------------|
| 2 | Multi-store / Multi-shop usage | 15 | 9 | 2 | **10** | 675 |
| 1 | Editor errors / publish-blocking bugs | 25 | 10 | 3 | **9** | 750 |
| 6 | Save/Reuse Section + Version History | 8 | 9 | 2 | **8** | 288 |
| 12 | Team access / collaborator permissions | 4 | 8 | 2 | **8** | 128 |
| 5 | Page size / Shopify limits (256kb) | 12 | 8 | 3 | **7** | 224 |
| 3 | Theme update / migration issues | 10 | 9 | 3 | **6** | 180 |
| 9 | Variant / Product page customization | 7 | 8 | 3 | **6** | 112 |
| 4 | Custom code / Liquid / advanced CSS | 14 | 8 | 2 | **5** | 280 |
| 10 | PageFly Analytics not working | 5 | 9 | 2 | **5** | 112 |
| 7 | Header/Footer per-page hide | 7 | 7 | 1 | **4** | 196 |
| 8 | 3rd-party integration / popup | 5 | 7 | 2 | **4** | 70 |
| 11 | Cache / republish issues | 4 | 6 | 1 | **3** | 72 |

### Top 5 by Total Acquisition Score

1. #1 Editor errors (750) — frequency dominates
2. #2 Multi-store (675) — Buy Prob 10/10
3. #6 Section Library (288) — team productivity
4. #4 Custom code (280) — high reqs but mid Buy Prob
5. #5 Page size (224) — recurring annoyance

---

## 4. Insights Structure (skill should auto-generate)

Sau khi score mỗi pain point, skill auto-derive 4 insights sections:

### Insight A: Top high-buy-probability (Buy Prob ≥ 8)
List pain points = "CORE selling points" cho PFE marketing.

### Insight B: Bottom low-buy-probability (Buy Prob ≤ 4)
List pain points = "DON'T market as PFE drivers" — quality of life only.

### Insight C: Strategic recommendations
Auto-generate 3 sections:
- **Marketing copy** — focus 80% lên Top 4 high-buy
- **Onboarding email sequence** — sequence hits top pain in order
- **Feature prioritization** — top by Total Acquisition Score

### Insight D: Gap analysis
For each pain point with mismatch (e.g., high frequency but low Buy Prob), explain WHY:
- High freq + low Buy Prob → likely có alternative or wrong audience
- Low freq + high Buy Prob → niche but high-value, may need outreach

---

## 5. Reasoning Templates (cho mỗi PFE Buy Prob score)

Skill output should include 1-sentence reasoning cho mỗi Buy Prob score. Templates:

| Score Range | Template |
|-------------|----------|
| 9-10 | "[Direct cost saving / operational efficiency angle]. No-brainer because [specific dollar impact or workflow benefit]." |
| 7-8 | "[Strong appeal cho audience]. Willing to pay because [recurring annoyance or compliance need]." |
| 5-6 | "Important nhưng có alternative ([workaround / 3rd-party tool / dev team]). Reduces buy intent because [alternative]." |
| 3-4 | "[Quality of life feature]. Not a purchase driver because [easy workaround or low frequency]." |
| 1-2 | "[Niche or marginal value]. Won't drive any purchase decision." |

---

## Appendix: Methodology constraints

- **Sample bias**: Crisp filter "Shopify Plus Merchants" curated by Tony — may have selection bias. Skill should flag if Sheet feedback has fundamentally different distribution.
- **Multi-language**: Crisp conversations span EN/JP/CN/VI/etc. Skill should handle multi-language requests.
- **Recurring customers**: Same merchant may submit N requests. Skill option to dedupe by customer email/store URL OR keep all (default: keep all, flag recurring as "high signal").
- **Time window**: 60-day sample for Crisp = balance between recency + sample size. Configurable for Sheet.

---

*Ready for H to build Claude Skill. Reference Google Sheet input: PageFly Feedback Form (Responses) — gid=1482381426.*
