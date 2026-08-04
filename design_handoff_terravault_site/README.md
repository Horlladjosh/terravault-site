# Handoff: Terravault — Climatetech Marketing Site

## Overview
Terravault is a (concept) direct-air-capture (DAC) carbon-removal company. This is a
complete, editorial dark-theme **marketing site** aimed at enterprise offtake buyers,
investors, and technical evaluators. It comprises 8 content pages plus a design-system
reference page. The site's job is to make carbon removals feel *defensible* — every claim
is tied to third-party verification, MRV methodology, and a data room.

## About the Design Files
The files in `design_files/` are **design references created in HTML** — high-fidelity
prototypes that show the intended look, layout, copy, and behavior. They are **not**
production code to ship as-is.

They are authored as "Design Components" (`.dc.html`): each file has a custom `<x-dc>`
template plus a small `<script data-dc-script> class Component extends DCLogic` block, and
loads a runtime called `support.js`. **That runtime is proprietary to the design tool and
is not included** — the files will not run in a normal browser. Treat them as detailed
visual + interaction specs to read, not to execute.

Your task: **recreate these designs in the target codebase's environment** using its
established patterns and libraries — React/Next, Vue/Nuxt, Astro, SvelteKit, plain HTML,
etc. If no codebase exists yet, this is a static marketing site with light interactivity;
**Astro or Next.js (static export) are both excellent fits**. All layout is plain
HTML/CSS (flexbox + CSS grid) and all styling is inline — trivially portable to any
component framework or a single stylesheet.

## Fidelity
**High-fidelity (hifi).** Final colors, typography, spacing, copy, and interactions are
all present and intentional. Recreate the UI pixel-for-pixel. Exact hex values, font
families, sizes, and the responsive `clamp()` type scale are given in **Design Tokens**
below and are also readable inline in each design file.

---

## Design Tokens

Styling in the source files is **inline** (`style="…"`), with a small global reset and
font import per page. There is no CSS variable layer in the source — the values below are
the de-facto tokens. Recommend materializing them as CSS custom properties / a theme file
in the target codebase.

### Color
| Token | Hex | Usage |
|---|---|---|
| `--bg` | `#090b09` | Page background (near-black green) |
| `--surface` | `#0d100e` | Card / panel base |
| `--surface-2` | `#12160f` | Card hover / gradient top |
| `--surface-panel` | `#0f130d` → `#0b0d0b` | Data-panel gradient (`linear-gradient(160deg, …)`) |
| `--text` | `#f4f2ec` | Primary text (warm off-white) |
| `--text-muted` | `#a9a79d` | Body / secondary text |
| `--text-dim` | `#918f86` | Captions inside cards |
| `--text-faint` | `#6b6960` | Footnotes, footer meta, labels |
| `--accent` | `#9ef27a` | Brand green — eyebrows, numbers, glow dots, links |
| `--accent-2` | `#1d9e75` | Deep green — gradient partner |
| `--accent-3` | `#0b3d2c` | Darkest green — logo gradient tail |
| `--cta-ink` | `#06210f` | Text color on green CTA buttons |
| hairline | `rgba(255,255,255,0.07–0.10)` | Card borders, dividers |
| accent hairline | `rgba(158,242,122,0.25–0.30)` | Badge borders, card hover border |
| accent wash | `rgba(158,242,122,0.06–0.16)` | Badge fills, radial glows |

Key gradients:
- **Logo mark:** `linear-gradient(135deg, #9ef27a, #1d9e75 60%, #0b3d2c)` on a 24px rounded square (7px radius).
- **Primary CTA:** `linear-gradient(135deg, #b4f792, #1d9e75)`, text `#06210f`, hover `filter: brightness(1.06)`.
- **Data bars:** `linear-gradient(180deg, #9ef27a, #1d9e75)`.
- **Hero glow:** stacked `radial-gradient(ellipse 70% 50% at 50% -10%, rgba(157,242,122,0.16), transparent 60%)` layered over `#090b09`.
- **CTA-section glow:** `radial-gradient(ellipse 60% 60% at 50% 50%, rgba(158,242,122,0.08), transparent 70%)`.

### Typography
Two Google Fonts, loaded per page:
```
Manrope: 400,500,600,700,800   → body, UI, labels, buttons, nav
Fraunces (opsz 9..144, ital): 400,500,600 + italic 400,500 → display headings, big numbers, pull-quotes
```
- **Display** = `'Fraunces', serif`, **weight 500**, `letter-spacing: -0.01em to -0.02em`,
  `line-height: 1.04–1.06`. Emphasis words are **italic + `#9ef27a`** (e.g. *gigaton scale*).
