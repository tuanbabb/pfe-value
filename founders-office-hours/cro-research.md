# CRO Behavioral Research Reference
> Used by SSA (Shopify Store Audit) to ground findings in peer-reviewed research  
> Philosophy: ethical CRO only — leverage psychology that reflects genuine value, never fake urgency or dark patterns  
> Last updated: 2026-05-26

---

## How to use this file

When SSA identifies an issue or opportunity on a merchant's page, cite the relevant research using this format:

```
[Finding] — grounded in [Research Name] ([Author, Year])
Expected CVR impact: [range] if applied ethically
Ethical check: [what makes this ethical vs dark pattern]
```

Never cite research to justify manipulative tactics. If a recommendation would only work through deception, it's a dark pattern — flag it and suggest an ethical alternative instead.

---

## R1 — Loss Aversion & Prospect Theory

**Source:** Kahneman & Tversky (1979) · *Econometrica* · "Prospect Theory: An Analysis of Decision under Risk"  
**Supporting:** Ganzach & Karsahi (1995) · *Journal of Marketing*

**Core finding:** People feel losses ~2.25× more intensely than equivalent gains. Loss-framed messaging ("Don't lose your discount") outperforms gain-framed ("Save 20%") in most contexts — not as a trick, but because it accurately reflects how humans weight risk.

**CVR impact:** Meta-analysis of A/B tests shows 15–30% lift on CTR for loss-framed CTAs vs gain-framed. Effect degrades rapidly when the claimed loss is not credible or verifiable.

**Ethical application for Shopify stores:**
- Real low-stock warnings (pulled from live inventory) — not hardcoded "Only 3 left"
- Genuine time-limited offers (sale end dates that are real)
- "Don't miss your saved cart" recovery emails when cart is genuinely about to expire
- Framing return policy as removing loss risk: "Hate it? Full refund, no questions"

**Dark pattern to avoid:** Fake countdown timers that reset on refresh. Fake stock numbers. Permanent "sale" prices. These backfire when customers discover them — trust loss is irreversible.

**SSA audit signals:**
- Is urgency copy ("X left in stock", "Sale ends in...") backed by real data?
- Does the loss framing reflect a genuine risk to the customer?
- Is the return policy framed as risk removal, or buried in fine print?

---

## R2 — FOMO (Fear of Missing Out)

**Source:** Przybylski, Murayama, DeHaan & Gladwell (2013) · *Computers in Human Behavior* · "Motivational, emotional, and behavioral correlates of fear of missing out"

**Core finding:** FOMO is driven by unmet needs for social belonging and competence — seeing others act creates genuine motivation to participate. Social activity signals (real-time "X people viewing this") trigger authentic FOMO. Static or fake signals trigger skepticism once noticed.

**CVR impact:** Experian (2014) found real-time social proof signals increase product page engagement. Baymard Institute recommends use only when data is genuinely live — fake signals reduce trust by 23% among returning visitors who notice the inconsistency.

**Ethical application:**
- Live "X people viewing" — only if pulled from real analytics in real time
- "X sold in the last 24 hours" — only if accurate
- "Back in stock" notifications — authentic scarcity signal
- Wishlists visible to friends (opt-in) — genuine social proof

**Dark pattern to avoid:** Hardcoded social proof numbers. "15 people viewing right now" that never changes. Recently purchased popups with fake names/locations. These are explicitly called out in EU Digital Services Act (2022) as deceptive.

**SSA audit signals:**
- Are social proof numbers dynamic or static in the page source?
- Does "X viewing now" change on reload, or stay the same?
- Are recently-purchased notifications tied to real order data?

---

## R3 — Social Proof

**Source:** Cialdini (1984) · *Influence: The Psychology of Persuasion*  
**Quantified:** Spiegel Research Center (2017) · Northwestern University · study of 57,000+ products

**Core finding:** Spiegel found that displaying reviews increases CVR by **270%** for products with 5+ reviews vs no reviews. Reviews with photos: additional **91% lift**. Verified purchase badges increase trust signals. Placement near CTA outperforms placement below the fold.

**CVR impact:** 270% CVR increase (5+ reviews vs 0). Nielsen Norman Group eye-tracking: review stars in product title area receive 3× more fixations than reviews placed at page bottom.

**Ethical application:**
- Authentic reviews only — never incentivize positive reviews (violates FTC guidelines)
- Display negative reviews alongside positive (Spiegel: showing ~4.2–4.5 avg rating is MORE convincing than 5.0 — 5.0 looks fake)
- Photo reviews prioritized in display
- "Verified purchase" labels where available
- Aggregate stats ("4.8/5 from 1,247 reviews") near Add-to-Cart

