# Joint & Bone Institute — Squarespace Build Playbook

Direction A "Deep Ocean" · Final implementation.
Living document — updated as the build progresses.

---

## Site identity

| Item | Value |
|---|---|
| Practice name | Joint & Bone Institute of California |
| Tagline | California Orthopedic Surgeons |
| Locations | Bakersfield · Delano · Potterville |
| Phone | 661.544.3352 |
| Hours | Mon–Fri 8:00 a.m – 5 p.m |

---

## Brand tokens

### Color palette (Squarespace 5-swatch system)

| Swatch | Hex | Role |
|---|---|---|
| 1 | `#FFFFFF` | White (Lightest sections) |
| 2 | `#F5EFE3` | Warm Ivory (Light sections) |
| 3 | `#EAE2D2` | Bone (alt backgrounds) |
| 4 | `#0F2D4F` | Deep Navy (Dark sections, headings) |
| 5 | `#081A30` | Deep Dark (Footer) |

### Accent colors (applied via Custom CSS, not palette)

| Name | Hex | Used for |
|---|---|---|
| Aged Brass | `#C89A3A` | Primary CTAs, BOOK NOW button |
| Brass Deep | `#A37A27` | Accent rules, italic accents, hover states |
| Stone | `#D9CFBD` | Muted accents, italic display words |
| Muted Text | `#6A6558` | Meta text, captions |

### Typography

| Element | Font | Weight | Size | Letter-spacing |
|---|---|---|---|---|
| Headings (H1–H4) | Roboto Slab | 900 Black | varies | -0.02em |
| Body | Archivo | 400 | 16px | 0 |
| Buttons | Archivo | 700 | 13px | 1.2px UPPERCASE |
| Eyebrows / kickers | Archivo or Roboto Slab | 700 | 11–16px | 2–3.5px UPPERCASE |
| Italic accent words | Roboto Slab | 500 italic | inherit | 0 |

---

## Logo files (in `/logo/` folder)

| File | Use |
|---|---|
| `jbi-logo-final.svg` | Master logo SVG (full lockup) |
| `jbi-logo-squarespace.svg` | Cleaned SVG without external font imports (for Squarespace upload) |
| `jbi-logo-final-inverted.svg` | Inverted lockup for dark backgrounds (footer) |
| `logo-full.png` | 1400×560 PNG render — used in Squarespace Logo & Title |
| `favicon.svg` | Simple JBI navy square SVG |
| `favicon-512.png` | 512×512 PNG favicon — used in Browser Icon setting |
| `render-for-export.html` | Browser-renderable preview for capturing PNGs |
| `_logo-render.html` / `_favicon-render.html` | Headless Chrome render sources |

---

## Squarespace plan

**Required: Business plan or higher.** Custom CSS + Code Injection are gated behind Business tier.

---

## Section paths in Squarespace

| Setting | Path |
|---|---|
| Site title + tagline | Settings ⚙ → General |
| Favicon (Browser Icon) | Settings ⚙ → General → Browser Icon |
| Color palette | Website → Styles → Colors → Edit Palette |
| Fonts | Website → Styles → Fonts |
| Buttons | Website → Styles → Buttons |
| Logo | Design → Logo & Title |
| Custom CSS | Pages → (scroll to bottom) → Custom Code → Custom CSS |
| Code Injection | Pages → Custom Code → Code Injection (Header / Footer) |
| Header layout | Edit site → pencil on header → Layout tab |
| Announcement bar | Edit site → pencil at top |

---

## Custom CSS — paste this into Pages → Custom Code → Custom CSS

