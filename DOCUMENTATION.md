# Andy Suth Psychology — Website Documentation

Internal reference for how the site is built, hosted, and maintained.
_Last updated: August 5, 2026_

---

## 🌐 Live site
- **URL:** https://andysuthpsychology.org
- **SSL/https:** Active
- **Favicon:** Inline SVG — forest-green tile with italic "AS" monogram

---

## 🚀 Hosting & deployment

The site is deployed via **Netlify**, connected to **GitHub**. Pushing to the GitHub repo automatically triggers a new Netlify deploy.

| What | Where |
|------|-------|
| **GitHub repo** | https://github.com/maan-sacdalan-llc/andysuthpsychology |
| **Netlify project** | https://app.netlify.com/projects/andysuthpsychology/overview |
| **Domain registrar** | GoDaddy (DNS points to Netlify) |

### To publish an update
1. Get the new `index.html` (and any other files) from the designer.
2. Commit/push them to the GitHub repo above.
3. Netlify auto-deploys within ~1 minute. Check the Netlify dashboard for build status.

### Files in the repo root
- `index.html` — the entire website (single self-contained file — all fonts, images, styles, and code are inlined)
- `sitemap.xml` — lists the homepage for search engines
- `robots.txt` — allows all crawlers, points to the sitemap

---

## 📄 Site structure (all one page, JS-navigated)
- **Home** — hero, credentials strip, services grid, approach, CTA
- **About** — bio, career timeline, education & credentials, memberships
- **Services** — overview grid → 6 detail pages:
  - Child & Adolescent Neuropsychological Assessment
  - Adult Neuropsychological Assessment
  - Neurodiversity Assessment
  - Diagnostic Assessment
  - Psychotherapy for Adults
  - ADHD Across the Lifespan
- **Fees & Insurance** — rate ranges + superbill/insurance note
- **Contact** — offices, phone, email, and working form
- **Footer** — nav, contact info, copyright

---

## ✉️ Contact form

- **Service:** FormSubmit (https://formsubmit.co) — free, no account needed
- **Delivers to:** contact@suthpsychology.org
- **⚠️ Activation:** The FIRST form submission on the live site sends a one-time confirmation email to contact@suthpsychology.org. Click that link once to start receiving messages.
- Fires a `contact_form_submit` event to the dataLayer on success (for analytics conversion tracking).

---

## 📊 Analytics — Google Tag Manager / Google Analytics

- **Google Tag Manager container ID:** `GTM-WG5984DD`
- Installed high in the `<head>` (plus the `<noscript>` fallback).
- **To view traffic:** Google Analytics → Reports (visits, page views, sources, locations).
- **Conversion tracking (form submissions):** In GTM, create a trigger on the Custom Event named `contact_form_submit` and forward it to GA as a conversion / key event.
- **Verify tracking:** Use GTM Preview mode, or watch GA → Realtime while visiting the site.

---

## 🔍 SEO / AEO (answer-engine optimization)

Built into `index.html`:
- **Structured data (schema.org JSON-LD):**
  - Psychologist / MedicalBusiness / LocalBusiness (both offices, phone, email, services, area served)
  - Person entity for Dr. Suth (credentials, degrees, licenses, memberships)
  - FAQPage with 5 Q&As (services, location, insurance, fees, getting started)
- **Meta tags:** title, description, canonical (https), robots, Open Graph, Twitter cards
- **sitemap.xml** submitted to Google Search Console

### Recommended next steps (off-page)
- Claim a **Google Business Profile** for each office (Carmel + Monterey) — big for local/AI search
- Expand FAQ schema as real client questions come in

---

## 🎨 Design reference
- **Fonts:** Cormorant Garamond (headlines/display), Mulish (body/UI)
- **Palette:** Paper `#F4F2EA` · Card `#EAE7DC` · Ink `#28352D` · Forest `#3C5142` · Sage `#6F8A63` · Clay `#9A6F4E` · Gold `#C9A97E`
- **Source file:** `Suth Psychology.dc.html` (the editable master — `index.html` is generated/bundled from this)

---

## 🏢 Practice details (as shown on site)
- **Name:** Andy Suth, Ph.D. and Associates
- **Phone:** 831-233-1121
- **Email:** contact@suthpsychology.org
- **Offices:**
  - Carmel — 3771 Rio Road, Suite 111
  - Monterey — 200 Camino Aguajito, Suite 205
- **Licenses:** CA PSY33640 · IL 071-006431
