# CLAUDE.md — Operating Manual for personal-website

> ## ⚠️ POSSIBLY SUPERSEDED — READ BEFORE DOING ANY FEATURE WORK
> A prior cross-repo inventory audit flagged this project as **likely
> superseded** by `~/Projects/gariyuu-web`, a full Next.js build that
> covers landing + about/résumé (with real content) + a public chat
> demo + a password-gated dashboard. `gariyuu-web` is the
> actively-maintained, full-featured replacement candidate; this repo
> was listed as **"a candidate to delete."**
>
> That said — as of this doc refresh (2026-08-07), this repo is **not
> dormant**: it received 6 new commits *today* reworking the site into
> a dark "hacker" theme with a JS boot animation, on top of the docs
> commit. So there is active, recent investment here even though the
> supersession question has never been resolved.
>
> **No deletion has happened. This is not yet decided.** Before
> starting any new feature work here, **check with the owner** on
> whether this repo should keep being developed, be frozen as-is, or
> be deleted in favor of `gariyuu-web`. See `PROJECT_STATE.md` and
> `HANDOFF.md` for the full framing, and `HANDOFF.md`'s "Prompt for the
> next Claude Code account" section for exact wording to open with.

This file is the primary entry point for any AI coding agent (or human)
picking up this repository. Read this first, then `PROJECT_STATE.md`,
then `TASKS.md`, before touching anything.

This entire memory system (`CLAUDE.md`, `PROJECT_STATE.md`,
`ARCHITECTURE.md`, `FILE_MAP.md`, `FEATURES.md`, `TASKS.md`,
`ROADMAP.md`, `DECISIONS.md`, `DATABASE.md`, `API_REFERENCE.md`,
`UI_SYSTEM.md`, `SECURITY.md`, `TESTING.md`, `DEPLOYMENT.md`,
`CHANGELOG.md`, `SESSION_LOG.md`, `HANDOFF.md`, `README.md`) was
generated on **2026-08-06** by auditing the actual repository (files,
`.gitignore`, `.vercel/` config, git history), and **refreshed on
2026-08-07** after the site was reworked into a dark hacker theme with
JavaScript — not by recalling prior chat history. Where something
couldn't be verified from the repo alone, it is labeled **Inferred** or
**Unverified** rather than stated as fact.

**Scope note up front:** this is an intentionally tiny project — one
static HTML file, one photo, and Vercel hosting config. Do not
over-document it as if it were a complex app, and do not add framework,
build-step, or backend structure that doesn't exist just to fill out
these files. Several of the 17 files below are short by design, some
almost entirely "N/A" — that is correct for this repo's scope, not a
sign that the documentation is incomplete.

## Project identity

- **Name:** personal-website (GitHub repo: `Gariyuuu/personal-website`)
- **One-sentence description:** Gary Wang's personal résumé/portfolio
  website — a single static HTML page with inline CSS, no JavaScript,
  no build step.
- **Detailed summary:** A one-page online résumé: sticky nav, hero with
  photo/headline/social links, and sections for About, Experience,
  Projects, Education, Skills, Honors, and Contact. Content is a
  hand-authored HTML rendering of the owner's resume. As of 2026-08-07
  the page is wrapped in a dark "hacker" visual theme — a full-screen
  Matrix-style canvas rain effect and a skippable JS terminal
  boot/"hack" intro sequence play before the résumé content is shown —
  layered on top of the same résumé content and section structure
  described above. See `FEATURES.md` and `UI_SYSTEM.md`.
- **Target audience:** Anyone the owner shares the link with (e.g.
  recruiters, collaborators) — a public, always-current online resume.
- **Current development stage:** Complete and stable for its current
  scope. It is a living document — content (job history, projects) gets
  updated periodically as the owner's resume changes — not a
  feature-in-progress site.
- **Production status:** Linked to a Vercel project (see
  `.vercel/project.json`, `projectName: "personal-website"`), pushed to
  GitHub and up to date with `origin/main`. The live production URL is
  **Unverified** from within this repo (no custom domain or deployment
  URL is recorded in any tracked file) — see `DEPLOYMENT.md`.
- **Repository type:** Single, tiny static site. Not a monorepo, not
  part of any other project in `~/Projects`.
- **Important scope note:** `~/Projects` (the parent of this repo) is
  **not** a monorepo — it's a collection of unrelated, independently
  pushed git repos belonging to the same developer. Nothing in this
  memory system applies outside `~/Projects/personal-website`.

## Current status

See `PROJECT_STATE.md` for the exact, timestamped snapshot. Summary:

- The site is complete, working, and the working tree is **clean**
  (nothing uncommitted, nothing untracked) as of the 2026-08-06 audit.