```css
/* ===== Headings — Roboto Slab 900 ===== */
h1, h2, h3, h4 {
  font-family: 'Roboto Slab', Georgia, serif !important;
  font-weight: 900 !important;
  letter-spacing: -0.02em;
  color: #0f2d4f;
}

/* ===== Body — Archivo ===== */
body, p, li {
  font-family: 'Archivo', -apple-system, sans-serif !important;
  color: #1a1f2a;
}

/* ===== Primary button (gold CTA) ===== */
.sqs-button-element--primary {
  background: #c89a3a !important;
  color: #081a30 !important;
  font-family: 'Archivo', sans-serif !important;
  font-weight: 700 !important;
  letter-spacing: 1.5px !important;
  text-transform: uppercase !important;
  font-size: 13px !important;
  border-radius: 2px !important;
  padding: 16px 26px !important;
  display: inline-flex !important;
  align-items: center !important;
  gap: 12px !important;
  transition: all 0.25s ease !important;
}
.sqs-button-element--primary::after {
  content: "→";
  font-size: 16px;
  font-weight: 700;
  transition: transform 0.25s ease;
  display: inline-block;
}
.sqs-button-element--primary:hover {
  background: #a37a27 !important;
  transform: translateY(-2px);
  box-shadow: 0 10px 24px rgba(200,154,58,0.35);
}
.sqs-button-element--primary:hover::after {
  transform: translateX(6px);
}

/* ===== Secondary button (ghost, navy border) ===== */
.sqs-button-element--secondary {
  background: transparent !important;
  color: #0f2d4f !important;
  border: 1.5px solid #0f2d4f !important;
  font-family: 'Archivo', sans-serif !important;
  font-weight: 700 !important;
  font-size: 13px !important;
  letter-spacing: 1.5px !important;
  text-transform: uppercase !important;
  border-radius: 2px !important;
  padding: 14.5px 26px !important;
  position: relative;
  overflow: hidden;
  transition: all 0.25s ease !important;
}
.sqs-button-element--secondary::before {
  content: "";
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: #0f2d4f;
  transform: translateX(-100%);
  transition: transform 0.3s ease;
  z-index: -1;
}
.sqs-button-element--secondary:hover {
  color: #f5efe3 !important;
}
.sqs-button-element--secondary:hover::before {
  transform: translateX(0);
}

/* ===== Specialties blog cleanup ===== */
.blog-item-author-profile,
.blog-item-date-author,
.blog-item-author-date,
.entry-author,
.entry-date,
.author-name,
.published,
.blog-list-item-meta-item--date,
.entry-categories-comments,
.blog-meta-category,
.blog-meta-comments,
.blog-item-share,
.squarespace-social-buttons,
.comments,
.blog-item-comments,
.blog-item-pagination,
.blog-more-link {
  display: none !important;
}
.blog-basic-grid--container .blog-basic-grid--text {
  background: transparent;
  padding: 24px 0 0;
}
.blog-basic-grid--container .blog-title {
  font-family: 'Roboto Slab', serif !important;
  font-size: 24px !important;
  font-weight: 700 !important;
  color: #0f2d4f !important;
  letter-spacing: -0.4px !important;
}
.blog-meta-item--categories a {
  color: #a37a27 !important;
  font-size: 11px !important;
  letter-spacing: 1.5px !important;
  text-transform: uppercase !important;
  font-weight: 700 !important;
  text-decoration: none !important;
}

/* ===== Mega-menu overflow fix ===== */
.header, .header-inner, .header-nav, .header-actions,
.header-menu-nav-item, .header-menu-nav-item--external,
.header-nav-item, .header-nav-item--external,
.header-display-desktop, .header-title-nav-wrapper,
.header-announcement-bar-wrapper,
nav, [class*="nav-item"], [class*="header-menu"] {
  overflow: visible !important;
}

/* ===== Brass accent rule utility ===== */
hr.brass {
  border: 0;
  border-top: 2px solid #c89a3a;
  width: 40px;
  margin: 12px 0;
}
```

---

## Specialties Mega-Menu — Footer Code Injection

**Location:** Pages → Custom Code → Code Injection → **Footer**