**Dark pattern to avoid:** Hiding negative reviews. Buying fake reviews. Showing only 5-star reviews. Rating manipulation. All violate FTC guidelines (16 CFR Part 255) and Amazon/Shopify platform rules.

**SSA audit signals:**
- Review count and average rating — visible above fold?
- Rating distribution shown (not just average)?
- Reviews include photos?
- Are reviews placed near the primary CTA?
- Does average rating look artificially perfect (5.0 with no variation)?

---

## R4 — Paradox of Choice

**Source:** Schwartz (2004) · *The Paradox of Choice*  
**Original experiment:** Iyengar & Lepper (2000) · *Journal of Personality and Social Psychology* · "When Choice is Demotivating"  
**Processing cost:** Hick & Hyman (1952) · Hick's Law — decision time ∝ log₂(n choices)

**Core finding:** Iyengar & Lepper's jam study: 24 varieties attracted more attention but resulted in **10× lower purchase rate** (3% vs 30%) compared to 6 varieties. More options = more cognitive load = more decision fatigue = no decision. Hick's Law: each doubling of options increases decision time by a fixed increment.

**CVR impact:** Reducing collection pages from 50+ items to curated 12–15 with clear hierarchy can lift CVR 20–40% in documented e-commerce cases. Variant selectors with 3–4 options outperform 10+ in A/B tests across Baymard's dataset.

**Ethical application:**
- "Featured" or "Best Seller" tags to anchor attention without hiding other products
- Guided selling (quiz funnel) to narrow to relevant options — helpful, not limiting
- Smart defaults for variants (most popular pre-selected)
- Progressive disclosure: show top products first, "View all" secondary

**Dark pattern to avoid:** Hiding products to manipulate perception of scarcity. Forcing bundle purchases. "Recommended" labels on high-margin items regardless of genuine quality.

**SSA audit signals:**
- Collection pages: how many items per page? Is there a "featured" hierarchy?
- Product variant selectors: how many options? Are they visually manageable?
- Navigation: how many top-level categories? Does it feel overwhelming?
- Is there a quiz, filter, or guided selling tool to reduce choice burden?

---

## R5 — Processing Fluency

**Source:** Reber, Winkielman & Schwarz (2004) · *Psychological Science* · "Processing Fluency and Aesthetic Pleasure"  
**Applied:** Alter & Oppenheimer (2006) · *PNAS* · "Predicting short-term stock fluctuations by using processing fluency"

**Core finding:** Information that is easier to process cognitively is rated as more true, more beautiful, and more trustworthy — even when content is identical. Legible fonts, high contrast, clear hierarchy signal credibility before the brain consciously evaluates content.

**CVR impact:** Baymard Institute (2023, n=40,000+ usability sessions): 37% of cart abandonments are due to checkout process complexity — not price or shipping. Clear visual hierarchy and reduced cognitive load is the single highest-ROI improvement category in their research.

**Ethical application:** This is inherently ethical — making things clearer and easier to use is a genuine improvement for the user.
- Font: minimum 16px body on mobile, high contrast (WCAG AA: 4.5:1 ratio)
- Button copy: verb + specific outcome ("Add to Cart" → "Get Free Shipping on This Order")
- Form fields: labeled, logical order, minimal required fields
- Page hierarchy: one clear H1, logical H2/H3 structure
- Whitespace: breathing room between sections

**SSA audit signals:**
- Body font size on mobile (can check CSS)?
- CTA button: does copy describe the action + outcome?
- Are form fields labeled (not just placeholder text)?
- Visual hierarchy: can you identify H1, H2, H3 structure?
- Contrast: does CTA stand out from surrounding elements?

---

## R6 — Endowment Effect & Ownership Psychology

**Source:** Thaler (1980) · *Journal of Economic Behavior & Organization*  
**Extended:** Kahneman, Knetsch & Thaler (1990) · *Journal of Political Economy*  
**Applied to customization:** Franke & Piller (2004) · *Journal of Product Innovation Management*

**Core finding:** People value objects they own more than identical objects they don't. Creating a sense of psychological ownership before purchase increases attachment and willingness to pay. Franke & Piller found product customization increased willingness-to-pay by **~100%** on average — customers felt the customized product was already "theirs."

