# Andy Suth Psychology - Website Project

One-page clinical practice website for **Andy Suth, Ph.D. and Associates**, a licensed clinical psychology and neuropsychology practice on the Monterey Peninsula (Carmel and Monterey offices).

## Client

- **Andy Suth, Ph.D.** - Licensed Clinical Psychologist and Neuropsychologist (CA PSY33640, IL 071-006431)
- **Phone:** 831-233-1121
- **Email:** contact@suthpsychology.org (deployed), drandysuth@gmail.com, andy@suthpsychology.org
- **Offices:** 3771 Rio Road Suite 111, Carmel; 200 Camino Aguajito Suite 205, Monterey
- **Live site:** https://andysuthpsychology.org/

## Files in this folder

### Deployed version (primary deliverable)

| File | Purpose |
|---|---|
| `index.html` | Current production file, Framer DC export. Edit this one. |

### Alternate design directions (reference)

Two unused design concepts kept for comparison and future reference. These are hand-coded, not Framer exports.

| File | Design direction |
|---|---|
| `index-alt-look.html` | Rounded clinical. Slate-navy and ochre palette, bell-curve hero, folder-tab service cards. Zilla Slab + Work Sans. |
| `index-editorial-look.html` | Editorial monochrome. Fraunces display serif up to 96px, near-black on cream, single forest-green accent, hairline rules. |

### Logo assets

| File | Use |
|---|---|
| `logo-icon.svg` | Favicon and square mark, main design |
| `logo-horizontal.svg` | Horizontal lockup for header, main design |
| `logo-icon-alt.svg`, `logo-horizontal-alt.svg` | Marks for the rounded clinical alternate |
| `logo-icon-editorial.svg`, `logo-horizontal-editorial.svg` | Marks for the editorial alternate |

## Deployed file structure (`index.html`)

Single file, exported from a Framer-style Dynamic Component (DC) builder. Important things to know before editing:

- **Not a hand-coded HTML page.** Attributes use `sc-camel-*` prefixes (`sc-camel-on-click`, `sc-camel-view-box`). Preserve them exactly.
- **Sections are gated by `sc-if` conditionals** tied to page state (`isHome`, `isAbout`, `isServices`, `isChild`, `isAdultNeuro`, `isNeuro`, `isDiagnostic`, `isTherapy`, `isAdhd`, `isFees`, `isContact`). Routing logic lives in the `<script type="text/x-dc">` component at the bottom.
- **Fonts:** Cormorant Garamond (headings, italic accents), Mulish (body). Loaded via inlined `@font-face` with hashed asset filenames.
- **Palette:** `#f4f2ea` paper, `#28352d` ink, `#3c5142` and `#6f8a63` greens, `#c9a97e` and `#9a6f4e` tans/rust, `#eae7dc` card backing.
- **Encoding quirk:** the entire HTML payload is wrapped as a JSON-escaped string. Attribute quotes appear as `\"`, closing slashes as `\u002F`. Any text replacement script must account for this (see `/home/claude/merge_fees.py` for the pattern used to update the fees block).

## Form handling

The contact form uses **FormSubmit** (no backend required):

- Endpoint: `https://formsubmit.co/ajax/contact@suthpsychology.org`
- Method: `fetch` POST with JSON body
- Fields: name, email, phone, interested in, message, plus `_subject` and `_template: table`
- Dispatches a `contact_form_submit` dataLayer event for GTM
- **Activation requirement:** FormSubmit requires one real test submission to trigger the confirmation email before it starts delivering messages. Confirm this is done before launch.

## Structured data

JSON-LD at the top of the file covers three schemas:
1. `Psychologist` / `MedicalBusiness` / `LocalBusiness` for the practice
2. `Person` for Dr. Suth (education, credentials, memberships)
3. `FAQPage` with five Q&A entries

## Recent changes

### 2026-10-01: Fees and insurance copy update

Replaced the "Insurance & superbills" box inside the Fees section with a three-paragraph version that:

1. States which plans are in-network (Blue Cross Blue Shield, Medicare, Tricare West coming)
2. Explains superbill offering for out-of-network plans
3. Flags that most insurers don't cover independent neuropsychological or psychoeducational evaluations, and that developmental assessment coverage can depend on diagnosis

Voice: first-person ("I") to match the rest of the site.

## Open items / to-do

- [ ] **FAQPage schema inconsistency.** The structured data block still answers "Does Dr. Suth accept insurance?" with "Dr. Suth is not in-network with insurance plans but provides superbills..." This contradicts the new fees copy and could surface in Google search snippets. Needs updating to match.
- [ ] **Fee tiers in FAQ schema.** The structured data lists therapy at `$325/hour`, parent coaching and ADHD therapy at `$300/hour`, child neuropsych assessments starting at `$5,500`, neurodiversity assessments starting at `$3,000`. The visible fee tables show therapy/consultation at `$250 to $325 depending on timing`, child neuropsych `from $5,000`, neurodiversity `from $3,000`. Reconcile.
- [ ] **"Ohana Center / Montage"** phrasing: the About section currently reads "Ohana Center / Community Hospital of the Monterey Peninsula" (long form). Original client doc had what looked like a typo mixing "Montage" with Ohana. Confirm with Andy that the long form is accurate.
- [ ] **Adult Neuropsychological Assessment** service card: content lives in the file but is thinner than the other service pages. Consider deepening if client has more copy.
- [ ] **Diagnostic Assessment** service card: same note, lighter than the others.
- [ ] **FormSubmit activation test.** Send one real submission to the production endpoint and complete the confirmation link in the resulting email.
- [ ] **Booking URL.** The DC component accepts a `bookingUrl` prop; if left empty, "Book a 15-min call" buttons route to the contact page. If Andy wants to swap in Calendly or Acuity, set the prop at the DC level.
- [ ] **ADHD service page copy** has two sentence fragments that could use a cleanup pass: "As someone who specializes and has dedicate my professional career to working with problems like ADHD..." and "someone with an ADHD has unique skills along concerns."

## Editing notes for future updates

- When updating text inside the deployed `index.html`, use a Python script that treats the file as bytes and matches on the escaped form (`style=\\"...\\"`, `<\u002Fdiv>`). Do not try to pretty-print or reformat the file. Framer DC parses the full escaped string.
- When updating fees or any content that also appears in the FAQPage JSON-LD at the top, update both locations.
- Keep the `sc-if` block boundaries intact. Each section wrapper (`<sc-if value="{{ isHome }}">` through its closing `</sc-if>`) is what the DC component uses to show/hide pages.
- The two alternate design files (`index-alt-look.html`, `index-editorial-look.html`) are standalone HTML and can be opened directly in a browser. They do not share assets or stylesheets with the deployed file.

## Contact for this project

**Maan Sacdalan** - Arbcentrix Inc., Washington DC
