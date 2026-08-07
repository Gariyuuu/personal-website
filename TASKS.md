# TASKS.md

This project has no active feature work. Given its scope (a single
static resume page), this file is expected to stay mostly empty most of
the time — that's a correct reflection of the project's state, not a
missing section.

## Current task

None. Nothing is in progress as of the 2026-08-06 audit.

## Next up

Nothing is queued. The only realistic future work is periodic content
maintenance (see `PROJECT_STATE.md` → "Next three recommended
actions"):

- Update resume content (`index.html`) whenever the owner's actual
  resume changes (new job, new project, new honor, etc.).
- Optionally confirm the live Vercel deployment URL/auto-deploy
  behavior (a read-only check, not a code change) — see
  `DEPLOYMENT.md`.

## Blocked

Nothing is blocked.

## Bugs

None found during this audit. No TODO/FIXME markers, no broken links,
no malformed HTML found in `index.html`.

## Technical debt

None significant given the intentionally minimal scope. One very minor
open question (not a bug): whether Vercel's Git integration
auto-deploys `main` on push, or whether deploys require a manual
`vercel deploy --prod` — see `DEPLOYMENT.md`. Confirming this is
optional, low-priority, read-only work.

## Recently completed

Per git log (most recent first):

- `f344976` (2026-08-06) — Added an inline SVG favicon so the site
  shows an icon in the browser tab.
- `aa8b157` (2026-08-03) — Added `.DS_Store` to `.gitignore`.
- `bc9786d` (2026-07-27) — Updated the profile photo.
- `2d4d662` (2026-07-25) — Refreshed experience/projects/skills/honors
  content to match an updated resume; dropped GPA from Education; added
  a GitHub link alongside LinkedIn/email.
- `9869c4a` (2026-07-24) — Initial commit (first version of the site).

## Deferred

Nothing has been explicitly deferred.

## Rejected ideas

None recorded. No feature request has been made and turned down in
this repo's history — this section is kept for structural consistency
with the sibling-project documentation format and should be filled in
if/when a real proposal is considered and declined.
