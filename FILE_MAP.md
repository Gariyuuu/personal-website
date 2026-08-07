# FILE_MAP.md

Every file in this repository, what it's for, and how to edit it
safely. There are 5 tracked content/config files (plus the 17-file doc
set) and 1 gitignored directory, so this map is intentionally short.

## `index.html`

- **Purpose:** The entire website — one HTML file containing `<head>`
  metadata, an inline `<style>` block (all CSS), the full `<body>`
  markup (boot overlay, nav, hero, 7 content sections, footer), and two
  inline `<script>` blocks (canvas rain effect, boot/hack intro
  animation).
- **Size:** 611 lines, ~26KB (grew from ~246 lines/~12.8KB after the
  2026-08-07 dark hacker-theme rework — see `DECISIONS.md`/
  `CHANGELOG.md`).
- **Structure inside the file:**
  - `<head>`: charset/viewport meta, `<title>`, description meta tag, a
    real favicon link (`<link rel="icon" href="favicon.ico">`), Google
    Fonts preconnect + stylesheet tags for `Share Tech Mono`, and the
    entire `<style>` block.
  - `<body>`: `<canvas id="rain">` (background effect) → `<div
    id="boot">` (boot/hack intro overlay, removed by script once
    played or skipped) → `<nav>` (sticky, name + 7 anchor links) →
    `<main>` → `<header class="hero">` (avatar, name, headline, social
    icons incl. OpenReview) → 7 `<section id="...">` blocks (About,
    Experience, Projects, Education, Skills, Honors, Contact, in that
    order) → `<footer>` (copyright line) → two `<script>` blocks (rain
    animation, boot sequence logic).
- **Edit guidance:** This is a hand-authored resume page — when
  updating *content* (new job, new project, etc.), follow the existing
  pattern for that section (see `<div class="item">` blocks under
  Experience/Projects, or `<div class="row">` under Skills) rather than
  introducing a new markup pattern. Keep the nav's anchor links in sync
  if you add/remove/rename a section. Don't touch the two `<script>`
  blocks or the dark-theme CSS unless the visual/boot-animation
  behavior is specifically what's being changed. No build step — edits
  take effect immediately on save/redeploy.

## `favicon.ico`

- **Purpose:** Browser-tab icon, referenced via `<link rel="icon"
  href="favicon.ico">` in `index.html`'s `<head>`.
- **Format/size:** `.ico`, ~22.7KB. Replaced an earlier inline `data:`
  SVG favicon approach (see `DECISIONS.md`) — the exact commit that
  made the swap wasn't isolated during the 2026-08-07 doc refresh.
- **Edit guidance:** Replace the file directly to change the tab icon;
  no other file needs to change unless the filename itself changes (in
  which case update the `<link rel="icon">` `href` too).

## `photo.jpeg`

- **Purpose:** Profile photo shown in the circular avatar in the hero
  section, referenced via CSS: `background: ... url('photo.jpeg')
  center/cover no-repeat;` (see the `.avatar` rule in `index.html`'s
  `<style>` block).
- **Format/size:** JPEG, 400×400px, ~31.2KB (per direct inspection —
  `file photo.jpeg` reports "JPEG image data, baseline, precision 8,
  400x400, components 3").
- **Edit guidance:** Replace the file directly to update the photo
  (matching filename, and roughly square is safest since the CSS uses
  `border-radius: 50%` + `object-fit`-equivalent `background-size:
  cover`). Git history shows this has been swapped once before
  (`bc9786d`, "Update profile photo"), so this is an expected,
  low-risk kind of edit.

## `.vercel/` (gitignored — not committed)

- **Purpose:** Vercel CLI's local link metadata, created by `vercel
  link` (or the first `vercel` deploy). Confirms this directory is tied
  to a specific Vercel project.
- **Contents:**
  - `project.json` — `{"projectId": "prj_...", "orgId": "team_...",
    "projectName": "personal-website"}`. Identifies the Vercel project
    this local checkout deploys to.
  - `README.txt` — Vercel's own auto-generated explanation of the
    folder (explicitly states it should not be committed/shared).
- **Edit guidance:** **Do not hand-edit or commit this.** It's already
  correctly gitignored (`.gitignore` includes `.vercel`). If a fresh
  clone needs to be linked to the same Vercel project, run `vercel
  link` and select the existing `personal-website` project rather than
  creating a new one.

## `.gitignore`

- **Purpose:** Keeps local-only/generated files out of version control.
- **Contents:** `.vercel` and `.DS_Store` (two lines, nothing else).
- **Edit guidance:** No changes needed at this scope. If a build tool
  or `node_modules` is ever introduced, add the relevant ignore
  patterns then — don't pre-add unused ignore rules now.
