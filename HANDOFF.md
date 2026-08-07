# HANDOFF.md — Start Here

You are picking up **personal-website** with no memory of any prior
conversation. This file is your fastest path to being useful. This
project is small — you should be able to read every memory file in
this repo (and `index.html` itself) in a few minutes.

## What is this project?

Gary Wang's personal résumé/portfolio website: one static HTML page
(`index.html`) with inline CSS, no JavaScript, no framework, no build
step, hosted on Vercel. One image (`photo.jpeg`). That's the entire
project.

## What should I read first?

Given how small this repo is, you don't need much:

1. `CLAUDE.md` — full operating manual (identity, stack, conventions,
   "DO NOT CHANGE WITHOUT REVIEW").
2. `PROJECT_STATE.md` — exact current git/repo state.
3. `index.html` itself — it's ~250 lines; just read the whole thing
   rather than relying on `FEATURES.md`'s summary for anything you're
   about to edit.

Everything else (`ARCHITECTURE.md`, `FILE_MAP.md`, `FEATURES.md`,
`TASKS.md`, `ROADMAP.md`, `DECISIONS.md`, `DATABASE.md`,
`API_REFERENCE.md`, `UI_SYSTEM.md`, `SECURITY.md`, `TESTING.md`,
`DEPLOYMENT.md`, `CHANGELOG.md`, `SESSION_LOG.md`) is there for
completeness/consistency with the docs system used across this
developer's other repos, but most of it says "N/A, does not apply"
because this really is just one static page.

## What is the current task?

**Nothing is in progress.** The site is complete and stable. The
working tree is clean (`main`, HEAD `f344976`, up to date with
`origin/main`, nothing uncommitted). This session's only work was
building this documentation system — no application code was touched.

## What was the previous agent doing?

Building this 17-file documentation system from scratch (this repo had
zero documentation files before this session) — a full repo audit
followed by an account-switch checkpoint pass, per the same pattern
used on this developer's other `~/Projects` repos.

## What works right now?

Everything. The page loads, the photo renders, the favicon shows, all
7 nav anchors scroll to their matching section, and all external links
(GitHub, LinkedIn, mailto) point to real, correctly-formed
destinations. See `PROJECT_STATE.md` → "What currently works" for the
specific checks performed.

## What is broken?

Nothing. No known bugs, no TODOs, no broken links.

## Dangerous-to-modify areas

Nothing here is "dangerous" in the sense of breaking a live system —
there's no backend/database to corrupt. The closest things to a caution
list (see `CLAUDE.md` → "DO NOT CHANGE WITHOUT REVIEW"):

- Don't hand-edit or commit `.vercel/project.json` — it links this
  checkout to the existing live Vercel project; mishandling it risks
  creating a duplicate project or unlinking deploys.
- Don't change the owner's real contact details (email/GitHub/
  LinkedIn) without being explicitly told to.

## Which commands should I run first?

```bash
cd ~/Projects/personal-website
git status                 # confirm this matches PROJECT_STATE.md — should be clean
open index.html            # preview the page locally, no server/build needed
```

There is no `npm install`, no build, no lint, no test command — none of
those tools exist in this repo (see `CLAUDE.md` → Essential commands).

## How do I verify the app still works?

Open `index.html` in a browser and walk `TESTING.md`'s manual
smoke-test checklist (page loads, image renders, favicon shows, nav
anchors work, external links are correct, responsive layout collapses
correctly below 560px). There's no automated way to verify this beyond
looking at it — that's expected and sufficient at this scope.

---

## Prompt for the next Claude Code account

Copy-paste this to start a new session cleanly:

```
Read CLAUDE.md and PROJECT_STATE.md in full before doing anything else
(they're short — this is a tiny static-site repo, not a big app).
Then:

1. Run `git status` and `git log --oneline -5` and confirm the repo
   state matches what PROJECT_STATE.md describes. If it doesn't, stop
   and tell me what's different before proceeding.
2. Read index.html in full (it's ~250 lines) rather than trusting
   FEATURES.md's summary, if you're about to edit content.
3. In 2-3 sentences, confirm your understanding of: what this project
   is, and what the current task is (as of this writing: nothing is in
   progress — it's a complete, stable resume page).
4. Do not add a framework, build step, backend, analytics, or any new
   dependency unless I explicitly ask for it — the plain-static-HTML
   approach is a deliberate, standing decision (see DECISIONS.md), not
   an oversight.
5. If I ask for a content update (new job, new project, etc.), edit
   index.html directly following the existing markup pattern for that
   section (see FILE_MAP.md's edit guidance), then walk TESTING.md's
   manual smoke-test checklist before considering it done.
6. After any meaningful change, update PROJECT_STATE.md, CHANGELOG.md,
   and append to SESSION_LOG.md before ending your session.
```
