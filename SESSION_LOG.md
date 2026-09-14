# SESSION_LOG.md

Append-only log of work sessions on this repo. Never overwrite prior
entries — add a new dated entry at the bottom.

---

## 2026-08-06 — Documentation system build (from-scratch handoff audit)

**Agent:** Claude Code (Sonnet 5)

**What was requested:** Build a full 17-file handoff-documentation
system from scratch for this repo (which had zero documentation files
before this session), to the same structural standard as sibling
projects `chamber-seven` and `buildstrike-arena` — format/section
headings as reference only, all actual content sourced from directly
auditing this repo.

**What was done:**

1. Fully inspected the repo: read all 246 lines of `index.html`,
   confirmed `photo.jpeg`'s format/dimensions (400×400 JPEG), read
   `.gitignore`, read `.vercel/project.json` (gitignored, local-only —
   confirms link to Vercel project `personal-website`), and reviewed
   the complete git history (5 commits, `main` branch, tracking
   `origin/main`, clean working tree).
2. Searched `index.html` for TODO/FIXME/placeholder/lorem-ipsum text
   and checked every `href=`/`url()` reference — found none of the
   former, all of the latter resolve correctly (in-page anchors, real
   external URLs, or a file that exists in the repo).
3. Reviewed `chamber-seven`'s and `buildstrike-arena`'s
   `CLAUDE.md`/`PROJECT_STATE.md`/`HANDOFF.md` purely for section
   structure/format — no content copied; everything written here comes
   from this repo's own files.
4. Created all 17 requested files: `CLAUDE.md`, `PROJECT_STATE.md`,
   `ARCHITECTURE.md`, `FILE_MAP.md`, `FEATURES.md`, `TASKS.md`,
   `ROADMAP.md`, `DECISIONS.md`, `DATABASE.md`, `API_REFERENCE.md`,
   `UI_SYSTEM.md`, `SECURITY.md`, `TESTING.md`, `DEPLOYMENT.md`,
   `CHANGELOG.md`, `SESSION_LOG.md` (this file), `HANDOFF.md`.
5. Deliberately kept every file short and scoped to this project's
   actual size — most of `DATABASE.md`/`API_REFERENCE.md` are "does not
   apply" statements rather than padded/invented structure.
6. Ran a final account-switch checkpoint pass: re-ran `git
   status`/`git log` to confirm nothing changed mid-session, verified
   `PROJECT_STATE.md`/`TASKS.md`/`HANDOFF.md` describe the same current
   state consistently, and confirmed no secrets/tokens/keys were
   written into any file.

**What was NOT done (explicitly out of scope per the task):** no code
was changed, nothing was committed, nothing was pushed, nothing was
deployed. `.vercel`/Vercel dashboard settings were not queried live
(would require CLI auth / network access beyond a read-only local
audit) — the exact auto-deploy behavior and production URL remain
**Unverified**, flagged clearly in `DEPLOYMENT.md` and
`PROJECT_STATE.md` rather than guessed at.

**State at end of session:** Working tree has 17 new untracked files
(this documentation set) and is otherwise clean — no other changes.
`main` branch, HEAD at `f344976` (unchanged from session start).

---

## 2026-08-07 — Documentation refresh, supersession flag, README

**Agent:** Claude Code (Sonnet 5)

**What was requested:** Verify the existing 16-file doc set (from the
2026-08-06 audit) against the actual current repo, add the missing
17th file (`README.md`), and prominently flag that this repo was
identified in a separate cross-repo inventory audit as **possibly
superseded by `~/Projects/gariyuu-web`** and listed as "a candidate to
delete" — surfacing that clearly and consistently so a future session
doesn't invest work here without knowing the context, without deleting
anything.

**What was found:** The repo had drifted substantially since the
2026-08-06 baseline. Between that audit and this session, 6 new
commits (`b27b9c9` docs commit aside, then `9778732`, `eff4591`,
`c324c71`, `88b465d`, `813e215`) reworked the site from a plain
light-theme static page into a dark "hacker" theme: a canvas rain
background effect, a skippable JS terminal boot/hack intro sequence, a
Google Fonts webfont (`Share Tech Mono`), a real `favicon.ico` file
(replacing the inline SVG favicon the docs described), and a new
OpenReview social link. This meant several of the existing docs'
factual claims — "no JavaScript anywhere," "light theme only," "system
font stack, no Google Fonts," "inline SVG favicon, no separate file" —
were no longer true. (Note: several of these commits landed *during*
this very session, indicating another account/session was actively
working on the site concurrently — re-fetched and re-read `index.html`
before finalizing anything below to avoid documenting a stale state.)

**What was done:**

1. Re-read `index.html` in full (611 lines, up from ~250) and diffed
   its actual behavior/markup against every claim in the 16 existing
   docs.
2. Ran `git status`, `git log --oneline`, and `git fetch origin`
   (read-only) — confirmed working tree clean, HEAD `813e215`, up to
   date with `origin/main`, 11 commits total.
3. Scanned all tracked files (`git grep` for key/token/secret-like
   patterns) — found no real secrets. The only "sensitive-looking"
   values are the Vercel `projectId`/`orgId` quoted in `DEPLOYMENT.md`
   (sourced from the gitignored `.vercel/project.json`) — these are
   project identifiers, not auth credentials, so not treated as a
   secret leak, but noted as a minor thing worth being aware of since
   they're now in a public doc file.
