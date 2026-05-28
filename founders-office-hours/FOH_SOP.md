# Founder's Office Hours — SOP
**Owner:** Tony · **Support:** H  
**Last updated:** 2026-05-26 · **Version:** v1.0 (MVP)

---

## Overview

Founder's Office Hours là service cốt lõi của PFE Scale & Dominate. Tony review store merchant async, gửi lại Loom (~15 min) + 1-page PDF report trong 5 business days.

**Capacity:** 5 merchants/week (không quá — Tony đã commit public)  
**SLA:** 5 business days từ khi nhận intake email  
**Email:** tony@pagefly.io

---

## End-to-End Flow

```
[Merchant gửi intake email]
          │
          ▼
[Step 1] Tony nhận email → Log vào Sheet → Check capacity
          │
          ▼
[Step 2] Chạy SSA Agent → Nhận report
          │
          ▼
[Step 3] Tony vào store trực tiếp → Double-check + thêm notes cá nhân
          │
          ▼
[Step 4] Tony điền FOH_Report_Template.html → Save as PDF
          │
          ▼
[Step 5] Tony record Loom (~15 min) — theo Loom guide trong SSA report
          │
          ▼
[Step 6] Tony gửi Response Email (Loom link + PDF đính kèm)
          │
          ▼
[Step 7] Update Sheet → Status = Delivered
```

---

## Step-by-Step Chi Tiết

### Step 1 — Nhận & Log Intake Email (~5 min)

**Tony hoặc H làm:**

1. Email từ merchant đến tony@pagefly.io với subject `[Office Hours Request]`
2. Mở `FOH_Tracking_v1.xlsx` → tab **🗂 Active Queue**
3. Thêm 1 row mới:
   - **Email Received** = ngày hôm nay
   - **Review Due** = Email Received + 5 business days
   - **Status** = `Submitted`
   - Điền: Merchant Name, Store URL, Tier, Revenue Band, Merchant's #1 Question, Pages Reviewed (từ intake email)
4. Mở tab **📅 Capacity Tracker** → confirm week đó còn slot không
   - Nếu **còn slot**: proceed
   - Nếu **full (5/week)**: reply merchant ngay — "I've received your request. I'm fully booked this week but will review you by [date+7]. Thanks for your patience."
5. Mở tab **👥 Merchant Master** → check merchant đã có chưa
   - Nếu new merchant: add row mới, PFE Start Date = hôm nay, Session # = 1
   - Nếu returning: update Session # + Last Review Date

---

### Step 2 — Chạy SSA Agent (~automated, ~5 min setup)

**Tony làm trong Cowork:**

1. Mở Cowork session mới
2. Gõ: `SSA for [store URL]` và paste intake email vào
3. SSA tự crawl key pages dùng Chrome MCP, output structured report
4. **Đọc Executive Summary** — đây là phần quan trọng nhất để định hướng review
5. Note: SSA là AI — Tony phải verify trực tiếp trên store (Step 3)

**Nếu SSA fail hoặc Chrome không connect:**
- Skip SSA, Tony tự review trực tiếp trên store (vẫn trong SLA)
- Note trong Sheet: `SSA Run? = No`

---

### Step 3 — Tony Review Trực Tiếp (~20-25 min)

**Tony vào store thực tế:**

1. Mở store URL
2. Walk through từng page trong list (max 3 pages)
3. Dùng SSA report làm checklist — verify từng finding
4. **Thêm personal insights mà SSA không có:**
   - Growth strategy perspective
   - Patterns Tony thấy từ 200K+ merchants
   - Specific Shopify/PageFly tricks advanced
   - Điều gì trong store trông "off" theo kinh nghiệm cá nhân
5. Điền phần **"Tony's Notes"** trong SSA report (hoặc sticky note/doc riêng)
6. Xác nhận Top 3 Priority Actions (đồng ý hay điều chỉnh so với SSA suggestions)

**Thời gian budget:**
- 5-7 min/page nếu 3 pages
- Dành 5-7 min cho merchant's question
- Stop at 25 min — phần còn lại cho Loom

---

### Step 4 — Điền PDF Report (~5-10 min)

1. Mở `FOH_Report_Template.html` trong Chrome
2. Click vào từng field và điền (template là fillable HTML)
3. Điền đầy đủ:
   - Executive Summary (3-4 câu)
   - Top 3 Actions (specific, có effort + PageFly feature)
   - Merchant's Question answered
   - Page findings (strengths + issues per page)
   - Loom URL (điền sau khi record xong)
4. **Save as PDF:**
   - Cmd+P (Mac) hoặc Ctrl+P (Windows)
   - Destination: Save as PDF
   - Tên file: `[Store Name] · Founder's Review · [Month Year].pdf`
   - Ví dụ: `Luxe Botanics · Founder's Review · June 2026.pdf`
5. Save PDF vào Google Drive hoặc folder local để attach vào email

---

### Step 5 — Record Loom (~15 min)

