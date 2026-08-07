# SECURITY.md

The security surface of this project is intentionally minimal — it's a
static HTML page with no backend, no user input, and no secrets. This
file states that explicitly rather than manufacturing risk analysis for
attack surfaces that don't exist here.

## What does NOT apply here

- **No user input of any kind.** There are no forms, no text fields, no
  file uploads, no query-param handling, no cookies. Nothing a visitor
  types or sends is ever processed by this site.
- **No authentication/authorization.** No login, no sessions, no
  passwords, no tokens. See `DATABASE.md`/`API_REFERENCE.md` — there's
  no backend to authenticate against.
- **No database.** Nothing to inject into, no data to leak.
- **Minimal JavaScript, no user input.** As of 2026-08-07 `index.html`
  contains two small inline `<script>` blocks (a canvas rain effect and
  a boot-intro animation — see `ARCHITECTURE.md`). Both are
  hand-written, first-party, and process no user input of any kind (no
  `innerHTML` built from anything except hardcoded string arrays in the
  script itself) — there's no realistic XSS surface. There are no
  third-party JS *library* dependencies (no CDN `<script src>` tags),
  so no JS supply-chain risk in the traditional sense.
- **One third-party network dependency: Google Fonts.** `index.html`
  loads the `Share Tech Mono` webfont via `fonts.googleapis.com`/
  `fonts.gstatic.com` (added 2026-08-07). This is a real outbound
  request to a third party (Google) that earlier versions of this doc
  didn't have to account for — it's a low-risk, widely-used CDN font
  load, not tracking/analytics, but it is a dependency on a resource
  outside this repo's control (if Google Fonts is ever unreachable,
  the page falls back to its declared system-monospace fonts rather
  than breaking).
- **No secrets in the repo.** Checked directly during this pass (and
  the earlier 2026-08-06 audit): no `.env` files, no API keys, no
  tokens, no credentials anywhere in `index.html`, `.gitignore`, or the
  tracked files. The only "identifiers" present are the owner's
  intentionally-public contact details (email, GitHub username,
  LinkedIn URL, OpenReview profile URL) — these are meant to be public,
  not sensitive. Note: `DEPLOYMENT.md` quotes the Vercel `projectId`/
  `orgId` from the gitignored `.vercel/project.json` — these are
  project identifiers, not credentials that grant access on their own,
  but they are now visible in a committed, public doc file; flagged
  here for awareness rather than as an actual leak.

## What does apply

- **`.vercel/project.json`** contains a Vercel `projectId` and `orgId`.
  These are not secrets in the sense of granting access on their own
  (no API token is stored there), but the file is correctly gitignored
  and should stay that way — no reason to ever commit it.
- **Content accuracy is the main "risk."** Since the only "data" here is
  the owner's public resume content, the main thing to get wrong is
  accidentally publishing something the owner didn't intend (e.g. a
  stale draft, a typo'd email address that sends mail to the wrong
  person). Treat content edits with the same care as any small factual
  edit, not as a security issue — but it's worth naming since it's the
  closest thing to a real risk this project has.
- **Third-party links.** The GitHub/LinkedIn/mailto links point to
  real, presumably-owner-controlled destinations. If these are ever
  changed, verify the new destination is correct and actually
  controlled by the site's owner before publishing.

## Recommendations if scope ever grows

If a contact form, analytics, or any backend is ever added to this
site, revisit this file at that time — none of the above analysis would
still hold once real user input or third-party scripts enter the
picture.
