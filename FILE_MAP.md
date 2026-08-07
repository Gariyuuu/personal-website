# FILE_MAP.md

Every file in this repository, what it's for, and how to edit it
safely. There are only 4 files total (3 tracked + 1 gitignored
directory), so this map is intentionally short.

## `index.html`

- **Purpose:** The entire website — one HTML file containing `<head>`
  metadata, an inline `<style>` block (all CSS), and the full `<body>`
  markup (nav, hero, 7 content sections, footer).
- **Size:** ~246 lines, ~12.8KB.
- **Structure inside the file:**
  - `<head>`: charset/viewport meta, `<title>`, description meta tag, an
    inline SVG favicon (`data:image/svg+xml,...` — no separate favicon
    file), and the entire `<style>` block.
  - `<body>`: `<nav>` (sticky, name + 7 anchor links) → `<main>` →
    `<header class="hero">` (avatar, name, headline, social icons) → 7
    `<section id="...">` blocks (About, Experience, Projects,
    Education, Skills, Honors, Contact, in that order) → `<footer>`
    (copyright line).
- **Edit guidance:** This is a hand-authored resume page — when
  updating content (new job, new project, etc.), follow the existing
  pattern for that section (see `<div class="item">` blocks under
  Experience/Projects, or `<div class="row">` under Skills) rather than
  introducing a new markup pattern. Keep the nav's anchor links in sync
  if you add/remove/rename a section. No build step — edits take effect
  immediately on save/redeploy.

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