- **Body/UI** = `'Manrope', sans-serif`, weights 400–800.
- **Eyebrows / overlines:** 13px, `#9ef27a`, `font-weight:600`, `letter-spacing:0.05em`;
  some are uppercase with `letter-spacing:0.06–0.08em`.
- **Base body line-height:** 1.5. Antialiased (`-webkit-font-smoothing: antialiased`).

Responsive display scale (as used):
| Role | `font-size` |
|---|---|
| Home H1 | `clamp(42px, 6vw, 70px)` |
| Sub-page H1 | `clamp(38px, 5.4vw, 58–60px)` |
| Section H2 (large) | `clamp(30px, 4.6vw, 52px)` |
| Section H2 (standard) | `clamp(28px, 3.6vw, 38–42px)` |
| Section H2 (small) | `clamp(24–26px, 3–3.4vw, 32–36px)` |
| CTA H2 | `clamp(30–32px, 4.4–4.6vw, 44–46px)` |
| Big stat number | 32–38px Fraunces 500 |
| Body lead | 17–19px |
| Body | 14–16px |
| Caption / footnote | 11–13.5px |

### Spacing & layout
- 8px-ish rhythm; generous editorial whitespace.
- **Content container:** `max-width: 1160px; margin: 0 auto`. (Design-system page uses 1280px.)
- **Horizontal page padding:** `64px` (this is the standard gutter; keep responsive fallback for narrow screens).
- **Section vertical padding:** 80–132px; CTA sections 110–132px.
- **Card padding:** 30–44px.
- **Nav:** `padding: 20px 64px`, sticky.

### Radius
| Use | Value |
|---|---|
| Pills / CTAs / badges / chips | `100px` (`999px`) |
| Cards / panels | `16px` (small), `20px` (media/panels), `24px` (large CTA card) |
| Data bars | `5px 5px 0 0` |
| Logo square | `7px` |
| Avatars / step dots | `50%` |
| Media crops / hero image | `20px` |

### Elevation & motion
- Resting cards are **flat** — only a `1px` hairline border. No resting shadow.
- **Card hover:** `transform: translateY(-6px)` + border shifts to `rgba(158,242,122,0.3)`,
  transition `.35s cubic-bezier(.2,.8,.2,1)`.
- **Scroll reveal (every `[data-reveal]` element):** starts `opacity:0; translateY(28px)`,
  animates to `opacity:1; translateY(0)` over `.8s cubic-bezier(.16,1,.3,1)` via an
  IntersectionObserver (`threshold:0`, `rootMargin: 0px 0px -60px 0px`, unobserve after
  reveal). **Respect `prefers-reduced-motion: reduce`** — skip reveal entirely (source does).
- **Buttons:** primary hover `brightness(1.06)`; secondary (outline) hover fills
  `rgba(255,255,255,0.06)` and brightens border.
- **Nav links:** color `#a9a79d` → `#f4f2ec` on hover, `.25s`.
- Glow dots: 6px `#9ef27a` circle with `box-shadow: 0 0 8–10px #9ef27a`.

### Global reset (per page)
```css
* { margin:0; padding:0; box-sizing:border-box; }
html { scroll-behavior:smooth; }
body { font-family:'Manrope',sans-serif; background:#090b09; color:#f4f2ec;
       line-height:1.5; overflow-x:hidden; -webkit-font-smoothing:antialiased; }
a { color:inherit; text-decoration:none; }
::selection { background: rgba(158,242,122,0.25); }
```

---

## Screens / Views

All pages share the same **sticky glass nav** (logo left; Technology / For enterprise /
Company center-right; "Book a consult" pill button right) and the same **footer**
(4-column: brand blurb, Product, Company, Resources + bottom legal row). Recreate these
once as shared layout components.

