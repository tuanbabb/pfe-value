# Brief: Build Claude Skill — PageFly Feedback Analyzer

**To:** Hưng (H), Vanguard team
**From:** Tony Bui (T)
**Date:** 2026-05-07
**Project:** PageFly Enterprise (PFE) value validation
**Reference doc:** `H-Pain-Points-Methodology.md` (cùng folder)

---

## TL;DR

Build 1 Claude Skill auto-analyze feedback requests từ Google Sheet → output ranked pain points table + insights. Methodology đã có sẵn trong reference doc. T đã proven framework với 150 Crisp conversations; H scale lên với feedback Sheet.

---

## Why this skill

T đã build pain points framework manually từ Crisp data (60 days, 150 merchants). Process tốn ~3-4 tiếng work. Cần automate vì:

1. **Feedback Sheet liên tục có new entries** — manual analysis không scale
2. **Cần regular cadence** — weekly/monthly insights cho PFE roadmap decisions
3. **Cross-reference với Crisp data** — Sheet feedback + Crisp tickets = full picture
4. **Vanguard team + Lâm CS team có thể self-serve** — không cần T bottleneck

Skill này giúp Vanguard team có **always-fresh pain points dashboard** để inform PFE roadmap, marketing copy, và customer onboarding.

---

## Skill spec — high level

### Name (suggested)
`pagefly-feedback-analyzer` (hoặc tên H thấy hợp lý hơn)

### Trigger keywords
- "phân tích feedback", "analyze feedback Sheet"
- "pain points report", "PFE buy probability"
- "rank features by Total Acquisition Score"
- "what merchants want most"
- Hoặc paste Sheet URL

### Input
**Primary**: Google Sheet "PageFly Feedback Form (Responses)"
- URL: https://docs.google.com/spreadsheets/d/1UWZoSkv1Yx4vW24TJ7RPKQLaDL9aaO94-djiFrx2Lmg/edit?gid=1482381426
- Format: each row = 1 merchant feedback submission
- Columns expected: timestamp, store URL, plan, request text, severity (if labeled), etc.
- (H verify exact schema khi build)

**Secondary** (optional Phase 2):
- Crisp filter "Shopify Plus Merchants" — cross-reference data
- Mantle customer data — enrich với GMV / plan tier

### Workflow (suggested)
```
Step 1: Read Google Sheet → parse rows
Step 2: For each row → categorize into 1 of 12 pain point themes (semantic match)
        - If new theme detected → flag for taxonomy expansion
Step 3: Aggregate → count Reqs per theme
Step 4: Score each theme on ROI (1-10), Impl (1-3), PFE Buy Prob (1-10)
        - Use rubric in methodology doc
        - LLM-based scoring with reasoning
Step 5: Compute Total Acquisition Score per theme
Step 6: Sort by Buy Prob DESC, then Reqs DESC
Step 7: Generate Insights sections (Top 4, Bottom 4, Strategic recs, Gap analysis)
Step 8: Output formats:
        - Markdown table (preview chat)
        - Excel/Google Sheet (sortable, with formulas)
        - HTML dashboard (visual cho stakeholder share)
```

### Output deliverables (per skill run)
1. **Pain points ranked table** (markdown + Excel)
2. **4 insights sections** (auto-generated):
   - Top high-buy-probability themes
   - Bottom low-buy-probability themes
   - Strategic recommendations (marketing, onboarding, prioritization)
   - Gap analysis (frequency vs buy intent mismatches)
3. **Diff vs previous run** (Phase 2): "What changed since last analysis?"
4. **Recurring customers list** (Phase 2): merchants với 3+ feedback submissions = high signal

---

## Reference materials (in workspace folder)

- **`H-Pain-Points-Methodology.md`** ← MAIN reference, full taxonomy + scoring framework + reasoning templates + sample output
- **`Shopify-Plus-Merchants-Pain-Points-Analysis.md`** ← raw Crisp 150 conversations + sample insights output (proven format T validated)
- **`PFE-Roadmap-Backlog.xlsx`** Sheet "Pain Points Master" ← structured data with formulas

---

## Skill technical considerations (cho H decide)

**MCP connectors needed**:
- Google Sheets MCP (read PageFly Feedback Form)
- (Optional) Crisp MCP — cross-reference
- (Optional) Mantle MCP — customer enrichment

**LLM tasks** (Claude Code or skill-internal):
- Semantic categorization (text → 1 of 12 themes)
- Multi-language handling (EN/JP/CN/VI/...)
- Reasoning generation cho mỗi score
- Insights synthesis

**Output writer**:
- Markdown to chat
- Excel via openpyxl skill (xlsx skill)
- HTML dashboard nếu cần visual

**Trigger pattern**:
- Manual run on demand (Tony or Hưng runs it)
- (Phase 2) Scheduled weekly run, post results to Slack channel

---

## Phase 1 vs Phase 2 scope

### Phase 1 (MVP — H ship đầu tiên)
- Read Sheet → categorize → score → ranked table + insights
- Output: Markdown + Excel
- Manual run only
- Use 12 themes from methodology as fixed taxonomy

### Phase 2 (improvements sau)
- Cross-reference với Crisp + Mantle
- Diff vs previous run
- Recurring customer detection
- Scheduled weekly run + Slack post
- Auto-discover new themes (taxonomy expansion)
- HTML dashboard

---

## Validation criteria (how T knows skill works)

H có thể test skill bằng cách:

1. **Run skill on Crisp 150 conversations** (load CSV manually) → output should match T's manual analysis (within tolerance)
   - Top 4 high-buy themes match: Multi-store (10), Stability (9), Section Library (8), Team Roles (8)
   - Total Acquisition Score top 5 match approximately

2. **Run on real Feedback Sheet** → review output với Tony before share
3. **Edge cases**:
   - Multi-language requests handled correctly
   - New themes flagged when found
   - Recurring customers identified

---

## Timeline

T proposes:
- **Week 1 (this week)**: H read methodology, design skill spec, ask T clarifying questions
- **Week 2-3**: H build Phase 1 MVP, test on Crisp 150 sample
- **Week 4**: Production run on Feedback Sheet, present to Vanguard team
- **Q3**: Phase 2 improvements

Flexibility tùy Hưng capacity. Không có hard deadline trừ khi V-team cần insights cho PFE T4 launch (deadline mid-May).

---

## Communication

- **For clarifying questions**: ping T trên Slack
- **For methodology questions**: refer to `H-Pain-Points-Methodology.md` first; nếu unclear, ping T
- **For demo / review**: schedule 30min với T + Boo team

---

## Why this matters (motivation)

PFE positioning depends on accurate pain point understanding. T's manual analysis = snapshot. Skill = continuous monitoring. With this skill:

- **Vanguard team** have always-fresh data cho PFE roadmap decisions
- **CS team** identify trending issues earlier
- **Marketing** auto-update copy based on what's hottest
- **Tony's Founder's Office Hours** target pain points actually surfacing in feedback

This skill = foundation cho PFE iteration cycle (validate-build-ship-iterate).

---

*T sẵn sàng support H bất kỳ lúc nào. Best of luck building.*

— Tony Bui, Vanguard Team Lead