**CVR impact:** Product configurators and customization tools consistently show higher CVR and AOV vs standard product pages. Try-before-you-buy (if credible) reduces purchase anxiety by removing the "what if I don't like it" barrier.

**Ethical application:**
- Product customization (name engraving, color selection, bundle building) — creates genuine ownership feeling
- Quizzes that end with personalized recommendations ("We found your perfect match")
- "Save your build" functionality
- AR try-on (if available for product category)
- Wishlist as light commitment mechanic

**Dark pattern to avoid:** Pre-ticking add-ons or upsells in checkout (dark pattern, banned in EU under UCPD).

**SSA audit signals:**
- Is there any customization, configuration, or personalization mechanic?
- Does the product page language use "your" (possessive) copy?
- Is there a quiz or recommendation tool?
- PageFly opportunity: product configurator blocks, quiz funnels

---

## R7 — Trust & Credibility

**Source:** Fogg, Marshall, Laraki et al. (2003) · Stanford Persuasive Technology Lab (n=2,500)  
**Checkout-specific:** Baymard Institute (2022) · "Checkout Usability" large-scale study

**Core finding:** Stanford study: **75% of users judge a website's credibility based on visual design** before reading any content. Baymard (2022): **17% of checkout abandonment** is due to "I didn't trust the site with my credit card info." Trust signals at the right moment reduce this anxiety.

**CVR impact:** Adding security badge near payment field: 7–14% reduction in checkout abandonment (Baymard). Displaying return policy on product page (not just footer): 8–12% CVR lift documented in multiple tests.

**Ethical application (trust must be real to be maintained):**
- SSL certificate + Shopify Payments badge near checkout
- Return policy: simple language, visible before Add-to-Cart
- Real contact information: email, phone, or chat accessible
- Physical address or "about us" for brand legitimacy
- Real photography (not just stock photos)
- About page with founder story — especially relevant for DTC brands

**SSA audit signals:**
- Is return/refund policy visible on the product page itself (not just footer)?
- Are there trust badges near the Add-to-Cart or checkout button?
- Is there a visible contact option (chat, email, phone)?
- Does the design look consistent and professional, or are there mismatched fonts/colors?

---

## R8 — Peak-End Rule

**Source:** Kahneman, Fredrickson, Schreiber & Redelmeier (1993) · *Psychological Science* · "When More Pain Is Preferred to Less"

**Core finding:** People don't evaluate experiences by summing or averaging — they remember the **peak** (most intense moment, positive or negative) and the **end**. A painful peak or bad ending colors the entire experience, regardless of how good the rest was.

**CVR impact:** Direct CVR impact is minimal (applies post-purchase). But: LTV and referral impact is large. Brands with excellent post-purchase experience (confirmation page, email sequence) show 20–40% higher repeat purchase rates in documented case studies. Word-of-mouth is driven by peaks and endings.

**Ethical application:**
- Order confirmation page: warm, specific, not just a receipt
- Post-purchase email: celebrate the decision, set expectations, provide value
- Unboxing experience: if physical product — this is the peak moment
- If something goes wrong (delayed shipping): proactive communication makes the "end" better

**SSA audit signals (Tony flags, doesn't crawl):**
- Ask merchant: what does their confirmation page look like?
- Ask merchant: do they have a post-purchase email sequence?
- Note: if their product page is excellent but post-purchase is generic, the peak-end rule predicts weak LTV regardless of good CVR

---

## Quick Reference Matrix

| Research | Audit Layer | Primary SSA Check | Ethical Flag |
|----------|------------|-------------------|--------------|
| R1 Loss Aversion | CTA, urgency copy | Is urgency real or fake? | Fake scarcity = dark pattern |
| R2 FOMO | Social activity signals | Are live numbers actually live? | Static fake numbers = deceptive |
| R3 Social Proof | Reviews, trust badges | Reviews near CTA? Rating authentic? | Hidden negatives = manipulation |
| R4 Paradox of Choice | Navigation, variants, collection | Too many options without hierarchy? | Hiding products = dark pattern |
| R5 Processing Fluency | Typography, hierarchy, forms | Readable? Clear CTA? Low friction? | Inherently ethical when applied |
| R6 Endowment Effect | Customization, personalization | Any ownership-building mechanic? | Pre-ticked upsells = dark pattern |
| R7 Trust & Credibility | Design quality, trust signals | Return policy visible? Contact accessible? | Trust must be real to hold |
| R8 Peak-End Rule | Post-purchase (flag only) | Ask about confirmation + email sequence | N/A — apply positively only |
