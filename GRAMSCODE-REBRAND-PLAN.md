# gramscode Website Rebrand Plan

## Context
The project is a Framer-exported static HTML website currently branded as "AgencyGTM" — a B2B outbound infrastructure agency template. The goal is to rebrand it for **gramscode**, a UK-focused AI-powered GTM agency that builds automated outbound systems for B2B companies. There are 17 HTML files across the site (7 main pages + 6 blog posts + 4 case studies). "AgencyGTM" appears 41 times across all files.

The user has confirmed:
- They will provide a gramscode logo image file
- The testimonial slideshow photos will be replaced with **real client photos** (user will provide)

---

## Task 1 — Logo Swap (All 17 Pages)

**What to change:**
- The logo image file: currently `Eobfhywuzq0ios9TwHDnirPcdok.png` (compass/star icon). Replace with the gramscode logo file the user provides.
- All text occurrences of `AgencyGTM` in the nav logo label → `gramscode`
- Favicon references: same image file swap

**Files affected:** All 17 HTML files in `agencygtm.framer.website/`

**Approach:** Since the HTML is Framer-generated minified markup, use `str_replace_all` on each file to:
1. Replace `>AgencyGTM<` (nav text nodes) → `>gramscode<`
2. Replace the logo `src` attribute pointing to `Eobfhywuzq0ios9TwHDnirPcdok.png` with the new logo filename
3. Copy the user-provided logo file into `framerusercontent.com/images/`

---

## Task 2 — Testimonial Slideshow Photo Replacement (index.html)

**Current state:** The "50+ brands have upgraded with us" section shows 5 placeholder personas:
- Selectors: Randy Jackson (CEO, Teampay), Sophia Liu (CTO, InnovateX), Carlos Gomez (Marketing, BrightWave), Aisha Rahman (Product, NexusCorp)
- Featured: Raman Desai (CEO, Teampay)

**What to change:**
- User will provide real client photos (up to 5 images)
- Replace each photo `src` with the new image filename
- Replace each person's name, title, company with real client details
- Update the featured testimonial quote text and attribution

**Files affected:** `agencygtm.framer.website/index.html` only

**Approach:** Locate the inline JSON/HTML block for each testimonial card and do targeted replacements.

---

## Task 3 — Content Rebrand for gramscode (All Pages)

### A. Global text replacements (all 17 files)
| Old text | New text |
|---|---|
| `AgencyGTM` | `gramscode` |
| `AgencyGTM — B2B Outbound Infrastructure for GTM Agencies` | `gramscode — AI-Powered GTM for B2B Agencies` |
| `We build the ICP, messaging, and outbound infrastructure...` (meta description) | `gramscode builds the AI-powered outbound infrastructure that turns cold contacts into qualified pipeline. Email, LinkedIn, and calls.` |

### B. Homepage-specific changes (index.html)

| Section | Current | Proposed gramscode version |
|---|---|---|
| Tag pill | "For B2B Brands" | "For UK Agencies" |
| Hero heading | "We map your B2B market and then own it." | "We build your AI-powered outbound machine." |
| Hero sub-copy | "AgencyGTM builds the outbound infrastructure..." | "gramscode builds the AI-powered outbound infrastructure that replaces hope with a repeatable system. From ICP definition to qualified meetings on the calendar." |
| Comparison table header | "AgencyGTM" column | "gramscode" column |
| Stats | "500+ Qualified Meetings Booked / 15+ Countries Impact" | Update to gramscode's real numbers (ask user, or keep as aspirational) |
| CTA headline | "Build a predictable outbound pipeline in 90 days." | "Build a predictable AI outbound pipeline in 90 days." |
| "50+ brands..." | "50+ brands have upgraded with us" | Update to real gramscode social proof number |

### C. Team/Founder section (index.html + about.html)
- "Marcus Webb, Founder AgencyGTM" → replace with gramscode founder name/bio/photo
- Update the 4 supporting team member photos + names
- Update stats: "0+ Years of experience / $0M+ Worth pipeline generated" → real gramscode numbers

### D. Footer (all pages)
- "AgencyGTM builds the outbound infrastructure..." description → gramscode description
- "Copyright © 2026 AgencyGTM" → "Copyright © 2026 gramscode"
- Update LinkedIn and social links to gramscode's actual accounts

### E. About page (about.html)
- Update founder story: replace "Marcus Webb spent six years leading sales teams at two Series B SaaS companies..." with gramscode's founder background

### F. Blog posts (6 files in blogs/)
- Update author attribution and any inline "AgencyGTM" brand mentions to gramscode

### G. Case studies (4 files in case-studies/)
- The 4 case studies (Meridian Consulting, NovaScale AI, PeakGrowth Agency, RevStack) are fictional placeholders — leave the client names as-is for now (they're generic enough) but update all "AgencyGTM" references to gramscode within them

---

## Execution Order
1. Get logo file from user (GitHub link or local drop)
2. Replace logo image file + all logo text across all 17 pages
3. Make global `AgencyGTM` → `gramscode` text replacements across all 17 pages
4. Update homepage-specific content (hero, stats, comparison table, CTAs, footer)
5. Update founder/team section on index.html and about.html
6. Get real client photos from user → swap into testimonial slideshow
7. Update blog posts and case study author refs

---

## Verification
- Open `http://localhost:8765/index.html` in browser (server already running on port 8765)
- Confirm logo appears correctly in navbar
- Scroll through full homepage to confirm all text shows "gramscode"
- Check slideshow section for real client photos
- Open about.html, contact.html, case-studies.html to confirm logo + footer updated
- Check a blog post and a case study page for consistent branding