- **Current blockers:** None.
- **Highest-priority next task:** None queued. This is a maintenance-only
  project — the only "next actions" are content updates (resume
  changes) or optional low-effort hygiene items noted in `TASKS.md` /
  `PROJECT_STATE.md`.

## Technology stack

- **Language/markup:** Plain HTML5 + CSS + a small amount of vanilla
  JavaScript (two inline `<script>` IIFEs at the end of `<body>`: a
  canvas "digital rain" background effect, and a scripted terminal
  boot/hack-intro sequence that runs once per page load and can be
  skipped by click/keypress). No JS framework, no build step for the
  JS — it's hand-written inline script, same as the CSS.
- **Framework:** None. No React/Next.js/Vue/etc. No `package.json`
  exists in this repo — there are no npm dependencies at all.
- **Build step:** None. `index.html` is served as-is; there is nothing
  to compile, bundle, or transpile.
- **Styling:** Inline `<style>` block using CSS custom properties
  (`:root { --text; --muted; --line; --accent; --accent-2; --bg;
  --surface; --maxw }`), now a dark/near-black "hacker" palette (green
  accent `#00ff8c`, cyan accent `#00e5ff`). No Tailwind, no CSS
  framework, no CSS-in-JS. See `UI_SYSTEM.md`.
- **Fonts:** `"Share Tech Mono"` monospace webfont loaded from Google
  Fonts (`<link rel="preconnect">` to `fonts.googleapis.com`/
  `fonts.gstatic.com` + a `fonts.googleapis.com/css2?family=...`
  stylesheet link), falling back to system monospace fonts. This is a
  real third-party network request added during the 2026-08-07 theme
  rework — earlier docs describing "system font stack only, no Google
  Fonts" predate this change.
- **Icons:** Inline SVG paths, hand-authored directly in `index.html`
  (GitHub/LinkedIn/Email glyphs, plus an OpenReview glyph added
  2026-08-07). Favicon is a separate committed file, `favicon.ico`
  (referenced via `<link rel="icon" href="favicon.ico">`) — earlier
  docs describing an inline `data:` SVG favicon are outdated; that
  approach was replaced by this real `favicon.ico` file at some point
  before this refresh.
- **Images:** One JPEG, `photo.jpeg` (400×400px, ~31KB), referenced as
  a CSS `background-image` for the circular avatar.
- **Hosting:** Vercel. `.vercel/project.json` (gitignored, local-only)
  shows `projectName: "personal-website"`. No `vercel.json` in the repo
  — deployment relies entirely on Vercel's default static-file handling.
- **Database:** None. See `DATABASE.md`.
- **Backend / API routes:** None. See `API_REFERENCE.md`.
- **Auth:** None. No login, no forms, no user input of any kind — the
  only interactive elements are anchor links and `mailto:`/external
  links.
- **Testing:** None. See `TESTING.md`.
- **Package manager:** None — no `package.json`, no lockfile, no
  `node_modules`.
- **Version control:** Git, GitHub remote `Gariyuuu/personal-website`
  (public, per this user's convention of pushing `~/Projects`
  subfolders as separate repos — see the user's GitHub-account memory
  note).

## Essential commands

There is no build tool, package manager, or dev server configured in
this repo. To preview the page locally, either:

```bash
# Option A — just open the file directly (no server needed; the page
# has no relative-path JS/fetch calls that would require http:// origin)
open index.html

# Option B — serve it locally (only needed if you want to test
# something origin-sensitive, which nothing here currently requires)
cd ~/Projects/personal-website
python3 -m http.server 8000
# then visit http://localhost:8000
```

There is no `npm install`, `npm run dev`, `npm run build`, `npm run
lint`, or test command — none of those tools are present in this repo.

Deployment (see `DEPLOYMENT.md` for full detail):

```bash
# If the Vercel CLI is installed and authenticated:
npx vercel deploy --prod
```

