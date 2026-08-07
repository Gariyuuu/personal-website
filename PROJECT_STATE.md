# PROJECT_STATE.md — Exact Handoff Snapshot

**This file describes the state of the repository at one specific
moment.** It will go stale the instant more work happens — update it
after every meaningful session (see `CLAUDE.md` → Permanent rules).

## ⚠️ Supersession status — read this first

A prior cross-repo inventory audit of `~/Projects` flagged this repo as
**"likely superseded"** by `~/Projects/gariyuu-web` — a full Next.js
site (live at gariyuuu.com) that already covers landing + an about/
résumé page with real content + a public chat demo + a password-gated
usage dashboard. That audit listed `personal-website` as **"a
candidate to delete."**

**This has not been decided or acted on.** Nothing has been deleted.
Complicating the picture: this repo is not dormant — 6 commits landed
on 2026-08-07 (the same day as this doc refresh) reworking the site
into a dark "hacker" theme with a JS boot animation, i.e. someone was
actively investing new work here very recently, which sits in tension
with the "candidate to delete" framing. **A fresh session should check
with the owner before doing feature work here** — see `HANDOFF.md`'s
"Prompt for the next Claude Code account."

## Audit timestamp

- **Original audit:** 2026-08-06, ~05:52 local time (documentation-only
  audit — 17 memory files added, no application files changed).
- **This refresh:** 2026-08-07 — re-verified against the actual
  repository (the site changed substantially since the original audit:
  it was reworked from a plain light-theme static page into a dark
  "hacker" theme with JavaScript). Added `README.md` (was the one
  missing file of the canonical 17). Corrected stale technical claims
  across the doc set (see `CHANGELOG.md` and `SESSION_LOG.md` for the
  full list) and added this supersession section.

## Git state (as of this refresh)

- **Branch:** `main` (only branch, both locally and on the remote)
- **Tracking:** `origin/main`
  (`https://github.com/Gariyuuu/personal-website.git`), up to date —
  confirmed via `git fetch origin` (read-only, no new remote commits
  beyond local `HEAD`).
- **Latest commit:** `813e215` — "Make the hacker-log flood fill the
  whole screen with a shake" (2026-08-07)
- **Full commit history (11 commits total, oldest first):**
  1. `9869c4a` — 2026-07-24 — "Initial commit"
  2. `2d4d662` — 2026-07-25 — "Update resume content, drop GPA, add
     GitHub link"
  3. `bc9786d` — 2026-07-27 — "Update profile photo"
  4. `aa8b157` — 2026-08-03 — "Ignore .DS_Store"
  5. `f344976` — 2026-08-06 — "Add favicon so the site shows an icon in
     the browser tab" (this favicon approach was later replaced — see
     below)
  6. `b27b9c9` — 2026-08-06 — "docs: add full handoff documentation
     system"
  7. `9778732` — 2026-08-07 — "Rework site into a dark hacker theme,
     add OpenReview link"
  8. `eff4591` — 2026-08-07 — "Add terminal boot-up intro animation"
  9. `c324c71` — 2026-08-07 — "Slow the rain, extend the boot sequence,
     add a hacked red screen"
  10. `88b465d` — 2026-08-07 — "Turn the hacker-log flood into
      scattered black-and-white terminal windows"
  11. `813e215` — 2026-08-07 — "Make the hacker-log flood fill the
      whole screen with a shake" (HEAD)
- **Working tree: CLEAN.** `git status --porcelain` returns nothing.
- **Uncommitted changes:** none.
- **Untracked files:** none.

Note: a separate favicon file (`favicon.ico`, a real committed binary,
22.7KB) now exists and is referenced via `<link rel="icon"
href="favicon.ico">`. The inline `data:` SVG favicon added in commit
`f344976` is no longer what's in `index.html` — it was superseded by
this real file at some point during or after the theme rework. Exactly
which commit made that swap wasn't isolated during this pass (not
load-bearing enough to justify a full `git log -p` archaeology dig for
a repo whose future is itself an open question) — flagged here as a
minor unresolved provenance detail, not a bug.

## Current state

**Complete, stable, and actively touched very recently.** The site is
a working single-page résumé wrapped in a dark hacker-theme intro
(canvas rain + boot animation), with no known bugs, no TODOs, no
placeholder content, and no broken links. It is not mid-feature — each
commit in the 2026-08-07 burst is a complete, self-contained visual
tweak to the intro sequence, and the tree is clean.

## What currently works (verified this refresh)

- `index.html` is well-formed HTML5, 611 lines (grew from ~250 at the
  last audit due to the theme rework — new `<style>` rules for the
  dark palette/boot sequence, and two `<script>` blocks).
- All internal nav anchors (`#about`, `#experience`, `#projects`,
  `#education`, `#skills`, `#honors`, `#contact`) have a matching
  `id="..."` on a real `<section>` in the body.
- All external links (GitHub, LinkedIn, OpenReview, `mailto:`) are
  well-formed and point to plausible real destinations for this repo's
  owner — not verified by live HTTP request.
- `photo.jpeg` and `favicon.ico` both exist at the paths `index.html`
  references.
- The two inline `<script>` blocks (canvas rain, boot/hack intro) are
  self-contained: no external JS libraries, no user input processed, no
  data sent anywhere. Both respect `prefers-reduced-motion` (the boot
  sequence removes itself entirely; the rain effect returns early).
- No TODO/FIXME/placeholder/lorem-ipsum text found anywhere in
  `index.html`.

## What currently fails / is unverified

- **The live production URL is unknown from within this repo.** No
  custom domain or deployment URL is recorded in any tracked file.
  `.vercel/project.json` (gitignored, local-only) confirms the
  directory is linked to a Vercel project named `personal-website`, but
  the actual public URL and whether it auto-deploys on push were not
  checked against the Vercel dashboard/CLI (read-only, no live-service
  lookup performed). See `DEPLOYMENT.md`.
- No automated tests exist (none are really applicable at this scope —
  see `TESTING.md`).
- **The supersession/deletion question is unresolved** — see the
  section at the top of this file.

## Next three recommended actions

1. **Resolve the supersession question with the owner** — is this repo
   being kept alive as an actively-styled personal page distinct from
   `gariyuu-web`, frozen as-is, or slated for deletion? This is the
   single most important open question for this repo and should come
   before any further feature work (see `HANDOFF.md`).
2. **Confirm the live deployment.** Check the Vercel dashboard (or
   `vercel ls` / `vercel inspect`) to record the actual production URL
   and whether GitHub pushes auto-deploy — a read-only check.
3. **Keep resume content current** if the owner decides to keep this
   repo — update the matching `<section>` in `index.html` whenever the
   owner's actual résumé changes. See `FEATURES.md`.