```html
<style>
  .jbi-mega-host {
    position: relative !important;
    display: inline-block;
  }
  .jbi-mega {
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%) translateY(-12px);
    width: min(960px, 92vw);
    background: #ffffff;
    border-top: 3px solid #c89a3a;
    box-shadow: 0 24px 48px rgba(15,45,79,0.15);
    padding: 36px 44px 32px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 40px;
    opacity: 0;
    pointer-events: none;
    transition: opacity .25s ease, transform .25s ease;
    z-index: 99999;
    font-family: 'Archivo', sans-serif;
  }
  .jbi-mega-host:hover .jbi-mega,
  .jbi-mega:hover {
    opacity: 1 !important;
    pointer-events: auto !important;
    transform: translateX(-50%) translateY(0) !important;
  }
  .jbi-mega-col h4 {
    font-family: 'Roboto Slab', Georgia, serif;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 2.5px;
    text-transform: uppercase;
    color: #c89a3a;
    margin: 0 0 18px;
    padding-bottom: 12px;
    border-bottom: 1px solid rgba(15,45,79,0.1);
  }
  .jbi-mega-col a {
    display: block;
    padding: 9px 0;
    font-size: 14px;
    color: #1a1f2a;
    text-decoration: none;
    font-weight: 500;
    border-left: 2px solid transparent;
    transition: color .15s ease, padding-left .15s ease, border-color .15s ease;
  }
  .jbi-mega-col a:hover {
    color: #0f2d4f;
    padding-left: 10px;
    border-left-color: #c89a3a;
  }
  @media (max-width: 900px) {
    .jbi-mega { display: none !important; }
  }
</style>

<script>
(function(){
  function attachMega(){
    var link = document.querySelector('a[href="/specialties"]');
    if(!link) return false;
    if(link.dataset.jbiMegaAttached === '1') return true;

    link.removeAttribute('target');
    var host = link.parentElement;
    host.classList.add('jbi-mega-host');

    var mega = document.createElement('div');
    mega.className = 'jbi-mega';
    mega.innerHTML = `
      <div class="jbi-mega-col">
        <h4>Hip &amp; Knee</h4>
        <a href="/specialties/anterior-hip-replacement">Anterior Hip Replacement</a>
        <a href="/specialties/total-hip-replacement">Total Hip Replacement</a>
        <a href="/specialties/total-knee-replacement">Total Knee Replacement</a>
        <a href="/specialties/partial-knee-replacement">Partial Knee Replacement</a>
      </div>
      <div class="jbi-mega-col">
        <h4>Sports &amp; Regenerative</h4>
        <a href="/specialties/sports-medicine">Sports Medicine</a>
        <a href="/specialties/rotator-cuff-repair">Rotator Cuff Repair</a>
        <a href="/specialties/prp-injections">PRP Injections</a>
      </div>
      <div class="jbi-mega-col">
        <h4>Hand &amp; Fracture</h4>
        <a href="/specialties/carpal-tunnel-surgery">Carpal Tunnel Surgery</a>
        <a href="/specialties/trigger-finger">Trigger Finger</a>
        <a href="/specialties/fracture-care">Fracture Care</a>
        <a href="/specialties/wrist-arthritis">Wrist Arthritis</a>
      </div>
    `;

    host.appendChild(mega);
    link.dataset.jbiMegaAttached = '1';
    return true;
  }

  var attempts = 0;
  var interval = setInterval(function(){
    attempts++;
    if(attachMega() || attempts > 20){ clearInterval(interval); }
  }, 250);

  if(document.readyState === 'loading'){
    document.addEventListener('DOMContentLoaded', attachMega);
  } else {
    attachMega();
  }
})();
</script>
```

To add new specialties: append `<a href="/specialties/[slug]">[Title]</a>` lines to the appropriate column in `mega.innerHTML`. Save, refresh.

---

## Site structure

### Main navigation

```
About · Specialties ▾ · For Physicians · Patient Resources ▾ · 661.544.3352 · [BOOK NOW]
```

### Pages

| Path | Type | Status |
|---|---|---|
| `/` | Home | Live |
| `/about` | Page | Stub |
| `/specialties` | Blog (CMS) | Live |
| `/specialties/[slug]` | Blog post | 11 created (see below) |
| `/team` | Page | Stub |
| `/for-physicians` | Page | Stub |
| `/patient-resources` | Page | Stub |
| `/conditions` | Page (planned: body map) | Not yet built |
| `/request-appointment` | Page (booking) | Not yet built |

---

## Specialties content (Blog-as-CMS)

**Blog page**: `/specialties` — repurposed Squarespace Blog Page

### Categories

- `Hip & Knee`
- `Sports & Regenerative`
- `Hand & Fracture`
- `Featured` (used to surface posts on homepage)

### Posts created (11 of 18 planned)

#### Hip & Knee
- ✅ Anterior Hip Replacement → `/specialties/anterior-hip-replacement`
- ✅ Total Hip Replacement → `/specialties/total-hip-replacement`
- ✅ Total Knee Replacement → `/specialties/total-knee-replacement`
- ✅ Partial Knee Replacement → `/specialties/partial-knee-replacement`
- ☐ Robotic Joint Surgery
- ☐ ACL & Ligament Repair
- ☐ Meniscus & Cartilage

#### Sports & Regenerative
- ✅ Sports Medicine → `/specialties/sports-medicine`
- ✅ Rotator Cuff Repair → `/specialties/rotator-cuff-repair`
- ✅ PRP Injections → `/specialties/prp-injections`
- ☐ Arthroscopy
- ☐ Tendinitis & Bursitis
- ☐ Cartilage Restoration

#### Hand & Fracture
- ✅ Carpal Tunnel Surgery → `/specialties/carpal-tunnel-surgery`
- ✅ Trigger Finger → `/specialties/trigger-finger`
- ✅ Fracture Care → `/specialties/fracture-care`
- ✅ Wrist Arthritis → `/specialties/wrist-arthritis`
- ☐ Hand & Wrist Care
- ☐ Workplace Injuries