Whether pushing to `main` also triggers an automatic Vercel deployment
(via Vercel's GitHub integration) could not be confirmed from repo
files alone — `.vercel/project.json` only proves the directory is
*linked* to a Vercel project, not what that project's Git-integration
setting is. See `DEPLOYMENT.md`.

## Repository structure

```
personal-website/
├── index.html          # THE entire site. One file: <head> (meta, title,
│                        #   inline favicon, inline <style>) + <body> (nav,
│                        #   hero, 7 content sections, footer). No external
│                        #   CSS/JS files are referenced.
├── photo.jpeg           # Profile photo (400x400 JPEG), used as the CSS
│                        #   background-image for the circular avatar in
│                        #   the hero section. Only image asset in the repo.
├── favicon.ico           # Browser-tab icon, committed binary file
│                          #   (replaced an earlier inline data:-URI SVG
│                          #   favicon at some point before 2026-08-07).
├── .vercel/              # Vercel CLI link metadata. GITIGNORED — not
│   ├── project.json       #   committed to git. Contains projectId/orgId/
│   └── README.txt         #   projectName (Vercel's own auto-generated
│                           #   README explaining the folder).
└── .gitignore             # Ignores `.vercel` and `.DS_Store`. Nothing else.
```

**What should NOT be placed where:** there is no meaningful "where does
this go" question at this scope — there is exactly one content file. If
the site ever grows beyond a single page (e.g. a second page, a
separate CSS/JS file), that would be a real structural decision worth
recording in `DECISIONS.md` at the time, not something to pre-guess
here.

## Architecture summary

See `ARCHITECTURE.md` for the full write-up with a diagram. Short
version: browser requests `index.html` → Vercel's static file host
serves it (and `photo.jpeg`) directly, byte-for-byte, from what's in
the git repo. No server-side rendering, no API calls, no client-side
routing, no build artifacts sitting between the source file and what a
visitor sees.

## Coding conventions

Observed directly from `index.html` (Verified):

- **Single-file HTML** with an inline `<style>` block — no external
  stylesheet, no CSS modules, no preprocessor.
- **Semantic sectioning:** `<nav>`, `<header class="hero">`, one
  `<section id="...">` per resume category, `<footer>` — each section
  has a matching in-page anchor link in the nav.
- **CSS naming:** plain, short, descriptive class names (`.hero`,
  `.avatar`, `.social`, `.item`, `.skills`, `.honors`) — no BEM, no
  utility-class framework.
- **CSS custom properties** for the small color/sizing palette,
  declared once under `:root` and referenced via `var(--x)` throughout.
- **JavaScript:** two small inline `<script>` IIFEs at the end of
  `<body>` (canvas rain background + boot/hack intro sequence) — see
  the "Technology stack" section above. Nav anchor scrolling itself is
  still native browser behavior (`html { scroll-behavior: smooth; }`),
  not JS-driven.
- **Responsive:** one `@media (max-width: 560px)` breakpoint collapsing
  the two-column `.item` grid to one column and reducing hero padding.
  One `@media print` rule hides the nav when printing.
- If you add content, match the existing pattern: a new `<section
  id="...">` plus a matching nav `<a class="link" href="#...">` — don't
  introduce a new structural pattern for one new section.

## UI and design system

Full detail in `UI_SYSTEM.md`. Key facts (updated 2026-08-07 for the
dark hacker-theme rework): dark theme only (near-black background,
green/cyan accents — no `prefers-color-scheme` handling, just one fixed
dark palette), max content width `720px` centered, accent color
`#00ff8c` (green) with a `#00e5ff` (cyan) secondary accent, body copy
`16px/1.7`, `"Share Tech Mono"` monospace webfont (Google Fonts, with
system-monospace fallback), single responsive breakpoint at `560px`,
plus a full-screen canvas rain effect and a one-time skippable terminal
boot animation on load.

## Environment setup

**No environment variables exist in this repo.** There is no
`.env`/`.env.local`/`.env.example` file, and nothing in `index.html`
reads any runtime configuration — everything is hardcoded static
markup. Nothing to set up beyond having the two files present.

## Database summary

There is no database of any kind. See `DATABASE.md`.

## Authentication and authorization

There is no authentication system, no login, no user accounts, no
forms that collect or submit data. See `SECURITY.md`.

## API and integrations

There are no API routes, no backend, and no third-party API calls. The
only outbound links are static `href`s to GitHub, LinkedIn, and a
`mailto:` address. See `API_REFERENCE.md`.

## Testing and verification

No automated tests exist and none are appropriate to add given the
site has no logic to test — it's static markup. See `TESTING.md` for
the manual smoke-test checklist to run after any content change.

## Deployment

Full detail in `DEPLOYMENT.md`. Summary: hosted on Vercel (project
`personal-website`, linked via the gitignored `.vercel/project.json`).
Whether deploys are automatic on push to `main` (Vercel's GitHub
integration) or require a manual `vercel deploy --prod` could not be
confirmed from repo files alone — flagged as Unverified, check the
Vercel dashboard to confirm.

## Critical rules — DO NOT CHANGE WITHOUT REVIEW

- **`.vercel/project.json`** — do not delete or hand-edit this file's
  `projectId`/`orgId` values; doing so would unlink this local checkout
  from the existing live Vercel project (a new `vercel link` would be
  needed to reconnect, and could accidentally create a *second*,
  duplicate Vercel project if done carelessly). It's already gitignored
  correctly — do not remove it from `.gitignore` or commit it; Vercel's
  own guidance (`.vercel/README.txt`) is explicit that this folder
  should never be shared/committed.
- **Contact info accuracy** — the email (`gywng006@gmail.com`), GitHub
  (`Gariyuuu`), LinkedIn, and OpenReview URLs in `index.html` are the
  owner's real, public contact/profile details. Don't alter them
  without being told to; a typo here silently breaks how people reach
  the site's owner.
- **`.gitignore`** — keep `.vercel` and `.DS_Store` ignored. Don't add
  broad patterns that could accidentally re-include or exclude the wrong
  files given how small this repo is (there's nothing else to protect,
  but also nothing else that should ever need a special-case rule
  without a clear reason).

## Known issues

None found. No TODO/FIXME/placeholder text, no broken or obviously
temporary hardcoded content, and no dead links were found in
`index.html` during this audit (checked every `href=` and the
`background: url('photo.jpeg')` reference — all resolve to either a
real in-page anchor, a real external URL, or a file that exists in the
repo). The production deployment URL / custom domain is simply
**not recorded anywhere in this repo** — that's a documentation gap
about the live site, not a bug in the site itself. See `DEPLOYMENT.md`.

## AI working instructions

Future Claude Code sessions (or any AI agent) working in this repo
must:

1. Read `CLAUDE.md` (this file).
2. Read `PROJECT_STATE.md`.
3. Read `TASKS.md`.
4. Read whichever of `ARCHITECTURE.md` / `FEATURES.md` / `UI_SYSTEM.md`
   / `DEPLOYMENT.md` is relevant to the task at hand.
5. Inspect `index.html` directly before changing it — it's short
   (~250 lines); read the whole file rather than trusting a
   description of it.
6. Check `git status` before modifying files.
7. Avoid overwriting unrelated work (e.g. a resume update the owner is
   mid-editing).
8. Make small, reviewable changes — this file is easy to diff; keep it
   that way (don't reformat the whole file for an unrelated content
   edit).
9. There is no build/lint/test command to run after changes — instead,
   open `index.html` in a browser (or re-read it) and visually/
   structurally confirm the change, per `TESTING.md`'s manual checklist.
10. Update documentation after meaningful changes (see the permanent
    rules below).
11. Never claim something "works" without actually opening/inspecting
    the rendered page or the file — don't assume a text edit rendered
    correctly.
12. Never expose secrets — note that none exist in this repo currently
    (no env vars, no API keys); if that ever changes, treat it as a
    SECURITY.md-worthy event immediately.
13. Never commit `.vercel/` — it's gitignored for a reason (see
    Critical rules above).