**Setup trước khi record:**
- Mở store URL + SSA report + PDF report trên màn hình
- Bật Loom (record screen + face nếu muốn personal touch)
- Xem lại **"What I want to open with"** từ Tony's Notes

**15-minute structure (từ Loom Guide trong SSA report):**

| Min | Content |
|-----|---------|
| 0:00–1:00 | Open: "Hi [Name], I'm Tony. 3 things I want you to walk away with today..." |
| 1:00–3:00 | Executive summary — 1 strength + 1 biggest opportunity |
| 3:00–10:00 | Screen share: walk through pages live, narrate findings |
| 10:00–12:00 | Answer merchant's #1 question directly |
| 12:00–14:00 | Top 3 actions — WHY each matters, not just what |
| 14:00–15:00 | Close: "Start with #1. Reply if unclear. See you next month." |

**Quy tắc:**
- ✅ Screen share store thực tế — chỉ vào exactly what you mean
- ✅ Nói tự nhiên — đừng đọc script
- ✅ Gọi tên merchant ít nhất 2 lần
- ❌ Không quá 17 phút — cut at 15 nếu cần
- ❌ Không đọc từ report — report là cho merchant đọc sau

**Sau khi record:**
- Copy Loom share link
- Paste vào PDF report template → "Save as PDF" lần cuối với Loom URL
- Paste vào Sheet → cột "Loom URL"

---

### Step 6 — Gửi Response Email (~3 min)

1. Mở `Response_Email_Template.md`
2. Copy template email
3. Điền:
   - `[First Name]` = merchant first name
   - `[LOOM LINK]` = Loom share URL
   - Attach PDF report
   - Top 3 actions (copy từ PDF)
   - Merchant's question + direct answer
4. **Subject:** `Your Founder's Review is Ready — [Store Name] · [Month Year]`
5. Send từ tony@pagefly.io

---

### Step 7 — Update Sheet (~2 min)

Sau khi email sent:

1. `FOH_Tracking_v1.xlsx` → **🗂 Active Queue**:
   - Status → `Delivered`
   - Loom URL → paste link
   - PDF Report Link → paste Google Drive link (nếu có)
   - Top Actions → điền từ report
2. Move row to **📚 Session History** tab (hoặc dùng filter)
3. **👥 Merchant Master** → update:
   - Last Review Date = hôm nay
   - Next Review Eligible = hôm nay + 30 ngày
   - Total Sessions Completed += 1

---

## H's Role (Support)

H có thể làm Step 1 (Log + check capacity) và Step 7 (update Sheet) để giải phóng Tony.

**Tony phải tự làm:** Step 2 (SSA review), Step 3 (live store review), Step 4 (điền PDF), Step 5 (Loom), Step 6 (gửi email).

**Shared access:** cả Tony và H đều có quyền edit FOH_Tracking_v1.xlsx

---

## Edge Cases

| Tình huống | Xử lý |
|-----------|-------|
| Merchant không submit đủ info | Reply: "Thanks! Could you share [specific missing field]? E.g. which pages you want me to focus on, and your #1 question." |
| Week đã full (5 slots) | Reply ngay: "Received — fully booked this week. Your review will be by [date+7]." Log with due date +7 days |
| Merchant hỏi clarification sau khi nhận review | Reply via email, no new Loom needed unless major misunderstanding |
| Merchant muốn schedule 2nd session sớm hơn 30 ngày | "Office Hours opens monthly to keep it high-quality. Next one on [date]." |
| Merchant inactive (không submit sau 2 tháng) | Flag trong Master sheet → Churn Risk = 🟡 Watch → H follow up via PFE nurture sequence |
| Store bị private/password protected | Reply: "Can you temporarily remove the password so I can review? I'll let you know once I'm done." |

---

## Files & Links

| File | Purpose | Location |
|------|---------|----------|
| `Founders_Office_Hours_Intake_Template.md` | Template merchant dùng để submit | Google Drive / share link |
| `FOH_Tracking_v1.xlsx` | Tracking tất cả sessions + capacity | Google Drive (Tony + H access) |
| `SSA_SKILL.md` | SSA agent skill cho Cowork | Cowork plugin folder |
| `FOH_Report_Template.html` | PDF report template Tony điền | Local → open in Chrome |
| `Response_Email_Template.md` | Email Tony gửi sau review | Reference doc |
| `FOH_SOP.md` | This file | Google Drive |

---

## KPIs để track

| Metric | Target (MVP) | Measure |
|--------|-------------|---------|
| Review delivery time | ≤ 5 business days | Sheet: Email Received vs Delivered date |
| Merchant rating | ≥ 4.5/5 | Sheet: Merchant Rating column |
| Loom watch rate | ≥ 80% | Loom analytics |
| Merchant action rate | ≥ 70% implement ≥1 action | Follow-up email next month |
| Churn rate | < 10%/month | Master sheet: Churn Risk |
| Capacity utilization | 3-5/week | Capacity Tracker sheet |

---

*v1.0 MVP — Review sau 30 ngày để update dựa trên real feedback từ first cohort*
