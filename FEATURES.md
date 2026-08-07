# FEATURES.md

All "features" of this site are content sections of a one-page resume,
plus a small set of page-level affordances. Every item below is
**Implemented** and verified by direct inspection of `index.html` — no
partial/broken features were found.

## Page-level

| Feature | Status | File reference |
|---|---|---|
| Sticky top nav with anchor links to every section | Implemented | `index.html` `<nav>`, lines ~89-100 |
| Responsive layout (single breakpoint at 560px) | Implemented | `index.html` `@media (max-width: 560px)` rule, lines ~70-73 |
| Print stylesheet (hides nav when printed) | Implemented | `index.html` `@media print { nav { display: none; } }`, line ~84 |
| Inline SVG favicon (browser tab icon) | Implemented | `index.html` `<link rel="icon" href="data:image/svg+xml,...">`, line 8 — added in commit `f344976` |
| Smooth scroll to anchors | Implemented | `index.html` `html { scroll-behavior: smooth; }`, line 19 |

## Hero section

| Feature | Status | File reference |
|---|---|---|
| Circular avatar photo | Implemented | `.avatar` CSS rule + `photo.jpeg` |
| Name + headline | Implemented | `<h1>Gary Wang</h1>` + `.headline` paragraph |
| Social links: GitHub, LinkedIn, Email | Implemented | `.social` block, 3 `<a>` tags with inline SVG icons |

## Content sections (in page order)

| Section | Status | File reference |
|---|---|---|
| About | Implemented | `<section id="about">` — one paragraph bio |
| Experience | Implemented | `<section id="experience">` — 4 roles, each with dates/org/bullet list (Alibaba, UC Riverside, William & Barbara Leonard Transportation Center, MP Biomedicals) |
| Projects | Implemented | `<section id="projects">` — 2 entries (Job Salary Prediction Model, Language Learning Model Research Paper) |
| Education | Implemented | `<section id="education">` — UC Berkeley, B.A. Statistics & Economics, minor Data Science, with coursework list |
| Skills | Implemented | `<section id="skills">` — 4 rows (Programming, ML & Data, Tools, Languages) |
| Honors | Implemented | `<section id="honors">` — 3-item list |
| Contact | Implemented | `<section id="contact">` — email, LinkedIn, GitHub links restated in prose |
| Footer | Implemented | `<footer>` — one-line copyright, "© 2026 Gary Wang" |

## Explicitly not present (by design, not a gap)

- No dark mode / theme toggle.
- No contact form (contact is via direct `mailto:` link and social
  links only).
- No blog, no additional pages, no client-side routing.
- No analytics/tracking.
- No animations beyond native CSS `:hover` and smooth-scroll.

If any of the above is ever wanted, treat it as new scope — see
`ROADMAP.md` → "Out of scope" for the same list framed as explicit
non-goals, and update `DECISIONS.md` if a deliberate choice is made to
add one.