14. Never perform destructive git operations (`reset --hard`,
    force-push, `clean -f`) without explicit permission.
15. Never silently introduce a framework, build step, or backend "while
    touching something else" — this site is deliberately a plain static
    page; that's a real, standing decision (see `DECISIONS.md`), not an
    oversight to "fix."
16. Never add tracking/analytics scripts or further third-party
    resource loads beyond the existing Google Fonts stylesheet without
    being asked — the current script (canvas rain + boot animation) is
    self-contained, first-party, and takes no user input; keep it that
    way (see `SECURITY.md`).
17. Never change the owner's real contact details (email/GitHub/
    LinkedIn) without explicit instruction.
18. Record unresolved uncertainty (e.g. "is auto-deploy actually
    configured on Vercel?") in the relevant memory file rather than
    guessing and presenting a guess as fact.

## Permanent rules for future development

**After every meaningful task:**

1. Update `PROJECT_STATE.md` with the new exact stopping point.
2. Update `TASKS.md` if anything changed (move/close tasks, add newly
   discovered ones).
3. Append an entry to `SESSION_LOG.md` (do not overwrite prior
   entries).
4. Update `FEATURES.md` / `UI_SYSTEM.md` / `DEPLOYMENT.md` if the
   change touched content, styling, or hosting config respectively.
5. Record meaningful decisions in `DECISIONS.md`.
6. Manually verify per `TESTING.md`'s checklist.
7. Clearly record anything not verified (e.g. "edited but not
   previewed in a browser") rather than implying full verification.

**Before every meaningful task:**

1. Read `CLAUDE.md`.
2. Read `PROJECT_STATE.md`.
3. Read `TASKS.md`.
4. Run `git status` and `git diff` (or `git diff --stat`).
5. Read `index.html` in full before editing it (it's short — there's
   no excuse to work from a stale mental model of it).
6. Confirm the requested work isn't already done.
7. Preserve unrelated work — don't `git checkout`/`reset`/`clean`
   without first stashing or confirming with the user.
