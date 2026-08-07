# CHANGELOG.md

Reconstructed from `git log` (all dates are actual commit dates — none
invented). No prior CHANGELOG.md existed before the 2026-08-06 audit.

## 2026-08-07 — Documentation refresh + supersession flag

Verified the 16-file doc set against the actual repo (which had
drifted significantly — see the entries below), corrected stale claims,
added the missing `README.md`, and flagged this repo as possibly
superseded by `~/Projects/gariyuu-web` pending the owner's decision. No
application code changed. See `SESSION_LOG.md` for full detail.

## 2026-08-07 — Make the hacker-log flood fill the whole screen with a shake

Commit `813e215`. Expanded the "flood" phase of the boot/hack intro
animation to fill the full screen and added a shake effect.

## 2026-08-07 — Turn the hacker-log flood into scattered black-and-white terminal windows

Commit `88b465d`. Changed the flood-phase visual from a single log
stream into multiple scattered, rotated terminal-window panels.

## 2026-08-07 — Slow the rain, extend the boot sequence, add a hacked red screen

Commit `c324c71`. Slowed the canvas rain animation, lengthened the
boot-sequence text, and added a red "crash"/compromised screen phase to
the intro sequence.

## 2026-08-07 — Add terminal boot-up intro animation

Commit `eff4591`. Added the first version of the skippable JS
terminal boot sequence that plays before the résumé content is shown.

## 2026-08-07 — Rework site into a dark hacker theme, add OpenReview link

Commit `9778732`. Replaced the light-theme design tokens with a dark,
near-black "hacker" palette (green/cyan accents), switched the font
stack to the `Share Tech Mono` Google Fonts webfont, added a canvas
"digital rain" background effect, and added an OpenReview link to the
social icons and Contact section.

## 2026-08-06 — Documentation handoff (previous audit)

Added a full 16-file documentation system (`CLAUDE.md`,
`PROJECT_STATE.md`, `ARCHITECTURE.md`, `FILE_MAP.md`, `FEATURES.md`,
`TASKS.md`, `ROADMAP.md`, `DECISIONS.md`, `DATABASE.md`,
`API_REFERENCE.md`, `UI_SYSTEM.md`, `SECURITY.md`, `TESTING.md`,
`DEPLOYMENT.md`, `CHANGELOG.md`, `SESSION_LOG.md`, `HANDOFF.md`) by
directly auditing the repo. Committed as `b27b9c9`.

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
