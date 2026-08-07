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
- **No JavaScript.** No XSS surface from client-side scripting (there is
  no script on the page to exploit) and no third-party JS dependencies
  to worry about supply-chain risk from.
- **No secrets in the repo.** Checked directly during this audit: no
  `.env` files, no API keys, no tokens, no credentials anywhere in
  `index.html`, `.gitignore`, or the tracked files. The only
  "identifiers" present are the owner's intentionally-public contact
  details (email, GitHub username, LinkedIn URL) — these are meant to
  be public, not sensitive.

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
