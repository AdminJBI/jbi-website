# Code Blocks

Each `.html` file is a self-contained Squarespace **Code Block**. Drop the contents into a Code Block on the appropriate page and section.

## Current code blocks

| File | Lives on | Section position |
|---|---|---|
| `care-we-provide.html` | Homepage | After Team section, before Footer |
| `dr-karan-srivastava.html` | `/team/karan-srivastava` | Full page body (one Code Block) |
| `kelly-guzman.html` | `/team/kelly-guzman` | Full page body (one Code Block) |
| `post-op/post-operative-care.html` | `/specialties/post-operative-care` | Hub page body (one Code Block) |
| `post-op/injections.html` | `/specialties/injections` | Sub-page body (one Code Block) |
| `post-op/wound-care.html` | `/specialties/wound-care` | Sub-page body (one Code Block) |
| `post-op/pain-management.html` | `/specialties/pain-management` | Sub-page body (one Code Block) |
| `post-op/follow-up-care.html` | `/specialties/follow-up-care` | Sub-page body (one Code Block) |

## How to use

1. In Squarespace edit mode on the target page, **+ Add Section** → **Blank** → **+ Add Block** → **Code**.
2. Open the `.html` file from this folder.
3. Copy entire contents (including `<style>` block and HTML).
4. Paste into the Squarespace Code editor.
5. Make sure **Display Source** is UNCHECKED.
6. Save.

## Editing later

When you need to update content (e.g., swap a card's link, add a specialty), edit the `.html` file here, then copy + paste back into Squarespace. Keeping the source in git means you always have the canonical version to roll back to.

## Physician profile pages

Full-page Code Blocks (class `.jbi-doc`) for individual surgeon bios under `/team/<slug>`.
The block carries its own `<h1>` inside the hero, so **hide the Squarespace native page
title** (Page Settings → uncheck "Show page title" / "Header Display") to avoid a duplicate
H1. Still set the SEO Title in Page Settings → SEO for the browser tab and Google.

- `dr-karan-srivastava.html` — ✅ Live at `/team/karan-srivastava`
- `kelly-guzman.html` — ✅ Built for `/team/kelly-guzman` (needs real headshot)

Pending profiles (to build from the same `.jbi-doc` template):
- `dr-pramod-srivastava.html` — Comprehensive Orthopedic Surgeon

## Post-Operative Care (hub + sub-pages)

Lives in `post-op/`. Shared style class `.jbi-svc` (navy/brass/ivory, Archivo).
The canonical CSS is `post-op/_TEMPLATE-STYLE.html` — **not a page**; it's the
single source to edit, then paste the updated `<style>` into each page file.

Each page below is its own full-page Code Block (own `<h1>` → hide the native title):

- **Hub** — `post-op/post-operative-care.html` → `/specialties/post-operative-care`
  (links to the 4 service cards below)
- `post-op/injections.html` → `/specialties/injections`
- `post-op/wound-care.html` → `/specialties/wound-care`
- `post-op/pain-management.html` → `/specialties/pain-management`
- `post-op/follow-up-care.html` → `/specialties/follow-up-care`

Each sub-page cross-links the other three plus the hub via the sidebar.

## Sections not yet built (pending code blocks)

- `patient-journal.html` — homepage Patient Journal teaser (3 article cards)
- `referring-physicians-cta.html` — homepage navy CTA band for referrals
- `footer.html` — custom 4-column footer to replace Squarespace default
- `body-map.html` — interactive Conditions page anatomy selector
