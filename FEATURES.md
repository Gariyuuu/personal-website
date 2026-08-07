# FEATURES.md

All "features" of this site are content sections of a one-page resume,
plus a small set of page-level affordances. Every item below is
**Implemented** and verified by direct inspection of `index.html` — no
partial/broken features were found.

## Page-level

| Feature | Status | File reference |
|---|---|---|
| Sticky top nav with anchor links to every section | Implemented | `index.html` `<nav>` |
| Responsive layout (single breakpoint at 560px) | Implemented | `index.html` `@media (max-width: 560px)` rule |
| Print stylesheet (hides nav + canvas rain when printed) | Implemented | `index.html` `@media print { nav { display: none; } canvas#rain { display: none; } }` |
| Favicon (browser tab icon) | Implemented | `index.html` `<link rel="icon" href="favicon.ico">`, a real committed file — earlier commit `f344976` used an inline `data:` SVG instead; that was later replaced by this file |
| Smooth scroll to anchors | Implemented | `index.html` `html { scroll-behavior: smooth; }` |
| Full-screen canvas "digital rain" background effect | Implemented, added 2026-08-07 | `<canvas id="rain">` + the first `<script>` IIFE; respects `prefers-reduced-motion` (returns early, no canvas draw) |
| Skippable terminal boot/hack-intro animation on load | Implemented, added 2026-08-07 | `<div id="boot">` + the second `<script>` IIFE; phases through a boot-text sequence, a scattered fake "flood" of terminal windows, a red "crash" screen, then a "reboot"/welcome message before removing itself; click or any keypress skips straight to removal; respects `prefers-reduced-motion` (removes itself immediately) |
| Google Fonts webfont (`Share Tech Mono`) | Implemented, added 2026-08-07 | `<link rel="preconnect">`/`<link rel="stylesheet">` tags in `<head>` — the one external network request this page makes |

## Hero section

| Feature | Status | File reference |
|---|---|---|
| Circular avatar photo | Implemented | `.avatar` CSS rule + `photo.jpeg` |
| Name + headline | Implemented | `<h1>Gary Wang</h1>` + `.headline` paragraph |
| Social links: GitHub, LinkedIn, OpenReview, Email | Implemented | `.social` block, 4 `<a>` tags with inline SVG icons — OpenReview added 2026-08-07 (commit `9778732`) |

## Content sections (in page order)

| Section | Status | File reference |
|---|---|---|
| About | Implemented | `<section id="about">` — one paragraph bio |
| Experience | Implemented | `<section id="experience">` — 4 roles, each with dates/org/bullet list (Alibaba, UC Riverside, William & Barbara Leonard Transportation Center, MP Biomedicals) |
| Projects | Implemented | `<section id="projects">` — 2 entries (Job Salary Prediction Model, Language Learning Model Research Paper) |
| Education | Implemented | `<section id="education">` — UC Berkeley, B.A. Statistics & Economics, minor Data Science, with coursework list |
| Skills | Implemented | `<section id="skills">` — 4 rows (Programming, ML & Data, Tools, Languages) |
| Honors | Implemented | `<section id="honors">` — 3-item list |
| Contact | Implemented | `<section id="contact">` — email, LinkedIn, GitHub, OpenReview links restated in prose |
| Footer | Implemented | `<footer>` — one-line copyright, "© 2026 Gary Wang" |

## Explicitly not present (by design, not a gap)

- No light/dark theme *toggle* — the site has one fixed dark theme
  (see `UI_SYSTEM.md`); there's no `prefers-color-scheme` handling or
  switcher.
- No contact form (contact is via direct `mailto:` link and social
  links only).
- No blog, no additional pages, no client-side routing.
- No analytics/tracking.
- No animations beyond CSS `:hover`/smooth-scroll and the two
  JS-driven effects listed in "Page-level" above (canvas rain, boot
  intro) — both purely visual, no logic beyond the animation itself.

If any of the above is ever wanted, treat it as new scope — see
`ROADMAP.md` → "Out of scope" for the same list framed as explicit
non-goals, and update `DECISIONS.md` if a deliberate choice is made to
add one.
