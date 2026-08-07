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

## Inline SVG favicon (`data:` URI) instead of a favicon file

- **Status:** Verified (evidenced directly by the commit that added it)
- **Decision:** The favicon is an inline SVG encoded as a `data:` URI in
  the `<link rel="icon">` tag, not a separate `favicon.ico`/`.png`/`.svg`
  file.
- **Evidence:** Commit `f344976`, "Add favicon so the site shows an
  icon in the browser tab" — added exactly one line (the `<link
  rel="icon" href="data:image/svg+xml,...">` tag) with no new file
  added to the repo.
- **Why (inferred):** Keeps the "one file is the whole site" property
  intact — no second asset file needed just for a tab icon.

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

## GPA removed from Education section

- **Status:** Verified
- **Decision:** GPA was present in an earlier version of the resume
  content and was deliberately removed.
- **Evidence:** Commit `2d4d662`'s message: "Update resume content,
  drop GPA, add GitHub link."
- **Why:** Not recorded beyond the commit message — a personal/content
  choice by the resume's owner, not a technical one.