4. Corrected the stale technical claims in `CLAUDE.md`, `ARCHITECTURE.md`,
   `FEATURES.md`, `SECURITY.md`, `DATABASE.md`, `TESTING.md`,
   `DECISIONS.md`, `FILE_MAP.md`, `ROADMAP.md`, and `UI_SYSTEM.md` to
   match the dark-theme/JS reality, and added the missing commit
   history to `CHANGELOG.md`.
5. Wrote `README.md` (the 17th canonical file, previously missing) with
   a prominent supersession banner.
6. Rewrote `PROJECT_STATE.md` and `TASKS.md` to reflect true current
   git/repo state and to state the supersession flag clearly and
   consistently.
7. Rewrote `HANDOFF.md` with the supersession warning up top and a
   refreshed "Prompt for the next Claude Code account" section that
   explicitly tells a fresh session to check with the owner on the
   supersession/deletion question before doing feature work.
8. Did not delete anything, did not touch `index.html`/`photo.jpeg`/
   `favicon.ico`, did not push.

**State at end of session:** Documentation set is now 17/17 files, all
internally consistent and matching the actual repo state. `main`
branch, HEAD `813e215`, working tree clean before this session's doc
commit. See `git log` for the exact commit this session produced.

## 2026-08-17 — Documentation sweep (onboard mode, no feature work)

- **Trigger:** Batch documentation-freshness sweep across several
  portfolio repos, not tied to a specific new-work request in this
  repo.
- **Findings:** Significant drift, including a real gap — two feature
  commits (`e5b5a58`/`ac22770`, 2026-08-07) had landed **after** the
  prior doc refresh (`b5dcff8`, same day) and were never documented at
  all: 8 cascading fake OS error/popup-spam dialogs during the boot
  flood, and a rain speed-easing effect (`window.__rainFast`). Also
  undocumented: OG/Twitter meta tags (`7dd923c`/`b344e6c`, 2026-08-13/14)
  and a CRT/phosphor flicker on the hero name (`4c11b1f`/`3747f05`,
  2026-08-15/17, adapted from a credited third-party MIT source).
  `index.html` grew from 611 to 687 lines. All feature branches
  (`chore/metadata-og`, `chore/polish`) are fully merged into `main`.
- **Verification performed:** Live-`curl`'d
  `https://personal-website-delta-plum.vercel.app/` (200) and
  `/photo.jpeg` (200, matches the new `og:image` URL). Read the actual
  popup/rain/CRT code in `index.html` directly rather than trusting
  commit messages alone.
- **Work completed:** Updated `PROJECT_STATE.md`, `TASKS.md`,
  `HANDOFF.md`, `CLAUDE.md`, `FEATURES.md`, `UI_SYSTEM.md`, `FILE_MAP.md`
  to document all of the above. Reframed `TASKS.md`'s current task as
  `T-001` = the still-unresolved supersession question (was previously
  described as "none," which didn't satisfy this doc system's
  current-task-consistency requirement and also undersold that the
  supersession question is a real standing blocker). **Did not**
  resolve or attempt to resolve the supersession question itself — that
  remains for the owner. Did not touch `index.html`/`photo.jpeg`/
  `favicon.ico`. `python3 verify_docs.py --root .` — all checks pass.
  No secrets found.
- **Work remaining:** `T-001` (ask the owner about supersession).
  Everything else carried over unchanged from prior entries.
- **Recommended next action:** Ask the owner the supersession question
  before any further feature work here.

## 2026-09-02 — Resume content update (feature/content work)

- **Trigger:** Owner explicitly asked to update the live site with
  their updated resume (Gary_Wang_Resume.SEP.pdf) and LinkedIn URL.
  The LinkedIn URL provided matched what was already on the site
  (`gary-wang-a912a0308`) — no change needed there. The owner's
  explicit request resolves the T-001 "invest here?" hesitation for
  content updates (supersession as a repo-lifecycle question remains
  formally open).
- **Work completed:** `index.html` content updated end to end — see
  CHANGELOG.md 2026-09-02 entry for the full delta (new Accio Work
  role, corrected titles/dates for the four prior roles, new
  Independent AI Development project entry, salary-prediction project
  dropped, coursework/skills/honors refreshed, contact email changed
  to gary_wang@berkeley.edu per the resume, meta descriptions updated).
- **Not changed:** theme, boot/rain/CRT scripts, design-system
  include, photo, favicon, GitHub/LinkedIn/OpenReview links.
- **Verification:** grepped that no stale strings remain
  (gywng006, "May 2023", Salary Prediction, OIDD); item count is 8
  (5 experience + 2 projects + 1 education). Committed and pushed;
  live deployment verified per the terminal session record.

## 2026-09-14 — Monochrome palette + nonchalant boot copy

- **Trigger:** owner asked for this site and gariyuuu.com to go "just black,
  not green" with a far more nonchalant loading page, same effects, no
  changes to transitions/animation.
- **Work completed:** see CHANGELOG 2026-09-14. Only colour values and
  strings changed in `index.html`; no JS logic, timing or keyframe edits.
- **Verification:** served on a free local port, title-checked, Playwright
  captures of all five phases; no green left (`grep` for 00ff8c /
  0,255,140 / green returns nothing in `index.html`).