### Post template (apply to each)

Each post body should include these blocks:
1. **Hero block** (Code) — eyebrow + H1 + lede in warm ivory card
2. **Overview** (H2 + paragraph)
3. **When you might need this** (H2 + bulleted list)
4. **What to expect** (H2 + paragraph)
5. **Recovery timeline** (Code block — 4-step grid)
6. **Surgeons who treat this** (Code block — pill links)
7. **CTA button** — "Request a consultation" → `/request-appointment`

(Templates are in the chat history — copy from earlier messages.)

---

## Homepage sections (top to bottom)

| # | Section | Implementation | Status |
|---|---|---|---|
| 1 | Announcement bar | Squarespace native | ✅ Live |
| 2 | Header | Squarespace native + Custom CSS + mega-menu JS | ✅ Live |
| 3 | Hero | Squarespace banner + video background + native blocks | ✅ Live |
| 4 | Stats row | Hardcoded Code Block (`.jbi-stats`) | ✅ Live (4 stats: 27+ YRS, 9,400+, 99% PPOs/HMOs, 3 locations) |
| 5 | Team section | Hardcoded Code Block (`.jbi-team-wrap`, full-bleed) | ✅ Live (real staff: Dr. Pramod Srivastava, Dr. Karan Srivastava, Kelly Guzman PA) |
| 6 | Care We Provide | Hardcoded Code Block (`.jbi-care-wrap`, full-bleed, 3 cards) | ✅ Live (Hip & Knee · Sports & Regenerative · Hand & Fracture) |
| 7 | Patient Journal | Not yet built | ☐ Pending |
| 8 | Referring Physicians CTA | Not yet built | ☐ Pending |
| 9 | Footer | Squarespace native (default) | ⚠️ Needs custom 4-col footer to replace template default |

---

## Header configuration

- **Layout preset**: Logo Center
- **Logo**: `logo-full.png` (uploaded via Design → Logo & Title)
- **Logo height**: ~60–80px
- **Announcement bar**: navy background, ivory text — `Bakersfield · Delano · Potterville | Mon-Fri 8:00 a.m - 5 p.m | 661.544.3352`
- **Header button**: BOOK NOW (primary, gold) → links to `/request-appointment`
- **Phone in nav**: nav link `661.544.3352` → `tel:6615443352` (brass styling via CSS)
- **Account / Social Links**: disabled
- **Specialties dropdown**: custom mega-menu via Footer Code Injection (3 columns)

---

## Hero section

- **Background**: video (orthopedic surgeon, dark overlay 40%)
- **Eyebrow**: `— CALIFORNIA ORTHOPEDICS · EST. 1997` (top-left, white, spaced caps)
- **H1**: `Strength, restored with precision.` — `precision.` is italic + brass `#a37a27`
- **Lede**: California's trusted orthopedic surgeons...
- **Buttons**:
  - Primary gold: `Request an appointment` → `/request-appointment`
  - Secondary ghost: `Explore conditions` → `/conditions` (or `/specialties`)
- **Chip**: `● ACCEPTING NEW PATIENTS · SAME-WEEK CONSULTS` (bottom-left, white card with green dot)

---

## Stats section (Code Block)

Located in Code Block directly below hero. Class: `.jbi-stats`.

**Final stat copy:**
1. `27+ YRS` — of Care
2. `9,400+` — Procedures
3. `99% of` — PPOs and HMOs Accepted
4. `3 locations` — across Kern and Tulare County

**Top transition**: gradient fade (no border) blending into hero above. `margin-top: -20px` overlap.

---

## Team section (Code Block, full-bleed)

Class: `.jbi-team-wrap`. Pulls full viewport width using `100vw` break-out.

**Heading**: `Fellowship-trained.` *Patient-chosen.* (italic stone accent)
**CTA button (top-right)**: `Meet our team →` → `/team`
**Eyebrow**: `— THE TEAM` (16px, brass)
**Grid**: 3 cards (3 columns on desktop, stacks on mobile)
**Each card links to**: `/team`

### Real team members (currently live)
1. **Dr. Pramod Srivastava M.D** — COMPREHENSIVE ORTHOPEDIC SURGEON — Fellowship · Hospital for Special Surgery
2. **Dr. Karan Srivastava M.D** — JOINT REPLACEMENT SPECIALIST — Fellowship · Mayo Clinic
3. **Kelly Guzman** — PHYSICIAN ASSISTANT — Fellowship · Rutgers, The State University of New Jersey

