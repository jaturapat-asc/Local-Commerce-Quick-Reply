
# 🏪 Local Commerce Quick-Reply

> **AI Copilot ที่ร่างข้อความตอบแชทปิดการขายสำหรับร้านค้าชุมชน OTOP บน LINE OA**
> ลดเวลาตอบ · ลดลูกค้าหลุด · เพิ่มยอดขาย — โดยคนยังคงเป็นผู้ตัดสินใจส่งข้อความทุกครั้ง

[![Pillar](https://img.shields.io/badge/Pillar-SME_%26_Local_Economy-blue)]()
[![Status](https://img.shields.io/badge/Status-Approved_for_Development-brightgreen)]()
[![License](https://img.shields.io/badge/License-MIT-yellow)]()
[![LINE](https://img.shields.io/badge/Channel-LINE_OA-00C300)]()
[![LLM](https://img.shields.io/badge/LLM-Gemini_1.5_Flash-4285F4)]()

---

## 📑 Table of Contents

- [Overview](#overview)
- [Stage 0 — Pillar Selection & Idea](#stage-0--pillar-selection--idea)
- [Stage 1 — Intent Capture & Framing](#stage-1--intent-capture--framing)
- [Stage 2 — Market Research](#stage-2--market-research)
- [Stage 3 — Feasibility & Constraints](#stage-3--feasibility--constraints)
- [Stage 4 — Scope Definition](#stage-4--scope-definition)
- [Stage 5 — Team Formation](#stage-5--team-formation)
- [Stage 6 — Rough Mockups](#stage-6--rough-mockups)
- [Stage 7 — Approval & Handoff](#stage-7--approval--handoff)
- [Stage 8a — Content Document](#stage-8a--content-document)
- [Stage 8b — Summary Presentation](#stage-8b--summary-presentation)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Design Principles](#design-principles)
- [License](#license)

---

## Overview

**Local Commerce Quick-Reply** เป็นโปรเจกต์ที่พัฒนาขึ้นสำหรับ **AI for All Thailand Innovation Sprint** ภายใต้เสาหลัก **🏪 SME & Local Economy**

ระบบทำงานในโหมด **Human-in-the-Loop (Copilot)** บน LINE Official Account:

1. เจ้าของร้านอัปโหลดข้อมูลสินค้าผ่าน **Google Sheets** (Zero-Setup)
2. ลูกค้าทักแชท → **AI ร่าง Draft Reply** จากแคตตาล็อก + **คำนวณยอดรวม+ค่าส่ง** ด้วย Deterministic Logic
3. แอดมินร้านเห็น Draft → กด **Approve** / **Edit** / **Reject** → ข้อความส่งถึงลูกค้า

| Key Metric | Before | After (Target) |
|---|---|---|
| First Response Time | > 30 นาที | **< 1 นาที** |
| Admin Time / Day | 2–3 ชั่วโมง | **ลดลง ≥ 60%** |
| AI Draft Acceptance | N/A | **> 80%** |
| Conversion Rate | Baseline | **เพิ่ม 15–20%** |

---

## Stage 0 — Pillar Selection & Idea

### เสาหลักที่เลือก

**🏪 SME & Local Economy** — เสริมพลังให้ SMEs ไทย ร้านค้าท้องถิ่น ผู้ประกอบการท่องเที่ยว และวิสาหกิจชุมชน ให้แข่งขันในเศรษฐกิจดิจิทัลได้

### ไอเดียเริ่มต้น

> ตัวช่วยสรุปและตอบแชทปิดการขายสำหรับร้านค้าออนไลน์ชุมชน — ร้านค้า OTOP หรือวิสาหกิจชุมชนมีคนตอบแชทไม่พอ ตอบช้า หรือตอบคำถามซ้ำ ๆ ทำให้เสียลูกค้า

---

## Stage 1 — Intent Capture & Framing

### Problem Statement

ร้านค้า OTOP / วิสาหกิจชุมชนส่วนใหญ่เป็น **One-man show** (ทีม 1–2 คน) ต้องทำทั้งผลิต จัดสต็อก แพ็กพัสดุ และตอบแชทไปพร้อมกัน:

- เสียเวลาเฉลี่ย **2–3 ชม./วัน** กับคำถามซ้ำเดิม (ค่าส่ง, สต็อก, บัญชีโอนเงิน, COD)
- ตอบช้าเกิน 15–30 นาที → **Drop-off rate 30–50%**
- ลูกค้าไทยนิยม **"ทักแชทก่อนโอน"** — Conversational Commerce คิดเป็น **30–40% ของ E-commerce ไทย**

### Solution

| Component | รายละเอียด |
|---|---|
| **ชื่อโปรเจกต์** | Local Commerce Quick-Reply |
| **กลุ่มเป้าหมาย** | แอดมินร้านค้าชุมชน / OTOP ที่ขายผ่าน LINE OA |
| **ช่องทาง** | LINE Official Account (100% MVP) |
| **วิธีทำงาน** | AI ร่างข้อความ + คำนวณยอดรวม → แอดมินกด Approve (Human-in-the-Loop) |
| **เทคโนโลยี** | Context Injection / Prompt Stuffing บน LINE OA |

### การแบ่งประเภทสนทนา

| ประเภท | สัดส่วน | บทบาท AI |
|---|---|---|
| **Transactional / FAQ** (ราคา, สต็อก, ค่าส่ง, บัญชีโอน, สลิป) | 70% | ร่าง Draft Reply + คำนวณยอด → แอดมินกด Approve |
| **Consultative / Custom** (ต่อรอง, สั่งผลิตพิเศษ, แพ้อาหาร) | 30% | คัดกรอง + แจ้งเตือนด่วน `[Tag: Human Attention]` → แอดมินตอบเอง |

### Success Metrics (KPIs)

| KPI | Baseline | Target |
|---|---|---|
| First Response Time | > 30 นาที | < 1 นาที |
| Admin Time Reduction | 2–3 ชม./วัน | ลดลง ≥ 60% |
| AI Draft Acceptance Rate | N/A | > 80% |
| Conversion Rate Lift | Baseline | เพิ่ม 15–20% |

### Constraints & Risks (ระบุตั้งแต่ต้น)

- **เวลา**: จำกัดตามรอบ Hackathon → สถาปัตยกรรมต้องคลีน
- **ต้นทุน**: ≤ หลักร้อยบาท/เดือน (กำไรต่อชิ้นต่ำ)
- **PDPA**: ข้อมูลสลิป/ชื่อ/ที่อยู่ ประมวลผลเพื่อสรุปออเดอร์เท่านั้น ไม่ส่งต่อ/เทรนโมเดล

---

## Stage 2 — Market Research

### Competitive Landscape

| เครื่องมือ | จุดแข็ง | จุดอ่อนสำหรับร้านค้าชุมชน |
|---|---|---|
| **Manychat** | Broadcast, Flow builder | ตั้งค่าซับซ้อน, เน้น Facebook/IG |
| **BotNoi** | Rule-based ภาษาไทย | ต้องสร้าง Flowchart ดักคำ, ตอบไม่ยืดหยุ่น |
| **AIYA** | ตอบอัตโนมัติบน LINE | ขาด Human-in-the-loop ที่ดี |
| **Zwiz.ai** | จัดการคำสั่งซื้อ/ตัดสต็อก | ค่าบริการหลักพัน/เดือน |
| **Kaojao (ข้าวเจ้า)** | ระบบจัดการออเดอร์ | Rule-based, ไม่ยืดหยุ่นกับภาษาพูด |
| **Zaapi** | Broadcast + ระบบสั่งซื้อ | Steep learning curve, ราคาสูง |

### Pain Points ร่วมของคู่แข่ง

1. **ตั้งค่ายาก (Steep Learning Curve)** — ต้องสร้าง Flowchart/Keyword ทีละคำ
2. **ตอบไม่ยืดหยุ่น** — พิมพ์ผิด/ภาษาพูด → บอทวนลูป
3. **ไม่มี Human-in-the-Loop ที่ดี** — เลือกได้แค่ "บอท 100%" หรือ "คน 100%"
4. **ค่าบริการสูง** — เริ่มหลักพันบาท/เดือน

### Market Size

| ข้อมูล | ตัวเลข |
|---|---|
| ผู้ประกอบการ OTOP ลงทะเบียน | ~90,000–100,000 ราย |
| วิสาหกิจชุมชนจดทะเบียน | > 80,000 แห่ง |
| กลุ่มที่ขายออนไลน์แล้ว (LINE/Facebook) | ~15,000–25,000 กิจการ (15–20%) |
| Conversational Commerce ไทย | 30–40% ของ E-commerce รวม |

### 4 จุดแตกต่างหลัก (Differentiation)

1. **🚀 Zero-Setup** — อัปโหลด Google Sheets URL → ใช้งานได้ทันที ไม่ต้องสร้าง Rule-based Flowchart
2. **🤝 Copilot / Human-in-the-Loop Mode** — AI ร่าง Draft Reply → คนกดส่ง → ลด Hallucination
3. **🇹🇭 Local Context & Nuance** — Prompt สำหรับสินค้าท้องถิ่น ภาษาเป็นกันเอง คำนวณค่าส่งตามเงื่อนไขชุมชน
4. **💸 Accessible Pricing** — Lightweight LLM + Pay-per-use / Free Tier → ≤ หลักร้อยบาท/เดือน

---

## Stage 3 — Feasibility & Constraints

### Technical Architecture (Hackathon-Ready)

| Component | Choice | Rationale |
|---|---|---|
| Messaging | LINE Messaging API + Webhook | ช่องทางหลักลูกค้าไทย, Token ได้ใน 5 นาที |
| Local Dev | ngrok | Forward localhost เป็น HTTPS ทดสอบ Webhook ทันที |
| LLM | Gemini 1.5 Flash (Google AI Studio Free Tier) | Context Window ใหญ่, $0 |
| RAG Strategy | **Prompt Stuffing 100%** (ไม่ใช้ Vector DB) | สินค้า 10–50 รายการ ใส่ System Prompt ตรงๆ |
| Data Store | Google Sheets (6 คอลัมน์) | เจ้าของร้านแก้ไขง่าย |
| Backend | Python/FastAPI หรือ Node.js | คลีน, เร็ว |
| Hosting | Render หรือ Railway | Auto-deploy จาก GitHub, Free Tier, HTTPS |

### Google Sheets Schema

| Column | Description | Example |
|---|---|---|
| `Item_Name` | ชื่อสินค้า | น้ำพริกกุ้งเสียบ |
| `Price` | ราคาต่อหน่วย (บาท) | 89 |
| `Stock_Status` | สถานะสต็อก | พร้อมส่ง / หมด |
| `Description` | รายละเอียด | เผ็ดกลาง, ขนาด 200g |
| `Shipping_Rate` | เงื่อนไขค่าส่ง | กทม.50฿, ตจว.70฿ |
| `FAQ` | คำถามบ่อย | เก็บได้ 6 เดือน, มี อย. |

### Team Structure (4 คน)

| Role | Responsibility |
|---|---|
| **Backend & Webhook Dev** | LINE API, Webhook, Google Sheets API, Hosting |
| **AI & Prompt Engineer** | System Prompt, Guardrails, Negative Constraints, Testing |
| **Frontend / UX Designer** | Rich Menu LINE, Admin Approve Web App, Wireframe |
| **Business & Pitching Lead** | Mock Pilot, Case Study, Impact Numbers, Slides, Demo Video |

### Pilot Strategy

- ใช้ **Synthetic Persona / Mock Pilot** (ไม่มีร้านค้าจริงช่วง Hackathon)
- ร้านจำลอง: **"ร้านน้ำพริกแม่บุญเรือน OTOP นครปฐม"**
- สินค้าจริง 10–15 รายการใน Google Sheets
- บันทึกวิดีโอ: **Happy Path + Exception Path**

### Budget

| รายการ | Hackathon | Production |
|---|---|---|
| LLM API | $0 (Gemini Free Tier) | ≤ หลักร้อยบาท/เดือน |
| Hosting | $0 (Render/Railway Free Tier) | ≤ $5–10/เดือน |
| Google Sheets | $0 | $0 |
| LINE OA | $0 (Free plan) | $0–590฿/เดือน |
| **รวม** | **$0** | **≤ หลักร้อยบาท/เดือน** |

### Risk Mitigation

#### Risk 1: LLM Hallucination

| มาตรการ | รายละเอียด |
|---|---|
| **Strict Negative Constraints** | Prompt บังคับ: ตอบเฉพาะข้อมูลในแคตตาล็อก ไม่มี → "ขอประสานเจ้าหน้าที่ฯ" |
| **Rule-Based Hybrid Check** | ราคา/ค่าส่ง/ยอดรวม ใช้ Deterministic Logic (ไม่ให้ LLM คิดเลข) |
| **Human-in-the-Loop** | ข้อความยอดเงิน/คำสั่งซื้อ ต้องแอดมิน Approve เสมอ |

#### Risk 2: PDPA & Privacy

| มาตรการ | รายละเอียด |
|---|---|
| **Data Minimization** | เก็บเฉพาะข้อมูลจำเป็น (ชื่อ, ที่อยู่, ยอดเงิน) |
| **Zero Training Retention** | ไม่ส่งข้อมูลสนทนาไปเทรนโมเดล |
| **Auto-Purge** | ลบข้อมูลส่วนบุคคลหลังจัดส่งเสร็จ |
| **Privacy Notice** | แจ้งใน Rich Menu ว่าระบบใช้ AI |

### Feasibility Verdict

| Dimension | Rating |
|---|---|
| Technical Feasibility | 🟢 Go |
| Resource & Capability | 🟢 Go |
| Timeline Feasibility | 🟢 Go (Conditional) |
| Budget/Cost | 🟢 Go |
| Regulatory (PDPA) | 🟢 Go (with safeguards) |
| **Overall** | **🟢 GO** |

---

## Stage 4 — Scope Definition

### 🟢 MVP Features — Must-Have (ทำใน Hackathon)

| ID | Feature | Description | Priority |
|---|---|---|---|
| F1 | **Catalog Ingestion** | ดึงข้อมูลจาก Google Sheets (6 คอลัมน์) → inject เข้า System Prompt | Must-Have |
| F2 | **AI Draft Reply** | ลูกค้าทักแชท → AI ร่างข้อความตอบกลับ (ภาษาไทย สุภาพ เป็นกันเอง) | Must-Have |
| F3 | **Order Summary & Calculation** | คำนวณยอดรวม + ค่าส่ง ด้วย Deterministic Logic | Must-Have |
| F4 | **Admin Approve UI** | Web App ให้แอดมินเห็น Draft → กด Approve/Edit/Reject | Must-Have |
| F5 | **Human Attention Tag** | คำถามซับซ้อน/ต่อรอง → แจ้งเตือนแอดมิน | Must-Have |
| F6 | **Guardrails & Fallback** | Prompt Constraints + Fallback "ขอประสานเจ้าหน้าที่ฯ" | Must-Have |
| F7 | **Mock Pilot Demo** | ร้านจำลอง 1 ร้าน + สินค้า 10–15 รายการ + วิดีโอ | Must-Have |

### 🟡 Nice-to-Have (ทำถ้ามีเวลา)

| ID | Feature |
|---|---|
| N1 | Slip Verification (OCR อ่านสลิปโอนเงิน) |
| N2 | Multi-language (ภาษาถิ่น / English) |
| N3 | Analytics Dashboard (สถิติแชท/ยอดขาย/เวลาตอบ) |

### 🔴 Out of Scope

| ID | Feature | Reason |
|---|---|---|
| O1 | Facebook Messenger / IG DM | Meta App Review ใช้เวลานาน |
| O2 | Payment Gateway Integration | ต้อง Merchant Account |
| O3 | Full Inventory Management | ต้องเชื่อม POS/ERP |
| O4 | Voice Message Support | ต้องเพิ่ม STT pipeline |

### User Stories

| ID | User Story |
|---|---|
| US-1 | ในฐานะ **เจ้าของร้าน** ฉันต้องการ **อัปโหลดแคตตาล็อกสินค้าผ่าน Google Sheets** เพื่อที่ AI จะได้มีข้อมูลตอบลูกค้าโดยไม่ต้องตั้งค่ายุ่งยาก |
| US-2 | ในฐานะ **ลูกค้า** เมื่อฉัน **ทักแชทถามข้อมูลสินค้า** ฉันต้องการ **ได้คำตอบที่ถูกต้องและรวดเร็ว** ภายใน 1 นาที |
| US-3 | ในฐานะ **แอดมินร้าน** ฉันต้องการ **เห็นข้อความที่ AI ร่างให้ก่อนส่ง** เพื่อตรวจสอบความถูกต้องและกดส่งในคลิกเดียว |
| US-4 | ในฐานะ **แอดมินร้าน** เมื่อ **ลูกค้าถามคำถามซับซ้อน** ฉันต้องการ **ได้รับการแจ้งเตือนด่วน** เพื่อเข้ามาตอบเอง |
| US-5 | ในฐานะ **ลูกค้า** เมื่อฉัน **สั่งสินค้าหลายรายการ** ฉันต้องการ **เห็นสรุปยอดรวม+ค่าส่งที่ถูกต้อง** โดยไม่ต้องคำนวณเอง |

---

## Stage 5 — Team Formation

### Team Roster & Task Mapping

| Role | Responsibility | MVP Features Owned |
|---|---|---|
| **Backend & Webhook Dev** | เชื่อมต่อ LINE Messaging API, Webhook, Google Sheets API, Hosting (Render/Railway) | F1, F3 |
| **AI & Prompt Engineer** | ออกแบบ System Prompt, Guardrails, Negative Constraints, Fallback Logic, ทดสอบความแม่นยำ | F2, F5, F6 |
| **Frontend / UX Designer** | Rich Menu LINE, Admin Approve Web App (Approve/Edit/Reject), Wireframe สำหรับ Pitch | F4 |
| **Business & Pitching Lead** | Mock Pilot ร้านจำลอง, กรณีศึกษา, ตัวเลขผลกระทบ, สไลด์, วิดีโอเดโม | F7 |

### Collaboration Points

```
Backend ↔ AI       : System Prompt ต้องรับ Catalog Data จาก Google Sheets
Backend ↔ Frontend : Admin Approve UI ต้องเรียก API → ตกลง API Contract ก่อน
AI ↔ Business      : ทดสอบ Prompt กับ Scenario ร้านจำลอง → ปรับ Guardrails
Frontend ↔ Business: Wireframe/UI สะท้อน User Flow สำหรับเดโม
```

---

## Stage 6 — Rough Mockups

### User Flows (4 Flows)

#### Flow 1: 🟢 Happy Path — ถามสินค้า → ปิดการขาย

```
ลูกค้าทักแชท LINE OA
        │
        ▼
Webhook → FastAPI Backend
        │
        ▼
ดึงแคตตาล็อกจาก Google Sheets
        │
        ▼
Prompt Stuffing: ข้อความลูกค้า + แคตตาล็อก + System Prompt
        │
        ▼
Gemini 1.5 Flash → สร้าง Draft Reply
        │
        ▼
Deterministic Logic → คำนวณยอดรวม + ค่าส่ง
        │
        ▼
ส่ง Draft → Admin Dashboard + แจ้งเตือน
        │
        ├── ✅ Approve → ส่งข้อความถึงลูกค้าทันที
        ├── ✏️ Edit   → แก้ไข → กดส่ง
        └── ❌ Reject → พิมพ์ใหม่ หรือ ขอ AI ร่างใหม่
```

**Post-Sale Sub-Flow:**

```
ลูกค้าส่งสลิปโอนเงิน
        │
        ▼
AI ร่าง Draft: "ได้รับสลิปเรียบร้อยค่ะ จะจัดส่งภายใน..."
        │
        ▼
แอดมินกด Approve → ส่งยืนยัน + เลข Tracking
        │
        ▼
ระบบ Auto-Purge ข้อมูลส่วนบุคคลหลังจัดส่งเสร็จ
```

#### Flow 2: 🟡 Exception Path — คำถามซับซ้อน / ต่อรอง

```
ลูกค้าทักแชท (สั่งจำนวนมาก / ต่อรอง / สั่งผลิตพิเศษ / แพ้อาหาร)
        │
        ▼
Gemini วิเคราะห์ Intent → ตรวจพบคำถามซับซ้อน
        │
        ▼
Tag: 🔴 HUMAN ATTENTION
        │
        ├── AI ส่งข้อความอัตโนมัติ: "ขอประสานเจ้าของร้านฯ รอสักครู่ค่ะ"
        └── แจ้งเตือนด่วนไปแอดมิน + สรุปบริบท
                │
                ▼
        แอดมินตอบเอง
```

#### Flow 3: 🔵 Setup Flow — ตั้งค่าระบบครั้งแรก

```
Step 1: กรอกชื่อร้าน + คำทักทาย + โทนภาษา + สรรพนาม
Step 2: วาง Google Sheets URL → ระบบดึงข้อมูลอัตโนมัติ → Preview
Step 3: ตั้งค่าบัญชีธนาคาร + เงื่อนไขค่าส่ง + COD
Step 4: กดทดสอบระบบ → จำลองบทสนทนา
Step 5: ใส่ LINE Channel Access Token + Secret → Webhook URL อัตโนมัติ
        ↓
✅ พร้อมใช้งาน! (ภายใน 10 นาที)
```

#### Flow 4: 🟠 Catalog Update — อัปเดตสินค้า

```
เจ้าของร้านแก้ไข Google Sheets → Auto-Sync ทุก 5 นาที หรือกด 🔄 Refresh
→ AI ใช้ข้อมูลล่าสุดทันที
```

### Screen Mockups (7 หน้าจอ)

#### Screen 1: LINE OA — Rich Menu

```
┌──────────────┬──────────────┬────────────────┐
│   🛒 สินค้า   │   💬 ถามตอบ  │   📦 เช็คพัสดุ  │
│   ทั้งหมด     │   คำถามบ่อย  │   ติดตามสถานะ  │
├──────────────┴──────────────┴────────────────┤
│   📋 โปรโมชัน  │   🔔 แจ้งเตือน                 │
│   ประจำเดือน   │   สินค้าใหม่                   │
└──────────────┴───────────────────────────────┘
```

#### Screen 2: LINE OA Chat — Happy Path

```
👤 ลูกค้า: น้ำพริกกุ้งเสียบ 3 กระปุก กับน้ำพริกตาแดง 2 กระปุก ส่ง กทม. รวมเท่าไหร่คะ

🤖 AI (Approved): สวัสดีค่ะ 🙏 สินค้าทั้ง 2 มีพร้อมส่งค่ะ 😊
   🧾 สรุปออเดอร์:
   น้ำพริกกุ้งเสียบ  3 × 89 = 267 บาท
   น้ำพริกตาแดง    2 × 79 = 158 บาท
   ค่าส่ง กทม.            =  50 บาท
   ═══════════════════════
   💰 รวม: 475 บาท
   🏦 กสิกรไทย xxx-x-xx890-x
   โอนแล้วส่งสลิปมาได้เลยนะคะ 📸
```

#### Screen 3: LINE OA Chat — สินค้าหมด

```
👤 ลูกค้า: น้ำพริกเผากุ้งยังมีไหมคะ

🤖 AI (Approved): ขอโทษด้วยนะคะ 🙏 น้ำพริกเผากุ้งสินค้าหมดชั่วคราวค่ะ
   💡 แนะนำ:
   • น้ำพริกกุ้งเสียบ (89฿) ขายดีอันดับ 1 รสชาติใกล้เคียงค่ะ
   • น้ำพริกปลาร้าทรงเครื่อง (99฿) รสจัดจ้าน ลูกค้าชอบมากค่ะ
```

#### Screen 4: LINE OA Chat — Fallback (ไม่มีข้อมูล)

```
👤 ลูกค้า: มีน้ำพริกมะขามเปียกไหมคะ

🤖 AI (Approved): ขอบคุณที่สนใจค่ะ 🙏
   ตอนนี้ทางร้านยังไม่มีน้ำพริกมะขามเปียกในรายการค่ะ
   สินค้าที่มีตอนนี้:
   🌶️ น้ำพริกกุ้งเสียบ (89฿) · น้ำพริกตาแดง (79฿) · น้ำพริกปลาร้าฯ (99฿)
```

#### Screen 5: Admin Dashboard — Main View

```
┌──────────────────────────────────────────────────────────┐
│  🏪 Local Commerce Quick-Reply — Admin Dashboard          │
├─────────┬────────────────────────────────────────────────┤
│ MENU    │  📊 สรุปวันนี้                                   │
│ 🏠 หลัก  │  💬 24  │  ✅ 19  │  ⏳ 3  │  🔴 2             │
│ 💬 แชท  │────────────────────────────────────────────────│
│ 📦 สินค้า│  ⏳ PENDING APPROVAL                           │
│ ⚙️ ตั้งค่า│  ┌──────────────────────────────────────────┐ │
│ 📊 สถิติ │  │ 💬 คุณวิภา — ⏱️ 12 วิ.                     │ │
│         │  │ 📩 "น้ำพริกกุ้งเสียบ 3 + ตาแดง 2 ส่ง กทม." │ │
│         │  │ 🤖 Draft: รวม 475 บาท                      │ │
│         │  │ 📎 Sheets Row #5, #3                       │ │
│         │  │ [✅ Approve] [✏️ Edit] [❌ Reject]           │ │
│         │  └──────────────────────────────────────────┘ │
│         │  ┌──────────────────────────────────────────┐ │
│         │  │ 🔴 คุณประสิทธิ์ — HUMAN ATTENTION          │ │
│         │  │ ⚠️ ออเดอร์ 200 ชิ้น + ต่อรอง + ฉลากพิเศษ   │ │
│         │  │ [💬 ตอบเอง] [📋 ดูประวัติ]                   │ │
│         │  └──────────────────────────────────────────┘ │
└─────────┴────────────────────────────────────────────────┘
```

#### Screen 6: Admin Dashboard — Settings

- 🏪 ข้อมูลร้าน (ชื่อ, คำทักทาย, โทนภาษา, สรรพนาม)
- 📦 แคตตาล็อก (Google Sheets URL + Sync)
- 🏦 บัญชีธนาคาร (ธนาคาร, เลขบัญชี, COD)
- 📦 เงื่อนไขค่าส่ง (กทม./ตจว./ฟรีขั้นต่ำ/วันจัดส่ง)
- 🔔 การแจ้งเตือน (LINE Notify + Web Push)

#### Screen 7: Admin Dashboard — Analytics (Nice-to-Have)

- สถิติรายสัปดาห์: แชทรวม, เวลาตอบเฉลี่ย, อัตราปิดขาย, AI ถูกต้อง %
- กราฟแชทรายวัน
- สินค้าขายดี Top 3

### Customer Journey Maps

#### Persona 1: แม่บุญเรือน — เจ้าของร้าน (อายุ 52)

```
  Awareness       Onboarding      Daily Use       Value           Advocacy
  ─────────       ──────────      ─────────       ─────           ────────
  สมาชิกกลุ่ม      ตั้งค่าร้าน      ลูกค้าทักแชท     ดูสถิติ          แนะนำเพื่อน
  OTOP แนะนำ      เชื่อม Sheets    AI ร่าง Draft   สรุปยอดขาย      ร้านค้าในกลุ่ม
                  ทดสอบ           กด Approve      เวลาที่ประหยัด

  😟 กังวล         😮 ประหลาดใจ     😊 สบายใจ       🤩 ตื่นเต้น      🥰 ภูมิใจ
  "AI จะยากไหม"   "ง่ายกว่าที่คิด!" "ไม่ต้องกลัว    "ประหยัดเวลา    "ช่วยเพื่อน
                                   บอทตอบผิด"     ได้เยอะเลย!"    ด้วยกัน"
```

#### Persona 2: คุณวิภา — ลูกค้า (อายุ 35)

```
  Discovery       Inquiry         Response        Purchase        Retention
  ─────────       ───────         ────────        ────────        ─────────
  เห็นโพสต์ FB     ทักแชท LINE OA  ได้ Draft Reply  โอนเงิน+สลิป    ได้ของ ประทับใจ
  Add LINE OA     ถามราคา+ค่าส่ง  สรุปยอดถูกต้อง                   สั่งซ้ำ

  ⏱️ Before: > 30 นาที (Drop-off 30-50%)
  ⏱️ After:  < 1 นาที (ตอบทันที ลูกค้าอยู่)
```

---

## Stage 7 — Approval & Handoff

### Approval Status: ✅ APPROVED

Initiative Brief ได้รับการอนุมัติครบถ้วนทุกส่วน

### Assumption Confirmation Gate

| # | Assumption | Status |
|---|---|---|
| A1 | Drop-off rate 30–50% เมื่อตอบช้าเกิน 15–30 นาที | ✅ Accepted |
| A2 | 70/30 split ระหว่าง Transactional vs Consultative | ✅ Accepted |
| A3 | ร้านค้าชุมชนมีสินค้า 10–50 รายการ | ✅ Accepted |
| A4 | Gemini 1.5 Flash Free Tier เพียงพอสำหรับ Hackathon | ✅ Accepted |
| A5 | แอดมินสามารถ Approve ภายใน 30–45 วินาที | ✅ Accepted |
| A6 | เจ้าของร้านอายุ 50+ ตั้งค่าได้ภายใน 10 นาที | ✅ Accepted |

### Go / No-Go Verdict: ✅ GO

- **Technical:** ทุก Component พร้อมใช้งาน ไม่มี dependency ที่ block
- **Team:** 4 คน สกิลครบ ตรงกับ Tech Stack
- **Budget:** $0 ช่วง Hackathon
- **Market:** 15,000–25,000 กิจการ target, คู่แข่งมีจุดอ่อนชัด 4 ด้าน
- **Risk:** 3 ความเสี่ยงหลัก ทั้งหมดมีมาตรการครบ

### Handoff Checklist

| # | Deliverable | Status |
|---|---|---|
| 1 | Problem Statement + Evidence | ✅ |
| 2 | Market Research + Competitive Analysis | ✅ |
| 3 | Technical Feasibility + Risk Mitigation | ✅ |
| 4 | MVP Scope + User Stories | ✅ Approved |
| 5 | Team Formation + Task Mapping | ✅ |
| 6 | Mockups + Flows + Journey + Design Principles | ✅ |
| 7 | Initiative Brief | ✅ Approved |
| 8a | Content Document (Markdown) | ✅ |
| 8b | Summary Presentation (HTML) | ✅ |

---

## Stage 8a — Content Document

Content Document (Markdown) ฉบับสมบูรณ์ถูกสร้างขึ้นจากข้อมูล Carry-Forward ทุก Stage ประกอบด้วย **17 sections**:

1. Overview
2. Problem Statement (รวม Customer Journey — Current State)
3. Solution Summary (รวม Participant's Verbatim + 4 Differentiators)
4. Confirmed Parameters (Decision Table ทุกรายการ)
5. Competitive Landscape (6 คู่แข่ง + Market Size)
6. Feasibility Assessment (5 Dimensions — ทั้งหมด GO)
7. Screens & Flows (4 Flows + 7 Screens)
8. Architecture / How It Works (System Diagram + Data Flow)
9. Scope (MVP 7 Features + Nice-to-Have 3 + Out of Scope 4)
10. Success Criteria (4 KPIs + Definition of Done)
11. Team Composition (4 คน + Task Mapping + Collaboration Points)
12. Timeline (4 Phases)
13. Key Risks & Mitigations (3 Risks + มาตรการครบ)
14. Open Assumptions (6 ข้อ — ทั้งหมด Accepted)
15. Decision Log (14 Decisions + Corrections Log)
16. Go / No-Go (✅ GO + Conditions)
17. Evidence & Sources (Source Summary + Unverified Claims)

### Source Citation Summary

| Source Type | Count |
|---|---|
| `[source: user input]` | ข้อมูลส่วนใหญ่ |
| `[source: participant — verbatim]` | 2 |
| `[source: assumption]` | 4 |
| `[source: synthesized from user input]` | 3 |
| `[source: workflow log]` | 1 |

📄 **ดาวน์โหลด Content Document ฉบับเต็ม:** ดูในไฟล์ `content-document.md`

---

## Stage 8b — Summary Presentation

Summary Presentation (HTML) ถูก render เป็น Interactive Slides ประกอบด้วย:

- **Slide 1:** Overview — ชื่อโปรเจกต์, Vision, Status
- **Slide 2:** Problem Statement — สถิติ, Drop-off rate, Conversational Commerce
- **Slide 3:** Solution Summary — 70/30 split, 4 จุดแตกต่าง
- **Slide 4:** Confirmed Parameters — ตาราง Tech Decisions
- **Slide 5:** Competitive Landscape — 6 คู่แข่ง, Pain Points, Market Size
- **Slide 6:** Feasibility Assessment — 5 Dimensions → GO
- **Slide 7:** System Flow — Happy Path + Exception Path diagrams
- **Slide 8:** LINE Chat Wireframes — Happy Path + Escalate phone mockups
- **Slide 9:** Admin Dashboard Wireframe — Pending Queue, HITL cards
- **Slide 10:** Architecture — System diagram, Sheets Schema, Tech Decisions
- **Slide 11:** Scope — MVP Features table, Nice-to-Have, Out of Scope

📄 **ดาวน์โหลด Presentation:** ดูในไฟล์ `presentation.html`

---

## Getting Started

### Prerequisites

- Python 3.10+ หรือ Node.js 18+
- LINE Official Account + Developer Console
- Google Account (สำหรับ Sheets + Gemini API)
- [ngrok](https://ngrok.com/) (สำหรับ Local Development)

### Quick Setup (< 10 นาที)

```bash
# 1. Clone repository
git clone https://github.com/your-team/local-commerce-quick-reply.git
cd local-commerce-quick-reply

# 2. Install dependencies
pip install -r requirements.txt

# 3. Set environment variables
cp .env.example .env
# แก้ไข .env:
#   LINE_CHANNEL_ACCESS_TOKEN=xxx
#   LINE_CHANNEL_SECRET=xxx
#   GEMINI_API_KEY=xxx
#   GOOGLE_SHEETS_URL=xxx

# 4. Start server
uvicorn main:app --reload --port 8000

# 5. Start ngrok (terminal อีกหน้าต่าง)
ngrok http 8000

# 6. Copy ngrok HTTPS URL → LINE Developer Console → Webhook URL
# 7. ทดสอบทักแชท LINE OA ของคุณ!
```

### Google Sheets Template

สร้าง Google Sheets ตาม Schema นี้:

| Item_Name | Price | Stock_Status | Description | Shipping_Rate | FAQ |
|---|---|---|---|---|---|
| น้ำพริกกุ้งเสียบ | 89 | พร้อมส่ง | เผ็ดกลาง 200g | กทม.50 ตจว.70 | เก็บได้ 6 เดือน มี อย. |
| น้ำพริกตาแดง | 79 | พร้อมส่ง | เผ็ดมาก 200g | กทม.50 ตจว.70 | เก็บได้ 6 เดือน มี อย. |
| น้ำพริกปลาร้าทรงเครื่อง | 99 | พร้อมส่ง | เผ็ดน้อย 250g | กทม.50 ตจว.70 | เก็บได้ 3 เดือน มี อย. |

---

## Project Structure

```
local-commerce-quick-reply/
├── README.md                    ← คุณอยู่ที่นี่
├── content-document.md          ← Stage 8a: Content Document ฉบับเต็ม
├── presentation.html            ← Stage 8b: Summary Presentation (HTML)
├── .env.example                 ← Environment variables template
├── requirements.txt             ← Python dependencies
├── main.py                      ← FastAPI application entry point
├── app/
│   ├── __init__.py
│   ├── webhook.py               ← LINE Webhook handler
│   ├── llm.py                   ← Gemini 1.5 Flash integration
│   ├── catalog.py               ← Google Sheets catalog ingestion
│   ├── calculator.py            ← Deterministic order calculation
│   ├── classifier.py            ← Intent classifier (Transactional vs Consultative)
│   ├── guardrails.py            ← Prompt constraints & fallback logic
│   └── notifier.py              ← LINE Notify + Web Push notifications
├── admin/
│   ├── index.html               ← Admin Dashboard UI
│   ├── settings.html            ← Shop settings page
│   └── static/
│       ├── style.css
│       └── app.js
├── prompts/
│   ├── system_prompt.txt        ← Main system prompt template
│   ├── guardrails.txt           ← Negative constraints
│   └── escalation_rules.txt     ← Human Attention tag rules
├── tests/
│   ├── test_calculator.py       ← Unit tests for order calculation
│   ├── test_classifier.py       ← Intent classification tests
│   └── test_scenarios/
│       ├── happy_path.json      ← Test scenarios: Happy Path
│       └── exception_path.json  ← Test scenarios: Exception Path
├── demo/
│   ├── mock_catalog.json        ← ร้านน้ำพริกแม่บุญเรือน mock data
│   └── demo_video_script.md     ← Script for demo video
└── docs/
    ├── api_contract.md          ← Backend ↔ Frontend API spec
    ├── stage1_carry_forward.md
    ├── stage2_carry_forward.md
    ├── stage3_carry_forward.md
    ├── stage4_carry_forward.md
    ├── stage5_carry_forward.md
    └── stage6_carry_forward.md
```

---

## Design Principles

### หลักการออกแบบ 7 ข้อ

| # | Principle | Design Rule |
|---|---|---|
| 1 | 🤝 **Copilot, Not Autopilot** | AI ร่างข้อความ แต่คนตัดสินใจส่งเสมอ — ปุ่ม Approve ต้องเป็นปุ่มใหญ่ที่สุด |
| 2 | 🪶 **Radical Simplicity** | ทุก Feature ต้องผ่านคำถาม *"แม่บุญเรือนใช้เองได้ไหม?"* |
| 3 | 🎯 **Accuracy Over Speed** | ตัวเลขทุกตัวต้องมาจากตาราง ไม่ใช่จาก LLM |
| 4 | 🗣️ **Authentic Local Voice** | อ่านข้อความแล้วรู้ว่าเป็นบอท → Prompt ต้องแก้ใหม่ |
| 5 | ⚡ **Speed That Converts** | ลูกค้าทักถึงตอบกลับ ≤ 1 นาที |
| 6 | 🔒 **Privacy by Default** | PDPA = Data Minimization + Zero Training + Auto-Purge |
| 7 | 💸 **Community-Affordable** | ทุก Decision ต้องผ่านคำถาม *"ร้านน้ำพริกจ่ายไหวไหม?"* |

### Design Principles → Features Matrix

| Principle | F1 Catalog | F2 AI Draft | F3 Order Calc | F4 Admin UI | F5 Escalate | F6 Guardrails |
|---|---|---|---|---|---|---|
| 🤝 Copilot | | ✅ | | ✅ | ✅ | ✅ |
| 🪶 Simplicity | ✅ | | | ✅ | | |
| 🎯 Accuracy | ✅ | | ✅ | ✅ | | ✅ |
| 🗣️ Local Voice | | ✅ | ✅ | | ✅ | |
| ⚡ Speed | ✅ | ✅ | ✅ | ✅ | ✅ | |
| 🔒 Privacy | | | | | | ✅ |
| 💸 Affordable | ✅ | ✅ | ✅ | | | ✅ |

---

## Timeline (Hackathon)

| Phase | Duration | Activities | Owner |
|---|---|---|---|
| **Phase 1: Setup** | Day 1 AM | สมัคร LINE OA, ngrok, Google Sheets, Repo + Deploy | Backend, Business |
| **Phase 2: Core Dev** | Day 1 PM – Day 2 AM | Webhook + Prompt (Backend+AI), Admin UI (Frontend), Guardrails (AI) | All |
| **Phase 3: Integration** | Day 2 PM | เชื่อมทุก Component, ทดสอบ Happy + Exception Path | All |
| **Phase 4: Demo** | Day 2 Eve – Day 3 | วิดีโอเดโม, สไลด์, ซ้อม Pitch | Business + All |

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- **AI for All Thailand Innovation Sprint** — โอกาสในการสร้างนวัตกรรมเพื่อชุมชน
- **ร้านค้า OTOP และวิสาหกิจชุมชนไทย** — แรงบันดาลใจในการแก้ปัญหาจริง
- **LINE Messaging API** — ช่องทางเข้าถึงผู้ใช้ไทย
- **Google AI Studio (Gemini)** — LLM ที่ทำให้ AI เข้าถึงได้สำหรับทุกคน

---

<p align="center">
  สร้างด้วย ❤️ เพื่อร้านค้าชุมชนไทย<br>
  <strong>AI for All Thailand Innovation Sprint 2026</strong>
</p>
