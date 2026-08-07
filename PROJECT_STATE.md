# PROJECT_STATE.md — Exact Handoff Snapshot

**This file describes the state of the repository at one specific
moment.** It will go stale the instant more work happens — update it
after every meaningful session (see `CLAUDE.md` → Permanent rules).

## Audit timestamp

- **Audit performed:** 2026-08-06, ~05:52 local time (documentation-only
  audit — no application files were changed; only these 17 memory files
  were added)
- **Re-confirmed at account-switch checkpoint:** 2026-08-06, same
  session, second pass. Nothing in the repository changed between the
  initial audit and this checkpoint — no new commits, no edits to
  `index.html`/`photo.jpeg`/`.gitignore`.

## Git state

- **Branch:** `main` (only branch, both locally and on the remote)
- **Tracking:** `origin/main`
  (`https://github.com/Gariyuuu/personal-website.git`), up to date
- **Latest commit:** `f3449762b89aadff63ac60250320ea0f3c88d1ea`
  (short: `f344976`) — "Add favicon so the site shows an icon in the
  browser tab" (2026-08-06)
- **Full commit history (5 commits total, oldest first):**
  1. `9869c4a` — 2026-07-24 — "Initial commit"
  2. `2d4d662` — 2026-07-25 — "Update resume content, drop GPA, add
     GitHub link"
  3. `bc9786d` — 2026-07-27 — "Update profile photo"
  4. `aa8b157` — 2026-08-03 — "Ignore .DS_Store"
  5. `f344976` — 2026-08-06 — "Add favicon so the site shows an icon in
     the browser tab" (HEAD)
- **Working tree: CLEAN.** `git status --porcelain` returns nothing
  before this audit's own file additions.
- **Uncommitted changes:** none.
- **Untracked files (before this audit):** none. **After this audit:**
  the 17 new documentation files listed in `CLAUDE.md`'s header
  (`CLAUDE.md`, `PROJECT_STATE.md`, `ARCHITECTURE.md`, `FILE_MAP.md`,
  `FEATURES.md`, `TASKS.md`, `ROADMAP.md`, `DECISIONS.md`,
  `DATABASE.md`, `API_REFERENCE.md`, `UI_SYSTEM.md`, `SECURITY.md`,
  `TESTING.md`, `DEPLOYMENT.md`, `CHANGELOG.md`, `SESSION_LOG.md`,
  `HANDOFF.md`) are untracked (not committed — this was a documentation
  build task; committing was explicitly out of scope).

## Current state

**Complete and stable.** The site is a finished, working single-page
résumé with no known bugs, no TODOs, no placeholder content, and no
broken links (every `href=` in `index.html` was checked during this
audit — all resolve correctly). This is not a project with an "in
progress" feature; it's a small, essentially-done personal site that
gets occasional content updates.

## What currently works (verified this audit)

- `index.html` is well-formed HTML (matching open/close tags for every
  major element; single `<html>`/`<head>`/`<body>`).
- All internal nav anchors (`#about`, `#experience`, `#projects`,
  `#education`, `#skills`, `#honors`, `#contact`) have a matching
  `id="..."` on a real `<section>` in the body — verified by direct
  read, no orphaned anchors.
- All external links (`https://github.com/Gariyuuu`,
  `https://www.linkedin.com/in/gary-wang-a912a0308/`,
  `mailto:gywng006@gmail.com`) are well-formed URLs pointing at
  plausible, real destinations for this repo's owner — not verified by
  live HTTP request (out of scope for a non-destructive local audit),
  but structurally correct.
- `photo.jpeg` exists at the path `index.html` references
  (`url('photo.jpeg')`, a relative path — correct given both files sit
  at the repo root).
- No TODO/FIXME/placeholder/lorem-ipsum text found anywhere in
  `index.html` (checked via direct read and pattern search).

## What currently fails / is unverified

- **The live production URL is unknown from within this repo.** No
  custom domain or deployment URL is recorded in any tracked file.
  `.vercel/project.json` (gitignored, local-only) confirms the
  directory is linked to a Vercel project named `personal-website`, but
  the actual public URL and whether it auto-deploys on push were not
  checked against the Vercel dashboard/CLI during this audit (a
  live-service lookup was treated as out of scope for a non-destructive,
  read-only documentation pass). See `DEPLOYMENT.md`.
- No automated tests exist (none are really applicable at this scope —
  see `TESTING.md`).

## Next three recommended actions

There is no urgent or blocking work. If asked what to do next, the
three most reasonable options are:

1. **Confirm the live deployment.** Check the Vercel dashboard (or run
   `vercel ls` / `vercel inspect` if the CLI is authenticated) to record
   the actual production URL and whether GitHub pushes auto-deploy —
   this is the one real gap in this documentation pass, and it's a
   read-only check, not a code change.
2. **Keep resume content current.** The next time the owner's resume
   changes (new job, new project, etc.), update the matching
   `<section>` in `index.html` — see `FEATURES.md` for exactly which
   section maps to which resume category.
3. **Nothing else is queued.** Do not invent feature work (e.g. adding
   a build step, a framework, analytics, a contact form) unless
   explicitly requested — see `CLAUDE.md`'s "DO NOT CHANGE WITHOUT
   REVIEW" and `ROADMAP.md`'s "Out of scope" section.