Image swap: replace `<img src="https://images.unsplash.com/...">` URLs with Squarespace asset URLs once real headshots are uploaded.

---

## Care We Provide section (Code Block, full-bleed)

Class: `.jbi-care-wrap`. White background section between Team and Footer.

**Heading**: `The care` *we provide.* (italic brass)
**CTA button (top-right)**: `Explore all specialties →` → `/specialties`
**Eyebrow**: `— Specialties` (16px, mid-blue)
**Grid**: 3 specialty category cards

### Card structure
Each card: photo (16:10 aspect) + brass kicker (01 · Category) + navy slab title + body paragraph + "Explore →" link

### Cards (currently live)
1. **01 · Hip & Knee** — "Joint replacement & reconstruction." → `/specialties/total-knee-replacement`
2. **02 · Sports & Regenerative** — "Get back to active life." → `/specialties/sports-medicine`
3. **03 · Hand & Fracture** — "Precision care for hand & trauma." → `/specialties/carpal-tunnel-surgery`

**Note**: Card click links only fire in live preview / published site — NOT inside Squarespace's edit mode (Squarespace intercepts clicks for editing).

---

## To-do — remaining build work

### Immediate
- [ ] Apply blog cleanup CSS for podcast-style "Episodes / About / Donate" links
- [ ] Build remaining 7 specialty posts to fill out mega-menu
- [ ] Replace hardcoded Care section with Summary Block pulling Featured posts

### Short-term
- [ ] Mark 4 specialties as `Featured` category for homepage display
- [ ] Build `/request-appointment` page (Phreesia/NexHealth embed for HIPAA)
- [ ] Build `/about` page (practice story, locations, mission)
- [ ] Build `/team` page (surgeon bios)
- [ ] Build `/conditions` page (interactive body map — to be hardcoded)
- [ ] Polish `/specialties` blog page with hero header
- [ ] Add Patient Journal section to homepage (Summary Block from a Journal blog)
- [ ] Add Referring Physicians CTA band to homepage
- [ ] Build `/for-physicians` referral page

### Pre-launch
- [ ] Mobile responsive QA (every section, every page)
- [ ] SEO: page titles, meta descriptions, Open Graph images
- [ ] Connect Google Analytics 4
- [ ] Connect custom domain
- [ ] Verify SSL
- [ ] Set up HIPAA-compliant intake forms (NOT native Squarespace forms)
- [ ] Write privacy policy, HIPAA notice, accessibility statement
- [ ] Submit XML sitemap to Google Search Console

---

## Key technical decisions made

1. **Hardcoded code blocks vs Squarespace native** — used hardcoded for hero stats, team, care sections to escape template constraints. Trade-off: less editable in Squarespace UI, but pixel-perfect match to design system.

2. **Blog-as-CMS for Specialties** — used Squarespace Blog page + categories instead of building 18 separate pages. Trade-off: blog UI conventions need CSS overrides, but content is now editable in one place and Summary Blocks can pull from it dynamically.

3. **Custom mega-menu via Code Injection** — Squarespace's native dropdown is single-column. Custom JS attaches a 3-column mega-menu to the Specialties nav link by `href="/specialties"` selector.

4. **Logo as PNG, not SVG** — Squarespace's SVG security scanner blocked our SVG with `@import` Google Fonts. Rendered to PNG via Chrome headless with proper Roboto Slab fonts loaded.

5. **Phone in nav as a Link, not a button** — Squarespace template only allowed 1 header button (used for BOOK NOW). Phone added as nav link, styled brass with dot prefix.

---

## Files in this project folder

```
Website design/
├── index.html                          # Reference design (full visual spec)
├── enhanced-homepage.html              # Earlier iteration
├── preview-homepage.html               # Earlier iteration
├── SQUARESPACE-BUILD.md                # This file (build playbook)
├── FRAMER-BUILD.md                     # Alternative Framer build path (abandoned)
└── logo/
    ├── jbi-logo-final.svg              # Master logo SVG
    ├── jbi-logo-squarespace.svg        # Squarespace-safe SVG
    ├── jbi-logo-final-inverted.svg     # Inverted for dark backgrounds
    ├── logo-full.png                   # Header logo PNG (1400×560)
    ├── favicon.svg                     # Favicon SVG
    ├── favicon-512.png                 # Favicon PNG (uploaded to Squarespace)
    ├── render-for-export.html          # Browser-renderable preview
    ├── _favicon-render.html            # Headless render source
    └── _logo-render.html               # Headless render source
```
