# Medstocksy Connect — Design System & Wireframes

> A WhatsApp-driven CRM module for [Medstocksy](https://medstocksy.in) (pharmacy SaaS).
> This repository is the **design package** — PRD, design rules, theme spec, and interactive wireframes.
> No code yet; this is the work that comes *before* code.

[![Status](https://img.shields.io/badge/status-design_complete-3ECF8E?style=flat-square)](#)
[![Live parent](https://img.shields.io/badge/parent_product-medstocksy.in-2563EB?style=flat-square&logo=googlechrome&logoColor=white)](https://medstocksy.in)
[![License](https://img.shields.io/badge/license-MIT-0F172A?style=flat-square)](LICENSE)

---

## 📦 What's in here

| File | What it is | Why it matters |
|------|------------|----------------|
| [`docs/PRD.md`](docs/PRD.md) | 12-section Product Requirements Document | Scope, goals, user flows, message templates, success metrics |
| [`docs/DESIGN-RULES.md`](docs/DESIGN-RULES.md) | 19 strategic rules for product decisions | Constraint-led thinking — what to reject and why |
| [`docs/THEME.md`](docs/THEME.md) | Complete design system spec | Colors, type, spacing, components, anti-patterns |
| [`wireframes/index.html`](wireframes/index.html) | 9 interactive wireframes | Open in any browser — no build step |
| [`CASE-STUDY.md`](CASE-STUDY.md) | Narrative writeup of the design process | The "why" behind every decision |

---

## 🎯 The problem

Pharmacies in India lose ~30–50% of customers after their first visit. They don't need a "CRM" — they need:

1. **Repeat customers** (refill reminders)
2. **Simple WhatsApp communication** (where customers actually are)
3. **Staff automation** (counter staff don't have time for software)

But WhatsApp has hard rate limits and account-suspension risk. Pharmacy staff can spare **<10 minutes** for training. So the design has to be ruthless.

---

## 🧭 The approach

This repo is structured as the artifacts of a real product-design process:

```
1. PRD              →  What we're building, for whom, with what guardrails
2. Design Rules     →  Strategic filter for "should this feature exist?"
3. Theme / System   →  Visual language (colors, type, components, motion)
4. Wireframes       →  Concrete screens, interaction states, edge cases
```

Each artifact is a **gate**: if a feature can't pass the rules, the wireframe never gets drawn.

---

## 🔑 Key design decisions

These came directly out of the rules + theme:

- **One dominant CTA per screen** — one Send / one Save / one Continue. Secondary actions step back.
- **Tag palette capped at 6** — `New`, `Repeat`, `High Value`, `Inactive`, `Chronic`, `OptOut`. Adding a 7th requires product approval.
- **WhatsApp constraints are ambient UI** — the rate-limit meter, send-window pill, and opt-in badge live in the layout at rest, not just on error.
- **Desktop-first, mobile companion** — bulk operations and configuration are desktop-only. Mobile is read-only + quick send.
- **No charts on the dashboard** — only single-value metric tiles, per a deliberate "Speed > Perfection" rule.
- **Locked `+91` prefix in phone fields** — phone is the customer primary key; predictability beats novelty.

---

## 🎨 Wireframes

Open [`wireframes/index.html`](wireframes/index.html) in a browser and use the top tabs (or ← / → arrow keys) to navigate.

| # | Frame | What it shows |
|---|-------|---------------|
| 01 | Dashboard | Owner home, 6 metric tiles, ambient WhatsApp health panel |
| 02 | Customers list | Search + 6 segment chips, compact 48 px rows |
| 03 | Customer profile | Stat strip, recent bills, full activity timeline |
| 04 | WhatsApp compose | Highest-stakes UI — rate meter, send window, opt-in badge baked into layout |
| 05 | Campaign wizard | 3-step flow: Segment → Template → Schedule |
| 06 | Reminder rules | Admin-only desktop view with per-medicine cycle config |
| 07 | Add customer sheet | 2 required fields, the rest collapsed |
| 08 | Mobile companion | 3 mobile screens — read-only + quick send |
| 09 | Theme reference | Color tokens, button variants, anti-patterns |

All screens use only the tokens defined in [`docs/THEME.md`](docs/THEME.md) — no off-palette color, no new component patterns.

---

## 🛠️ Tech direction (when implementation starts)

| Layer | Choice | Rationale |
|-------|--------|-----------|
| Frontend | React + TypeScript + Tailwind + shadcn/ui | Fast iteration, component reuse, accessibility built-in |
| Backend | Supabase (Postgres + Auth + Realtime) | Lean ops, RLS for multi-tenant safety |
| Hosting | Vercel | Zero-config, edge functions |
| WhatsApp | Twilio / Meta Business API | Compliance, rate limiting, webhooks |
| Scheduler | Supabase Cron / Vercel Crons | Trigger reminders, scheduled sends |

---

## 📚 Skills demonstrated by this repo

- ✅ Product thinking (writing a PRD with measurable goals)
- ✅ Constraint-led design (rules document)
- ✅ Design system creation (color tokens, type scale, component patterns)
- ✅ Wireframing (9 desktop + mobile frames)
- ✅ User-flow design (customer onboarding, campaign wizard, reminder rules)
- ✅ Accessibility considerations (WCAG-AA contrast, 44 px touch targets, focus rings)
- ✅ Cross-platform thinking (desktop-first with intentional mobile companion scope)

---

## 👤 Author

**Vaibhav Singh** — Full-Stack Web Developer
🌐 [vaibhav1.me](https://vaibhav1.me/) ·
💼 [LinkedIn](https://www.linkedin.com/in/vaibhavsingh125/) ·
📧 [singh12521vaibhav@gmail.com](mailto:singh12521vaibhav@gmail.com)

## 📄 License

MIT — see [LICENSE](LICENSE).
