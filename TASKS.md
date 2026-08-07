# TASKS.md

This project has no active feature work. Given its scope (a single
static resume page), this file is expected to stay mostly empty most of
the time — that's a correct reflection of the project's state, not a
missing section.

## ⚠️ Before adding any task here

This repo is flagged as possibly superseded by `~/Projects/gariyuu-web`
and was listed as "a candidate to delete" by a prior inventory audit —
but it also received 6 real commits on 2026-08-07 (dark hacker-theme
rework). **Check with the owner on the supersession/deletion question
before queuing or starting non-trivial new feature work here.** See
`PROJECT_STATE.md` and `HANDOFF.md` for the full framing.

## Current task

None. Nothing is in progress as of this 2026-08-07 refresh. The tree is
clean at commit `813e215`.

## Next up

Nothing is queued beyond the supersession check above. If the owner
confirms this repo should keep being developed, the only realistic
future work is periodic content/visual maintenance:

- Update resume content (`index.html`) whenever the owner's actual
  resume changes (new job, new project, new honor, etc.).
- Optionally confirm the live Vercel deployment URL/auto-deploy
  behavior (a read-only check, not a code change) — see
  `DEPLOYMENT.md`.

## Blocked

Nothing is technically blocked, but see the supersession check above —
treat non-trivial feature work as blocked on the owner's answer.

## Bugs

None found during this audit. No TODO/FIXME markers, no broken links,
no malformed HTML found in `index.html`.

## Technical debt

- The documentation set (16 files, now 17 with `README.md`) had drifted
  significantly from the actual `index.html` after the 2026-08-07
  hacker-theme rework (claims of "no JavaScript," "light theme only,"
  and an inline SVG favicon were all stale). Corrected in this pass —
  see `CHANGELOG.md`. Going forward, update docs in the same commit as
  any visual/structural change to avoid this happening again.
- One very minor open question (not a bug): whether Vercel's Git
  integration auto-deploys `main` on push, or whether deploys require a
  manual `vercel deploy --prod` — see `DEPLOYMENT.md`. Confirming this
  is optional, low-priority, read-only work.
- Minor provenance gap: exactly which commit swapped the inline `data:`
  SVG favicon (added in `f344976`) for the current `favicon.ico` file
  wasn't isolated during this pass — not load-bearing, noted in
  `PROJECT_STATE.md`.

## Recently completed

Per git log (most recent first):

- `813e215` (2026-08-07) — Made the hacker-log flood fill the whole
  screen with a shake effect.
- `88b465d` (2026-08-07) — Turned the hacker-log flood into scattered
  black-and-white terminal windows.
- `c324c71` (2026-08-07) — Slowed the rain, extended the boot sequence,
  added a hacked red screen.
- `eff4591` (2026-08-07) — Added the terminal boot-up intro animation.
- `9778732` (2026-08-07) — Reworked the site into a dark hacker theme;
  added the OpenReview link.
- `b27b9c9` (2026-08-06) — Added the full 17(→16-at-the-time) file
  handoff documentation system.
- `f344976` (2026-08-06) — Added a favicon (inline SVG at the time;
  since replaced by `favicon.ico`).
- `aa8b157` (2026-08-03) — Added `.DS_Store` to `.gitignore`.
- `bc9786d` (2026-07-27) — Updated the profile photo.
- `2d4d662` (2026-07-25) — Refreshed experience/projects/skills/honors
  content to match an updated resume; dropped GPA from Education; added
  a GitHub link alongside LinkedIn/email.
- `9869c4a` (2026-07-24) — Initial commit (first version of the site).

This 2026-08-07 documentation refresh (no commit hash yet at time of
writing — see `SESSION_LOG.md`): added `README.md`, corrected drifted
technical claims across the doc set, and added the supersession flag.

## Deferred

Nothing has been explicitly deferred.

## Rejected ideas

None recorded. No feature request has been made and turned down in
this repo's history.
