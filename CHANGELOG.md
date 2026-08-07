# CHANGELOG.md

Reconstructed from `git log` (all dates are actual commit dates — none
invented). No prior CHANGELOG.md existed before this audit.

## 2026-08-06 — Add favicon

Commit `f344976`. Added an inline SVG favicon (`data:image/svg+xml,...`
data URI, blue rounded square with "GW") so the site shows an icon in
the browser tab. One line added to `index.html`'s `<head>`; no new
files.

## 2026-08-03 — Ignore .DS_Store

Commit `aa8b157`. Added `.DS_Store` to `.gitignore` (repo hygiene, no
content change).

## 2026-07-27 — Update profile photo

Commit `bc9786d`. Replaced `photo.jpeg` with a new profile photo
(19,187 bytes → 31,967 bytes). No `index.html` changes.

## 2026-07-25 — Update resume content, drop GPA, add GitHub link

Commit `2d4d662`. Refreshed Experience/Projects/Skills/Honors content
to match an updated resume; removed GPA from the Education section;
added a GitHub link alongside LinkedIn and email in both the header
social icons and the Contact section; updated the contact email
address. 40 insertions, 30 deletions across `index.html`.

## 2026-07-24 — Initial commit

Commit `9869c4a`. First version of the site: `.gitignore`,
`index.html` (234 lines — full page structure, nav, hero, all content
sections, styling), and `photo.jpeg`.

## 2026-08-06 — Documentation handoff (this audit)

Added a full 17-file documentation system (`CLAUDE.md`,
`PROJECT_STATE.md`, `ARCHITECTURE.md`, `FILE_MAP.md`, `FEATURES.md`,
`TASKS.md`, `ROADMAP.md`, `DECISIONS.md`, `DATABASE.md`,
`API_REFERENCE.md`, `UI_SYSTEM.md`, `SECURITY.md`, `TESTING.md`,
`DEPLOYMENT.md`, `CHANGELOG.md`, `SESSION_LOG.md`, `HANDOFF.md`) by
directly auditing the repo — no application code was changed. See
`SESSION_LOG.md` for the full record of this pass.
