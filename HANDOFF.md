# HANDOFF.md — Start Here

You are picking up **personal-website** with no memory of any prior
conversation. This file is your fastest path to being useful.

## ⚠️ Read this before anything else

A prior cross-repo inventory audit flagged this project as **likely
superseded** by `~/Projects/gariyuu-web` (live at gariyuuu.com) — a
full Next.js build that already covers landing + an about/résumé page
with real content + a public chat demo + a password-gated usage
dashboard aggregating the owner's other apps. That audit listed
`personal-website` as **"a candidate to delete."**

**Nothing has been deleted. This has not been decided.** At the same
time, this repo is clearly not abandoned — 6 commits landed on
2026-08-07 reworking the site into a dark "hacker" theme with a JS
boot animation. So there's real, recent, deliberate investment here
even though the supersession question is still open. Do not resolve
this tension yourself by assuming either "it's dead, ignore it" or
"it's clearly still wanted, keep building." **Ask the owner.** See the
prompt at the bottom of this file.

## What is this project?

Gary Wang's personal résumé/portfolio website: one static HTML page
(`index.html`) with inline CSS and a small amount of inline JavaScript,
no framework, no build step, hosted on Vercel. As of 2026-08-07 the
page opens with a full-screen canvas "digital rain" effect and a
skippable terminal boot/hack-style intro animation before showing the
résumé content (nav, hero, About/Experience/Projects/Education/Skills/
Honors/Contact sections). One image (`photo.jpeg`) plus a favicon
(`favicon.ico`). That's the entire project.

## What should I read first?

1. `CLAUDE.md` — full operating manual (identity, stack, conventions,
   "DO NOT CHANGE WITHOUT REVIEW"), also carries the supersession
   warning at the top.
2. `PROJECT_STATE.md` — exact current git/repo state and the fuller
   supersession write-up.
3. `index.html` itself — it's ~611 lines now (grew from ~250 due to
   the 2026-08-07 theme rework); read the whole thing rather than
   relying on `FEATURES.md`'s summary for anything you're about to
   edit.

Everything else (`ARCHITECTURE.md`, `FILE_MAP.md`, `FEATURES.md`,
`TASKS.md`, `ROADMAP.md`, `DECISIONS.md`, `DATABASE.md`,
`API_REFERENCE.md`, `UI_SYSTEM.md`, `SECURITY.md`, `TESTING.md`,
`DEPLOYMENT.md`, `CHANGELOG.md`, `SESSION_LOG.md`, `README.md`) is
there for completeness/consistency with the docs system used across
this developer's other repos.

## What is the current task?

**Nothing is in progress**, and no new feature work should start
without first checking the supersession question with the owner (see
above). The working tree is clean (`main`, HEAD `813e215`, up to date
with `origin/main`, nothing uncommitted). The most recent work (six
commits on 2026-08-07) was a visual rework of the site into a dark
hacker theme with a boot-sequence animation — that work is complete
and stable, not mid-flight.

## What was the previous agent doing?

This pass (2026-08-07) re-verified all 16 existing doc files against
the actual repo — which had drifted significantly from the 2026-08-06
documentation baseline (the site gained a dark theme, JavaScript, a
Google Fonts webfont, a new OpenReview link, and a real `favicon.ico`
file since that baseline) — corrected the stale technical claims,
added the missing `README.md` (17th file), and added the supersession
flag throughout. No application code (`index.html`) was changed.

Before that, an earlier session built the original 16-file
documentation system from scratch (2026-08-06), and other sessions did
the actual hacker-theme rework (2026-08-07, commits `9778732` through
`813e215`).

## What works right now?

Everything. The page loads, the boot animation plays and can be
skipped (click or any keypress), the rain background renders, the
photo and favicon render, all 7 nav anchors scroll to their matching
section, and all external links (GitHub, LinkedIn, OpenReview, mailto)
point to real, correctly-formed destinations.

## What is broken?

Nothing. No known bugs, no TODOs, no broken links.

## Dangerous-to-modify areas

- Don't hand-edit or commit `.vercel/project.json` — it links this
  checkout to the existing live Vercel project.
- Don't change the owner's real contact details (email/GitHub/
  LinkedIn/OpenReview) without being explicitly told to.
- The boot/hack intro script (`<script>` blocks at the end of
  `<body>`) is self-contained and takes no user input — if you touch
  it, keep it that way; don't wire it to anything external.

## Which commands should I run first?

```bash
cd ~/Projects/personal-website
git status                 # confirm this matches PROJECT_STATE.md — should be clean
git fetch origin && git log --oneline origin/main -3   # confirm no new remote commits
open index.html            # preview the page locally, no server/build needed
```

There is no `npm install`, no build, no lint, no test command.

## How do I verify the app still works?

Open `index.html` in a browser and walk `TESTING.md`'s manual
smoke-test checklist (boot animation plays and is skippable, rain
background renders, page loads, image/favicon render, nav anchors
work, external links are correct, responsive layout collapses
correctly below 560px).

---

## Prompt for the next Claude Code account

Copy-paste this to start a new session cleanly:

```
Read CLAUDE.md, PROJECT_STATE.md, and HANDOFF.md in full before doing
anything else.

1. Run `git status`, `git log --oneline -5`, and `git fetch origin`
   (read-only) and confirm the repo state matches what PROJECT_STATE.md
   describes. If it doesn't, stop and tell me what's different before
   proceeding.

2. IMPORTANT — before doing ANY feature work, content update beyond a
   trivial fix, or restructuring in this repo: this project has been
   flagged as possibly superseded by ~/Projects/gariyuu-web (a fuller
   Next.js site that already has landing + about/résumé + a chat demo +
   a dashboard). Ask me directly: "Do you want to keep actively
   developing personal-website, freeze it as-is, or delete it in favor
   of gariyuu-web?" Do not assume an answer either way — this repo also
   received real new commits very recently (the dark hacker-theme
   rework), so it is genuinely ambiguous, not an obvious "abandoned
   repo." Wait for my answer before investing non-trivial work here.

3. Read index.html in full (it's ~611 lines now, not the ~250 lines an
   older doc snapshot might suggest) rather than trusting FEATURES.md's
   summary, if you're about to edit content.

4. Do not add a framework, build step, backend, analytics, or any new
   dependency beyond what's already there (the Google Fonts webfont)
   unless I explicitly ask for it.

5. If I ask for a content update (new job, new project, etc.), edit
   index.html directly following the existing markup pattern for that
   section, then walk TESTING.md's manual smoke-test checklist before
   considering it done.

6. After any meaningful change, update PROJECT_STATE.md, CHANGELOG.md,
   and append to SESSION_LOG.md before ending your session.
```
