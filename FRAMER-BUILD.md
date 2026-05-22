# Joint & Bone Institute — Framer Build Guide

Direction A "Deep Ocean" — final handoff, migrated to Framer.

Framer is React-based, which means the existing JSX (`direction-a.jsx`) ports almost 1:1 as Framer **Code Components**. Two build paths below — pick based on how much time you have.

---

## Path A — Fast path (no-code, ~3 hours)

Build the site using Framer's native layout tools. Reference `index.html` for visual specs.

## Path B — Power path (code components, ~6 hours)

Paste the JSX from `components/direction-a.jsx` directly into Framer Code Components. Identical visual match to the mockup.

**Recommended: Start with Path A. Drop to Path B only for interactive pieces (body map, chatbot).**

---

## 0. Project setup

1. Go to [framer.com](https://framer.com) → sign in.
2. Click **New Project** → **Blank site**.
3. Name it `jbi-website`.
4. Framer auto-assigns a `.framer.website` subdomain. Custom domain comes later (any paid plan).

### Plan required
- **Free**: build + preview only, no publishing.
- **Mini** ($10/mo): publish with framer.website subdomain.
- **Basic** ($15/mo): custom domain + CMS.
- **Pro** ($30/mo): CMS with more items, password protection, analytics.

For JBI: **Basic plan** minimum (you need CMS for Conditions/Surgeons and a custom domain).

---

## 1. Upload assets (drag-and-drop works for SVG!)

In Framer → **Assets panel** (left sidebar) → **Upload**:

| File | Upload as | Notes |
|---|---|---|
| `logo/jbi-logo-final.svg` | Asset | Primary logo — rename to `logo-primary` |
| `logo/jbi-logo-final-inverted.svg` | Asset | Footer logo — rename to `logo-inverted` |
| `logo/favicon-512.png` | Favicon | Settings → Site Settings → Favicon |
| Hero + section photos | Asset | Organize into `/photos/hero`, `/photos/surgeons`, etc. |

Framer accepts SVG natively — no Squarespace-style security blocks.

---

## 2. Typography — Design → Typography

1. Click **Design** tab → **Typography**.
2. Click **+ Add Font** → search **Roboto Slab** → add weights `500`, `700`, `900`.
3. Click **+ Add Font** → search **Archivo** → add weights `400`, `500`, `600`, `700`, `800`.
4. Create text styles:

| Style name | Font | Weight | Size | Line height | Letter spacing |
|---|---|---|---|---|---|
| `Display / H1` | Roboto Slab | 900 | 96px | 0.96 | -3.5px |
| `Display / H2` | Roboto Slab | 900 | 52px | 1.02 | -1.6px |
| `Display / H3` | Roboto Slab | 700 | 28px | 1.2 | -0.5px |
| `Body / Large` | Archivo | 400 | 19px | 1.6 | 0 |
| `Body / Default` | Archivo | 400 | 16px | 1.5 | 0 |
| `Eyebrow` | Archivo | 700 | 11px | 1 | 2px, UPPERCASE |
| `Button` | Archivo | 700 | 13px | 1 | 1.2px, UPPERCASE |
| `Accent / Italic` | Roboto Slab | 500 Italic | inherit | inherit | 0 |

These become reusable across every text element.

---

## 3. Brand colors — Design → Colors

Framer lets you define **unlimited** color tokens (unlike Squarespace's 5-swatch cap).

Click **Design → Colors → + Add Color** for each:

| Token | Hex | Use |
|---|---|---|
| `--deep` | `#0F2D4F` | Primary navy |
| `--deep-dark` | `#081A30` | Footer bg |
| `--mid` | `#2E5A87` | Secondary blue |
| `--soft` | `#6B8BAE` | Muted blue |
| `--warm` | `#F5EFE3` | Hero ivory |
| `--bone` | `#EAE2D2` | Alt bg |
| `--stone` | `#D9CFBD` | Muted accent |
| `--gold` | `#C89A3A` | Primary CTA |
| `--gold-deep` | `#A37A27` | Accent rules, hover |
| `--text` | `#1A1F2A` | Body copy |
| `--muted` | `#6A6558` | Meta text |
| `--line` | `rgba(15,45,79,0.16)` | Borders |

Once saved, you can reference these anywhere in the Framer design panel via the color picker → Styles tab.

---

## 4. Site structure — Pages panel

In Framer's **Pages** sidebar, create:

```
/                         Home
/about                    About
/conditions               Conditions (landing)
/conditions/[slug]        Condition detail (CMS)
/surgeons                 Surgeons (landing)
/surgeons/[slug]          Surgeon bio (CMS)
/resources                Patient Resources
/journal                  Journal (CMS)
/journal/[slug]           Article (CMS)
/for-physicians           Referring physician portal
/request-appointment      Booking page
/contact                  Contact
/privacy                  Legal
/hipaa                    HIPAA notice
/accessibility            A11y statement
/404                      Not found
```

For CMS-driven pages, you'll create the Collection next (§5).

---

## 5. CMS Collections — Content tab

Framer's CMS is where JBI wins big over Squarespace. Set up three collections:

### Collection: `Conditions`
Fields:
- `title` (Plain text)
- `slug` (URL slug)
- `region` (Option: Knee, Hip, Shoulder, Spine, Hand, Foot, Sports)
- `summary` (Plain text, 1 line)
- `symptoms` (Rich text)
- `diagnosis` (Rich text)
- `treatment_options` (Rich text)
- `recovery_timeline` (Rich text)
- `hero_image` (Image)
- `featured_surgeon` (Reference → Surgeons)

### Collection: `Surgeons`
Fields:
- `name` (Plain text)
- `title` (Plain text — e.g., "Knee & Sports Medicine")
- `fellowship` (Plain text)
- `education` (Rich text)
- `specialties` (Multi-option)
- `bio` (Rich text)
- `portrait` (Image)
- `press` (Rich text)
- `stats` (JSON or repeater — procedures done, years practicing, etc.)

### Collection: `Journal`
Fields:
- `title`
- `slug`
- `tag` (Option: Recovery, Pre-Op, Non-Surgical, Research, News)
- `excerpt`
- `body` (Rich text)
- `author` (Reference → Surgeons)
- `read_time` (Number)
- `hero_image`
- `published_date`

Create 3–5 sample entries in each collection for design purposes.

---

## 6. Home page — section by section

Use Framer's **Fluid Engine-style** layout (stacks). Each section below maps to the markup in `index.html`.

### 6.1 Header (global component)

1. Create a new component: **Components → + New → JBI Header**.
2. Layout: horizontal stack, sticky.
3. Contents:
   - Announcement bar (navy, white text, utility info)
   - Logo (link to `/`) — use `logo-primary` SVG, height 60px
   - Nav items: About · Conditions ▾ · Surgeons · Patient Resources ▾ · For Physicians
   - CTA button: "Book Appointment" (gold pill, link to `/request-appointment`)
4. For dropdowns: use Framer's **Menu** component (Insert → Menu) with nested items.
5. Drop the Header component into every page's top slot.

### 6.2 Hero section

Two stacked rows:

**Row 1 — full-width photo banner (560px tall):**
- Frame with background image (hero photo)
- Overlay: linear gradient from rgba(8,26,48,0.22) top to var(--warm) bottom
- Top-left eyebrow: "— CALIFORNIA ORTHOPEDICS · EST. 1997"
- Bottom-left chip: green dot + "ACCEPTING NEW PATIENTS · SAME-WEEK CONSULTS"

**Row 2 — headline on warm ivory:**
- Background: `--warm`
- Grid 1.3fr / 1fr
- Left: H1 display "Strength, restored with *precision.*" (italic word in brass)
- Right: lede paragraph + 2 buttons (primary gold, ghost)
- Below: stats row (4 columns) with 2px navy top border

### 6.3 Body Map / Conditions

- Background: `--whisper` (ivory tint)
- Three columns:
  1. Title + lede
  2. Region selector (clickable list — use Framer **variants** on an Interactive Component)
  3. Detail card showing conditions for selected region
- **Interactive behavior**: Create an Interactive Component called `RegionSelector` with variants for each region (Knee, Hip, etc.). Wire click events to switch variant.
- Data source: pull from `Conditions` CMS collection, filter by `region` field.

### 6.4 Specialties — 4 cards

- Background: white
- 2×2 grid
- Each card: photo (4:5) + kicker (01–04) + H3 + body + "Learn more →" link
- Use Framer's **Stack** with gap: 24px

### 6.5 Surgeons — dark section

- Background: radial gradient `#0F2D4F → #081A30`
- Add noise texture overlay (upload grain PNG as background-image with opacity 0.4)
- 4-column grid
- Each card: portrait (3:4) + name + title + fellowship
- Data source: `Surgeons` CMS collection (limit 4, sort by `featured` field)

### 6.6 Journal — 3 articles

- Background: `--warm`
- Grid: 2fr / 1fr / 1fr
- 1 featured article + 2 compact
- Data source: `Journal` CMS (limit 3, sort by `published_date` desc)

### 6.7 Referring physician CTA band

- Background: `--deep` with brass radial glow top-right
- Grid: 1.2fr / 1fr
- Left: H2 "Referring a patient? *Direct line.*" + body
- Right: 2 buttons (primary gold + ghost white)

### 6.8 Footer (global component)

- Create: **Components → + New → JBI Footer**
- Background: `--deep-dark`
- 4 columns: Logo block / Care / Patients / Visit
- Bottom bar with legal links
- Use `logo-inverted` SVG

---

## 7. Interactive pieces (Code Components)

Some features are easier as pasted React code. Framer allows this via **Code Components**.

### How to add a code component:
1. In Framer, click the **Code** tab (top nav).
2. Click **+ New Code File** → name it (e.g., `BodyMap.tsx`).
3. Paste React/TSX code.
4. Drag the component into any page.

### Components worth porting from `direction-a.jsx`:

| Component | Priority | What it does |
|---|---|---|
| `ABodyMap` | High | Interactive anatomy selector with condition list |
| `ChatDrawer` | Medium | AI Care Guide chatbot drawer |
| `InsuranceChecker` | Medium | Insurance eligibility checker form |
| `StatsRow` | Low | Just a styled grid — easier to rebuild in Framer |

For each: open `direction-a.jsx`, copy the component function, paste into a Framer code file, replace `React.useState` imports with Framer's import pattern:

```tsx
import { useState } from "react"
import { addPropertyControls, ControlType } from "framer"

export default function BodyMap(props) {
  const [selected, setSelected] = useState("knee")
  // ... rest of the original JSX
}
```

---

## 8. Responsive breakpoints

Framer has native breakpoints. In the canvas:

1. Click the **device picker** (top-right) → enable **Tablet** (810px) and **Phone** (390px).
2. For each section, override layout at each breakpoint:
   - Hero H1: 96px → 64px tablet → 44px phone
   - Grid columns: 4-col → 2-col → 1-col on phone
   - Nav: collapse to hamburger on phone (Framer's Menu component handles this automatically)

---

## 9. Forms (appointment requests, contact, referral)

Framer's native **Form component** works for simple forms. For anything touching PHI:

- **Don't use Framer forms for medical intake** — not HIPAA-compliant.
- Embed a HIPAA-compliant provider via an Embed block:
  - **NexHealth** (scheduling + intake)
  - **Phreesia** (intake + insurance)
  - **Jotform HIPAA** (custom forms, BAA available)

For the "Request an appointment" page: embed NexHealth's scheduler via iframe.

---

## 10. Publishing

1. Click **Publish** (top-right in Framer editor).
2. First publish: uses `yoursite.framer.website` subdomain (free tier).
3. Custom domain: **Site Settings → Domains → + Add Custom Domain**.
   - Point DNS A record to Framer's IP (shown in settings).
   - Framer handles SSL automatically.
4. Every subsequent publish takes ~30 seconds.

---

## 11. What to do RIGHT NOW — checklist

1. ☐ Sign up at framer.com, create `jbi-website` project
2. ☐ Upload all logo SVGs + favicon
3. ☐ Add Roboto Slab (500/700/900) and Archivo (400/500/600/700/800)
4. ☐ Set up 12 brand color tokens
5. ☐ Create the 3 CMS Collections (Conditions, Surgeons, Journal)
6. ☐ Build Header + Footer as reusable components
7. ☐ Build Home page top-to-bottom using `index.html` as visual reference
8. ☐ Create stub pages for About, Conditions landing, Surgeons landing, Resources, For Physicians
9. ☐ Add 3–5 sample CMS entries per collection
10. ☐ Connect NexHealth/Jotform for appointment + contact forms
11. ☐ Enable Tablet + Phone breakpoints, pass mobile QA
12. ☐ Connect custom domain, publish

---

## 12. Why Framer > Squarespace for this project

| Feature | Squarespace | Framer |
|---|---|---|
| SVG upload | Limited / blocked | ✅ Native |
| Color tokens | 5 swatches | Unlimited |
| Custom fonts | OK (UI heavy) | ✅ Fast, full control |
| React/JSX reuse | ❌ No | ✅ Direct paste |
| CMS | OK | ✅ More flexible, faster |
| Animations | Limited | ✅ Native, powerful |
| Custom CSS | Buried, Business plan only | ✅ Built-in |
| Learning curve | Low | Medium |
| Price | $23/mo+ | $15/mo+ |

---

## 13. Migration of existing assets

You already have:
- `index.html` — full visual reference (don't touch, use as specs)
- `logo/jbi-logo-final.svg` + `logo/jbi-logo-final-inverted.svg` — upload directly
- `logo/favicon-*.png` — upload as favicon
- Unsplash placeholder photo URLs in `index.html` — swap for licensed/real photography before launch

**Next step I can help with:** Want me to generate a Framer-ready Code Component file for the Body Map (the highest-value interactive piece), so you have it ready to paste when you reach §7?
