# Medstocksy Connect Design Case Study

A narrative writeup of how this design package was produced, what the constraints were, and why each major decision was made.

---

## 1. Context

[Medstocksy](https://medstocksy.in) is a live pharmacy inventory + sales SaaS I built. Customer churn was the next problem to solve  pharmacies in India lose 30–50% of customers after their first visit, and existing CRM tools don't fit their reality (counter staff can't learn enterprise software in <10 minutes; WhatsApp is the only channel customers actually use).

I had to design the next-phase **CRM module** before writing any code. This repo is what came out of that.

---

## 2. The brief I wrote myself

> **Build a customer-repeat system for pharmacies that drives 20–30% more repeat visits without adding staff workload, using WhatsApp as the primary channel  and make it learnable in 10 minutes.**

Three KPIs locked the brief:
- Repeat customer rate: **+20–30%**
- Manual follow-up reduction: **80%**
- Time-to-first-message after billing: **<2 minutes**

---

## 3. Constraints that shaped every decision

| Constraint | What it forced |
|------------|---------------|
| WhatsApp rate limits (10/hr, suspension risk) | Rate-limit meter as **ambient UI**, not error state |
| Pharmacy staff = non-technical, 10-min training cap | Pre-built segments (no filter builder), one CTA per screen, max 3 screens per task |
| Phone = primary key (no email culture) | Locked `+91` prefix in forms, phone-based dedup |
| Bulk sends >100 = real-world risk | Modal blocker + admin approval gate |
| Mobile = staff phones in a busy counter | Read-only + quick send only; configuration desktop-only |

These constraints became the **design rules**  every feature has to pass them or it doesn't ship.

---

## 4. The artifact stack (what I produced, in order)

### 4.1 PRD ([docs/PRD.md](docs/PRD.md))
12 sections covering scope, customer fields, message templates, segmentation logic, WhatsApp safety guardrails, success metrics, and risk mitigation. Wrote this *before* any visual.

### 4.2 Design Rules ([docs/DESIGN-RULES.md](docs/DESIGN-RULES.md))
19 strategic rules  each with a Why and a How-to-apply line. The rules are a **filter**: if a feature request can't pass them, it doesn't reach wireframes. Examples:

- *Rule 5  The 10-Minute Rule:* every feature must be learnable in <10 minutes.
- *Rule 9  WhatsApp Compliance:* every messaging feature must include rate limit + opt-out + audit + bounce monitoring or be rejected.
- *Rule 13  Core Loop Protection:* if a feature doesn't support `Bill → Customer → WhatsApp → Reminder → Repeat`, it's deferred to V2.

### 4.3 Theme spec ([docs/THEME.md](docs/THEME.md))
The visual language. Color tokens, type scale, spacing, radii, shadows, component patterns, motion, accessibility rules. Mapped directly to **shadcn/ui** CSS variables so it drops into a real React project.

Notable opinionated calls:
- **Trust Blue (`#2563EB`) + Care Green (`#10B981`)**  clinical without feeling cold
- **Tag palette capped at 6**  adding a 7th requires product approval; prevents the "tag color drift" failure mode
- **Tabular numerals** on every metric  stops dashboard tiles from jittering as values update
- **Motion budget: 120–200 ms, ease-out only**  no decorative animation

### 4.4 Wireframes ([wireframes/index.html](wireframes/index.html))
9 navigable frames in a single self-contained HTML file. Each frame uses **only the tokens from the theme spec**  that's the consistency check.

---

## 5. Six decisions worth justifying

### 5.1 One dominant CTA per screen
Pharmacy staff don't have time to scan. Every screen has exactly one primary button (`Send message`, `Save`, `Continue`). Secondary actions are outlined; tertiary actions are ghost-styled.

### 5.2 WhatsApp constraints rendered at rest, not on error
Most apps surface rate limits only when something fails. I baked the rate meter, send-window pill, and opt-in badge into the compose drawer's persistent footer. Staff see the constraint *before* they push too hard, which prevents the failure entirely.

### 5.3 Auto-tags suppressed in the Add Customer form
The auto-tags (`New`, `Repeat`, `Inactive`, `High Value`) are *derived* from activity. Showing them in the create form would invite confusion ("do I tick these?"). They're hidden until the customer has activity, then applied automatically.

### 5.4 No charts on the dashboard
The PRD calls for "minimal charts (simple bars/numbers only)." The dashboard ships with single-value metric tiles. If the owner wants depth, they click into the full reports page  V2.

### 5.5 Mobile is read-only + quick send only
Configuration (reminder rules, campaigns, settings) is desktop-only. The Rule 6 test: *"if the task needs >3 taps or >2 fields of input, it doesn't belong on mobile."* This kept the mobile UX honest  a glance + a one-tap response, not a shrunken desktop.

### 5.6 The bulk-send approval threshold = 100
Below 100 recipients, the campaign wizard shows a green checklist (4 ticks). Above 100, a hard modal blocks the send and routes to admin approval. The number is from the WhatsApp warm-up reality, not a guess.

---

## 6. Outcome

| Deliverable | Status |
|-------------|--------|
| PRD | ✅ Complete (12 sections) |
| Design Rules | ✅ 19 rules locked |
| Theme spec | ✅ Tokens, components, anti-patterns |
| Wireframes | ✅ 9 frames, navigable, theme-applied |
| Implementation | 🟡 Next step  slot into existing Medstocksy React + Supabase stack |

The design package alone is **review-ready**. A developer (me, in this case) can pick up `docs/THEME.md` + `wireframes/index.html` and start building shadcn/ui components without ambiguity.

---

## 7. What this case study demonstrates

If you're an employer skim-reading this:

- **Product thinking**  I scoped before I designed (PRD comes first)
- **Constraint-led design**  every rule has a why; rules filter features before wireframes
- **Design systems**  colors, type, components, motion, accessibility, anti-patterns
- **Wireframing**  desktop + mobile, interaction states, edge cases (opt-out, bulk-send block)
- **Pragmatism**  capped tag palette, no charts in V1, deferred features documented
- **Cross-functional thinking**  PRD reads like a product manager, theme reads like a designer, wireframes read like an engineer

I write code too  but this repo is the part of my work that AI screeners and recruiters tend to miss when they only look at language statistics.

---

## 8. Author

**Vaibhav Singh**  Full-Stack Web Developer
🌐 [vaibhav1.me](https://vaibhav1.me/) ·
💼 [LinkedIn](https://www.linkedin.com/in/vaibhavsingh125/) ·
📧 [singh12521vaibhav@gmail.com](mailto:singh12521vaibhav@gmail.com)
