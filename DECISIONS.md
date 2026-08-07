# DECISIONS.md

Architectural/technical decisions recoverable from this repo. Each is
labeled **Verified** (directly evidenced by repo contents) or
**Inferred** (a reasonable read of the evidence, but the "why" wasn't
recorded anywhere explicit).

## Plain static HTML instead of a framework

- **Status:** Inferred
- **Decision:** Build the site as a single hand-written HTML file with
  inline CSS, no JavaScript, no framework (no React/Next.js/etc.), and
  no build step.
- **Evidence:** No `package.json` exists anywhere in the repo; git log
  shows the site was committed as a complete, working `index.html` from
  the very first commit (`9869c4a`, "Initial commit," 234 lines) and has
  only ever received content edits since — never a framework migration.
- **Why (inferred, not stated anywhere in the repo):** For a single
  static resume page with no interactivity beyond links, a framework
  and build pipeline would add maintenance overhead (dependencies to
  update, a build step to keep working, a `node_modules` to manage) with
  no functional benefit. Plain HTML is also trivially portable to any
  static host.

## Inline `<style>` block instead of a separate CSS file

- **Status:** Inferred
- **Decision:** All CSS lives in one `<style>` block inside
  `index.html`'s `<head>`, rather than a linked external `.css` file.
- **Evidence:** Direct inspection of `index.html` — no `<link
  rel="stylesheet">` tag exists anywhere in the file.
- **Why (inferred):** At ~100 lines of CSS for a one-page site, a
  separate file would add an HTTP request and a second file to keep in
  sync with no real benefit; inlining keeps the entire site in exactly
  one file.

## Favicon: inline SVG (original), later replaced by a real `favicon.ico` file

- **Status:** Verified, but superseded — flagged during the 2026-08-07
  doc refresh as a place the docs had gone stale.
- **Original decision (commit `f344976`, 2026-08-06):** The favicon was
  an inline SVG encoded as a `data:` URI in the `<link rel="icon">`
  tag, not a separate file — "Add favicon so the site shows an icon in
  the browser tab," one line added, no new file.
- **Current state (verified 2026-08-07):** `index.html` now references
  `<link rel="icon" href="favicon.ico">`, and a real `favicon.ico`
  binary file (22.7KB) is committed at the repo root. The inline `data:`
  SVG approach is no longer in use.
- **Why the switch happened:** Not recorded in any commit message found
  during this pass — likely alongside or shortly after the 2026-08-07
  dark hacker-theme rework, to get a more detailed/multi-resolution
  icon than a simple inline SVG could easily provide. Exactly which
  commit made the swap wasn't isolated (see `PROJECT_STATE.md`).

## Vercel for hosting

- **Status:** Verified
- **Decision:** Deploy via Vercel.
- **Evidence:** `.vercel/project.json` (gitignored, local-only) links
  this directory to a Vercel project named `personal-website`.
- **Why (inferred):** Consistent with this user's convention across
  other `~/Projects` subfolders (per the user's own account notes) —
  Vercel is the default hosting choice used across their projects, and
  it requires zero configuration for a plain static HTML site.

## No `vercel.json`

- **Status:** Verified
- **Decision:** No `vercel.json` config file exists in the repo.
- **Evidence:** Directory listing of the repo root shows only
  `index.html`, `photo.jpeg`, `.gitignore`, and the gitignored
  `.vercel/`.
- **Why (inferred):** Vercel's zero-config static-file detection is
  sufficient for a single HTML file with no build step — there's
  nothing to configure (no build command, no output directory
  override, no redirects/headers needed).

## Dark "hacker" theme rework + JS boot animation

- **Status:** Verified
- **Decision:** Replaced the original light theme with a dark,
  near-black "hacker" palette (green/cyan accents), switched fonts to
  the `Share Tech Mono` Google Fonts monospace webfont, added a
  full-screen canvas "digital rain" background effect, and added a
  skippable JS terminal boot/hack-intro animation that plays once on
  page load.
- **Evidence:** Five commits on 2026-08-07: `9778732` ("Rework site
  into a dark hacker theme, add OpenReview link"), `eff4591` ("Add
  terminal boot-up intro animation"), `c324c71` ("Slow the rain, extend
  the boot sequence, add a hacked red screen"), `88b465d` ("Turn the
  hacker-log flood into scattered black-and-white terminal windows"),
  `813e215` ("Make the hacker-log flood fill the whole screen with a
  shake").
- **Why:** Not recorded beyond the commit messages — reads as a
  personal-branding/visual-style choice by the owner, not a technical
  one. Worth noting: this is a real, deliberate, multi-commit
  investment in this site's *presentation*, made on the same day this
  repo was separately flagged as a possible deletion candidate in favor
  of `gariyuu-web` (see `PROJECT_STATE.md`) — the two facts are in
  tension and haven't been reconciled with the owner as of this
  writing.
- **Note on prior docs:** the 2026-08-06 documentation baseline
  described the (then-accurate) light theme, no-JS, system-font state.
  Those claims were corrected during the 2026-08-07 doc refresh; this
  entry exists so the "why did the docs change" question has an answer
  in one place.

## GPA removed from Education section

- **Status:** Verified
- **Decision:** GPA was present in an earlier version of the resume
  content and was deliberately removed.
- **Evidence:** Commit `2d4d662`'s message: "Update resume content,
  drop GPA, add GitHub link."
- **Why:** Not recorded beyond the commit message — a personal/content
  choice by the resume's owner, not a technical one.
