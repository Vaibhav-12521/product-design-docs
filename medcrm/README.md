# medcrm — Customer Relations Wireframes

Modern, clean, minimalist wireframes for the **Customer Relations module** that slots into your live `app.medstocksy.in`. 10 frames, all in the same design language as your actual app (read from `D:\Medstocksy Projects\Medstocksy-inventory`).

This is the visual layer of the **Medstocksy Connect** PRD — the same product spec'd in `wire/medstocksy_connect_prd.md` and `wire/medstocksy_connect_rules.md`, but redrawn in the design language of your existing inventory app instead of a separate theme.

---

## 🧬 Why these match your live app

I read these files from `Medstocksy-inventory` to nail the language:

| File | What it told me |
|------|----------------|
| `tailwind.config.ts` | shadcn/ui CSS-variable theming, sidebar tokens, radius scale |
| `src/index.css` | Primary `217 91% 60%` (= `#3B82F6`), 12 px radius, 48 px touch targets, sidebar gradient `0 0% 98%` → `240 4.8% 95.9%`, 16 px base font, 18 px buttons |
| `src/components/Layout.tsx` | Sidebar with `bg-gradient-to-b from-sidebar to-sidebar-accent`, brand-header tile, `lucide-react` icons, route list pattern |

So the medcrm wireframes use **your tokens, not a separate theme**:
- Primary: `#3B82F6`  (matches `hsl(217 91% 60%)`)
- Active item: `#EFF6FF` background + 3 px primary bar (mirrors your `sidebar-accent`)
- Sidebar gradient: `#FAFAFA → #F4F4F5`
- Card radius: 12–20 px (lg from your config)
- Section eyebrow text: 11 px, uppercase, `#A1A1AA` letter-spacing 1
- Type: Inter (defaults from shadcn) · JetBrains Mono for numerals

---

## 📂 Frames in this folder

| # | File | Page | Demonstrates |
|---|------|------|--------------|
| 01 | `01-dashboard.svg` | CRM Dashboard | KPIs, ambient WhatsApp health, upcoming reminders feed, segment quick-access |
| 02 | `02-customers.svg` | Customers directory | Black "All" pill + neutral chips, avatar-led table, multi-tag rows |
| 03 | `03-customer-profile.svg` | Customer profile | Hero identity (no card), stat strip with separator lines, timeline + insights rail |
| 04 | `04-segments.svg` | Segments | 6 fixed segments as 220 px tiles · one black "premium" tile for High Value · explainer at bottom |
| 05 | `05-compose.svg` | WhatsApp compose drawer | Right-rail drawer · template + variables · WhatsApp-style green preview · sticky safety footer |
| 06 | `06-reminders.svg` | Reminder rules | List + dark inline editor · constraints visible at rest |
| 07 | `07-campaigns.svg` | Campaigns list | Status-coded cards (scheduled / sent / draft) · attribution metrics |
| 08 | `08-campaign-wizard.svg` | Campaign wizard step 2 | Stepper · template radio cards · Recommended badge · live preview · safety checklist |
| 09 | `09-templates.svg` | Templates library | 6-card grid · pre-built / custom split · WhatsApp green preview · usage metrics |
| 10 | `10-activity.svg` | Activity stream | Global event feed · color-coded dots · day-grouped headers · 90-day audit retention |

Total: **10 SVG frames + README**.

---

## 🎨 Minimalist principles applied

These wireframes are deliberately **lighter** than your earlier Connect wireframes:

1. **No drop shadows** — borders only. Your live app uses subtle borders, not card shadows.
2. **Surface tiles instead of bordered cards** for KPIs (`#FAFAFA` fill, no border) — gives breathing room without visual noise.
3. **Stat strips with horizontal separator lines** instead of metric tiles in the customer profile.
4. **One dark accent tile per screen** (the "High Value" segment, the dashboard's "Delivery Rate", the reminder editor) — high-contrast moment that anchors the eye.
5. **Pill-shaped buttons (44 px height, 22 px radius)** — softer than my earlier 10 px-radius rectangles, closer to the current Tailwind shadcn defaults.
6. **More whitespace** — frames are 1440 × 900 (your real screen size) so density is lower.
7. **Section eyebrow labels** in tracked uppercase (11 px / `#A1A1AA`) — replaces decorative section borders.
8. **Sidebar uses subtle gradient** (matches your `Layout.tsx` gradient pattern exactly).

---

## 🚀 Import into Figma (3 minutes)

1. Open Figma → **New design file**
2. Open this folder in File Explorer
3. **Select all 10 SVGs** (Ctrl+A, deselect this README)
4. Drag onto the Figma canvas
5. Right-click → **Tidy up** for auto-grid layout

Each `<g id="...">` group becomes a properly named Figma layer (sidebar, header, kpis, timeline, etc.) — easy to extract components from.

---

## 🔗 How this fits with the rest of `wire/`

| Folder | What's there | Relationship |
|--------|--------------|--------------|
| `wire/medstocksy_connect_prd.md` + `_rules.md` | Spec for the CRM module | **Source** for these wireframes |
| `wire/medstocksy_connect_wireframes.html` | Earlier Connect wireframes (theme-applied) | First-pass · superseded by these for live-app integration |
| `wire/wireframes-medstocksy-app/` | The parent inventory app's pages | The 8 frames the CRM **plugs into** |
| `wire/wireframes-figma/` | Other GitHub repos redesigned | Side portfolio · same theme family |
| `wire/medcrm/` *(this folder)* | **CRM module · matches live app** | Production-ready visual spec |

The full picture for a recruiter: **8 inventory pages + 10 CRM pages = 18-frame design package** describing an entire pharmacy OS.

---

## 🪧 What this set demonstrates

Beyond the obvious (UI/UX, wireframing, design systems), these frames demonstrate three judgment calls worth pointing out in interviews:

1. **The CRM was designed to slot *into* an existing app** — same sidebar tokens, same radius scale, same primary color. Most junior portfolios pick a fresh theme per project; integrating into a real product is harder and more honest.
2. **WhatsApp constraints are baked into layout, not error states** — the rate-limit meter, send-window pill, and opt-in badge are persistent UI (compose footer, dashboard right rail), not modal warnings.
3. **The segment palette is fixed at 6** — no custom-segment builder in V1. This is a constraint-led design choice straight from the PRD's Rule 5 (10-minute learning).

---

## 📤 Sharing options

### Option A — Bundle with live app
Add the live app URL to your portfolio caption: *"Customer Relations module · designed for [medstocksy.in](https://medstocksy.in)"*. The link gives the design real-world credibility.

### Option B — Combined Figma file
Make a single Figma file with two pages:
- *Inventory app* (the 8 frames in `wireframes-medstocksy-app/`)
- *CRM module · medcrm* (these 10 frames)

That's the **full pharmacy OS** in one shareable Figma URL.

### Option C — Case study on portfolio
Pair with `wire/upload/medstocksy-connect/CASE-STUDY.md` and post both as a single design case study on `vaibhav1.me`.

---

Built by Vaibhav Singh · Lucknow, India · Full-Stack Web Developer