### 1. Home (`Home.dc.html`)
- **Purpose:** top-of-funnel landing page; route evaluators to the right deep page.
- **Layout / sections, top to bottom:**
  1. **Hero** — centered, radial green glow bg. Badge pill ("Direct air capture,
     independently verified"), H1 with italic-green emphasis, lead paragraph (max 560px),
     two CTAs ("See the technology" green gradient → Technology; "Download verification
     report" outline → VerificationReport).
  2. **Hero media** — 1160px, `min(56vw,540px)` tall, 20px radius. Full-bleed image with
     dark bottom/left gradient scrims; bottom-left status pill ("Facility 02 — Permian
     Basin · live capture data"), bottom-right two live stats (1,240 tons / 98.4% uptime).
  3. **Stat strip** — 4-col grid, 1px gaps over a hairline (creates divider lines),
     rounded 14px. Each cell: big Fraunces green number + muted label
     (412K tons · $180/ton · 99.9% permanence · 14 partners).
  4. **Full-bleed video band** — `min(72vh,600px)`, autoplaying muted looped aerial
     footage with scrims; overlaid eyebrow + H2 + paragraph, bottom-right credit chip.
  5. **How it works** — 3-col card grid; each card has a numbered circle (01/02/03),
     title, description. Hover-lift cards.
  6. **Process media** — single 16:9-ish image with caption overlay ("Modular contactors…").
  7. **Network capture panel** — bordered panel, header row (live dot + "last 30 days" /
     "Updated hourly · MRV-linked"), split body: left = **8-bar CSS bar chart** (heights
     52–100%) with Wk1–Wk4 labels; right = 3 stacked KPIs.
  8. **Video feature** — 1.5fr/1fr grid: `<video controls>` clip left, copy right.
  9. **Pull quote** — centered italic Fraunces testimonial + avatar/attribution
     (Maya Reyes · Northbridge Capital).
  10. **Logo wall** — "Verified and backed by" + 5 partner wordmarks.
  11. **Deep-link grid** — "Everything an evaluator needs" — 3×2 card grid linking to
      Technology, Enterprise, MRV, VerificationReport, DataRoom, About (each: eyebrow,
      title with green →, description). Hover-lift.
  12. **CTA section** — "Ready to see the data room?" + "Request access" → DataRoom.
  13. Footer.
- **Interactions:** autoplay/loop/mute videos on mount (`data-autovideo`); scroll reveal
  on all `[data-reveal]`.

### 2. Technology (`Technology.dc.html`)
- **Purpose:** the engineering story for technical evaluators.
- **Sections:** centered hero (badge + H1 + lead) → **Process schematic** panel ("The
  capture cycle, end to end") → **Energy & mass balance** ("What it takes to remove one
  ton") → **Performance** ("Cost is falling as the fleet scales", 1.5fr/1fr grid) →
  **Facility specification** table ("Gen 3 module, at a glance") → **MRV** cross-link
  block → CTA ("Want the full methodology?" → Enterprise) → footer.
- **Interactions:** scroll reveal only.

### 3. Enterprise (`Enterprise.dc.html`)
- **Purpose:** the offtake / commercial pitch for procurement & sustainability teams.
- **Sections:** hero (H1 "Offtake removals you can [defend]", 2 CTAs) → value props →
  **Evaluation process** ("From first call to first ton delivered") → **FAQ accordion**
  ("Questions buyers ask us") → **Contact CTA card** ("Talk to our offtake team") → footer.
- **Interactive state:** `state = { open: 0 }` — an **accordion**; exactly one FAQ item
  open at a time, first item open by default; clicking a row toggles/swaps the open index.
  Recreate as a controlled accordion.

### 4. MRV (`MRV.dc.html`)
- **Purpose:** measurement, reporting & verification methodology — the credibility core.
- **Sections:** hero ("Every ton is measured, reported, and verified — not modeled") →
  **The measurement chain** ("Three meters, one reconciled number") → **deductions table**
  ("What we subtract before we count a ton") → **Permanence monitoring** ("We keep watching
  after the ton is stored") → **Standards** ("Protocols we conform to") → CTA ("Read the
  full protocol" → DataRoom) → footer.
- **Interactions:** scroll reveal only.

### 5. Data Room (`DataRoom.dc.html`)
- **Purpose:** gated evidence library for credentialed investors/buyers.
- **Sections:** hero ("The data room — [sourced]") → **What's inside** ("Seven folders,
  fully sourced", 2-col grid of folder cards) → **Getting access** ("Credentialed in three
  steps", vertical step list) → CTA ("Request data room access" → Enterprise) → footer.
- **Interactions:** scroll reveal only.

### 6. Verification Report (`VerificationReport.dc.html`)
- **Purpose:** the receipts — FY25 verified tons, independent statement, per-facility totals.
- **Interactions:** scroll reveal only.

### 7. About (`About.dc.html`)
- **Purpose:** company story, team, principles.
- **Interactions:** scroll reveal only.

### 8. Book a Consult (`BookConsult.dc.html`)
- **Purpose:** lead-capture / scheduling page (nav CTA target).
- **Interactive state:** `state = { slot: null, submitted: false }` — a **time-slot picker
  + form**: user selects a slot (sets `slot`), submits the form → `submitted: true` swaps
  the form for a success/confirmation state. Recreate as a controlled form with a
  selectable slot list and a post-submit confirmation view. (Source has no backend — wire
  to the target app's form/scheduling endpoint.)

### 9. Design System (`DesignSystem.dc.html`)
- **Purpose:** internal reference — tokens, type scale, spacing, components documented for
  a build. Use it as the canonical spec if any value here is ambiguous. Not a public page.

---

## Interactions & Behavior (summary)
- **Navigation:** plain anchor links between pages (`href="Technology.dc.html"` etc.).
  In the target app, map these to the router (`/technology`, `/enterprise`, `/mrv`,
  `/data-room`, `/verification-report`, `/about`, `/book-consult`).
- **Sticky nav:** `position: sticky; top:0; z-index:50`, translucent bg
  `rgba(9,11,9,0.72)` + `backdrop-filter: blur(14px)`, bottom hairline.
- **Scroll reveal:** IntersectionObserver fade-up on every `[data-reveal]`; disabled under
  `prefers-reduced-motion`. (See Design Tokens → motion for exact values.)
- **Videos:** hero/band videos autoplay muted+loop+`playsInline`; the "Watch" feature
  video uses native `controls`. All are placeholder Pexels clips — **swap for real
  facility footage**.
- **Accordion (Enterprise):** single-open, index-based.
- **Booking form (BookConsult):** slot selection + submitted confirmation state.
- **Hover:** card lift, button brightness/fill, nav-link color — values above.

## State Management
Minimal, all local component state:
- `Enterprise`: `{ open: number }` — currently open FAQ index.
- `BookConsult`: `{ slot: string|null, submitted: boolean }` — selected slot + form status.
- All other pages: no state beyond the mount-time scroll-reveal observer.
No global store, auth, or data fetching in the design. The data room's "credentialed
access" is narrative only — no gating is implemented.

## Assets
- **Fonts:** Manrope + Fraunces via Google Fonts (`fonts.googleapis.com`). Self-host in
  production if preferred.
- **Imagery:** all photos/videos are **external placeholders** from Unsplash and Pexels
  (facility exteriors, process halls, aerial b-roll). They are hotlinked in the source and
  must be **replaced with licensed Terravault footage/photography** before launch. Search
  the files for `unsplash.com` / `pexels.com` to find every reference.
- **Logo:** there is **no image logo** — the mark is a CSS gradient rounded-square +
  "Terravault" wordmark in Manrope 700. Reproduce with CSS or supply a real SVG mark.
- **Icons:** none as image assets — numbers, unicode arrows (→), and CSS shapes only.
- **Data visualization:** the Home bar chart is hand-built `<div>` bars (no chart lib);
  reproduce with divs or a lightweight chart lib as the codebase prefers.

## Files
In `design_files/`:
- `Home.dc.html` — landing page
- `Technology.dc.html` — technology / engineering
- `Enterprise.dc.html` — offtake / commercial (FAQ accordion)
- `MRV.dc.html` — measurement, reporting & verification
- `DataRoom.dc.html` — gated evidence library
- `VerificationReport.dc.html` — verified-tons report
- `About.dc.html` — company / team
- `BookConsult.dc.html` — consult booking (slot picker + form)
- `DesignSystem.dc.html` — token & component reference (spec, not a public page)

> Reading tip: in each file the markup lives between `<x-dc>` … `</x-dc>`; the small
> `<script data-dc-script>` block at the bottom holds only the interaction logic
> (scroll reveal, accordion, form). Ignore the `support.js` include and the `<x-dc>`
> wrapper — everything you need is the inline-styled HTML and that logic block.

## Screenshots
`screenshots/` holds a rendered reference PNG for each page (top of page — pages scroll
longer than one viewport; the design files are the source of truth for below-the-fold
content). Note: autoplaying videos may appear blank in the captures — that's a
screenshot limitation, not a design gap.
- `Home.png`, `Technology.png`, `Enterprise.png`, `MRV.png`, `DataRoom.png`,
  `VerificationReport.png`, `About.png`, `BookConsult.png`, `DesignSystem.png`

## Note on brand / content
Terravault is a **concept company** ("not an active company", per the footer). All stats,
partner names, and quotes are illustrative placeholders — confirm/replace real figures,
legal disclaimers, and testimonials before any public use.
