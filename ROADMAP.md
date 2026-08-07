# ROADMAP.md

This is a small, essentially-finished personal resume site. There is no
formal product roadmap — this file exists mainly to record what's
explicitly *not* planned, so a future session doesn't accidentally
"improve" the site into something it isn't meant to be.

## Current milestone

None. The site is complete for its purpose (an online resume/portfolio
link to share). No milestone is currently being worked toward.

**Note:** this repo is flagged as possibly superseded by
`~/Projects/gariyuu-web` (see `PROJECT_STATE.md`/`HANDOFF.md`). None of
the ideas below should be started without first checking that question
with the owner — no point roadmapping a repo that might be retired.

## Long-term ideas (not committed to, not scheduled)

These are plausible, low-effort future additions if the owner ever
wants them — none are requested or approved, listed only so a future
session has context if asked to brainstorm:

- A light-mode toggle/`prefers-color-scheme` support (the site was
  reworked into one fixed dark "hacker" theme on 2026-08-07 — see
  `DECISIONS.md`; there is currently no way to view it in a light
  theme).
- A second page (e.g. a longer project write-up, a blog) — would be the
  first time this repo becomes more than one page, and would be worth a
  `DECISIONS.md` entry if it happens (routing approach, whether to stay
  build-step-free).
- Open Graph / social share preview meta tags (currently only a basic
  `<meta name="description">` exists — no `og:image`/`og:title`/etc.).
- A custom domain (currently the production URL, if any, is whatever
  Vercel assigns by default — see `DEPLOYMENT.md`).

## Out of scope

Explicit non-goals for this project, per its nature as a static resume
page:

- No backend, no database, no user accounts — this will never need
  server-side logic to be "a resume page."
- No contact form (a `mailto:` link is sufficient and avoids needing
  any backend/email-sending service).
- No analytics/tracking scripts.
- No CMS — content changes are direct edits to `index.html`, and that's
  fine at this scale.
- No test suite — there's no logic to unit-test; visual/manual
  verification (see `TESTING.md`) is sufficient and appropriate here.

If a future request pushes meaningfully past "a one-page static
resume," treat that as a scope change worth flagging to the owner
explicitly rather than assuming it's wanted.
