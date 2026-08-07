# personal-website

Gary Wang's personal résumé/portfolio website — a single static HTML
page (`index.html`) with inline CSS and a small amount of inline
JavaScript, no framework, no build step, hosted on Vercel.

> ## ⚠️ Status: possibly superseded — read before contributing
>
> A cross-repo inventory audit of the owner's `~/Projects` flagged this
> repo as **likely superseded by `~/Projects/gariyuu-web`**
> (live at gariyuuu.com), a full Next.js site that already includes a
> landing page + an about/résumé page with real content + a public
> chat demo + a password-gated usage dashboard. That audit listed
> `personal-website` as **"a candidate to delete."**
>
> **Nothing has been deleted, and this has not been decided.** The
> picture is genuinely mixed: this repo received six real commits on
> 2026-08-07 reworking the site into a dark "hacker" theme with a JS
> boot animation — active, deliberate investment, made the same day it
> was flagged as a deletion candidate. Whether to keep developing this
> repo, freeze it as-is, or retire it in favor of `gariyuu-web` is an
> open question for the owner, not something a fresh AI session (or
> contributor) should decide unilaterally.
>
> **If you're picking this repo up cold: check with the owner on the
> supersession/deletion question before investing non-trivial work
> here.** See `HANDOFF.md` → "Prompt for the next Claude Code account"
> and `PROJECT_STATE.md` for the full context.

## What this is

A one-page online résumé: sticky nav, a hero section (photo, name,
headline, social links), and sections for About, Experience, Projects,
Education, Skills, Honors, and Contact. As of 2026-08-07 the page opens
with a full-screen canvas "digital rain" background effect and a
skippable terminal boot/hack-style intro animation before showing the
résumé content — a purely visual/presentational layer on top of the
same résumé content described above.

## Tech stack

- Plain HTML5 + inline CSS (one `<style>` block) + a small amount of
  inline vanilla JavaScript (two `<script>` blocks: a canvas rain
  effect and the boot-intro animation). No framework, no build step, no
  `package.json`, no dependencies.
- One external network dependency: the `Share Tech Mono` webfont from
  Google Fonts.
- Hosted on Vercel (zero-config static hosting, no `vercel.json`).

See `CLAUDE.md` for the full operating manual and `ARCHITECTURE.md` /
`UI_SYSTEM.md` / `FEATURES.md` for more detail.

## Running locally

No build step or dev server is required:

```bash
git clone https://github.com/Gariyuuu/personal-website.git
cd personal-website
open index.html
```

Or serve it locally if you want an `http://` origin for some reason:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deployment

Hosted on Vercel, linked via the gitignored `.vercel/project.json`.
Whether pushes to `main` auto-deploy via Vercel's GitHub integration or
require a manual `vercel deploy --prod` is unverified from within this
repo — see `DEPLOYMENT.md`.

## Documentation

This repo carries a full handoff-documentation set at its root, meant
to let any AI coding session (or human) pick this project up cold:
`CLAUDE.md`, `PROJECT_STATE.md`, `TASKS.md`, `HANDOFF.md`,
`SESSION_LOG.md`, `CHANGELOG.md`, `ARCHITECTURE.md`, `FEATURES.md`,
`DATABASE.md`, `SECURITY.md`, `DEPLOYMENT.md`, `TESTING.md`,
`DECISIONS.md`, `FILE_MAP.md`, `ROADMAP.md`, `UI_SYSTEM.md`, plus this
`README.md` and a bonus `API_REFERENCE.md`. Start with `CLAUDE.md`,
then `PROJECT_STATE.md`, then `HANDOFF.md` — and read the supersession
warning above before doing any feature work.

## License / ownership

Personal project, owned by Gary Wang (`Gariyuuu` on GitHub). Not
licensed for reuse; it's a résumé, not a template.
