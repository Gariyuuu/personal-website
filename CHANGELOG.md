# CHANGELOG.md

Reconstructed from `git log` (all dates are actual commit dates — none
invented). No prior CHANGELOG.md existed before the 2026-08-06 audit.

## 2026-09-14 — Content synced to the owner's LinkedIn

On the owner's request ("just update the stuff with my linkedin"), résumé
content in `index.html` now matches LinkedIn (source: the LinkedIn archive at
gary-wang-archive.vercel.app, cross-checked against LinkedIn's own profile
export PDF and the Sep 11 page print). Rule: LinkedIn wins wherever it states
something; site content LinkedIn doesn't contradict is kept. Changes: hero
headline is LinkedIn's ("stats, econ & ds @ ucb · San Francisco Bay Area");
About rewritten around current roles; Experience expanded from 5 to all 22
LinkedIn entries with LinkedIn titles/dates (Accio → Full Stack Engineer
Jun–Aug 2026; Alibaba Group → Business Analyst; new Alibaba Cloud ML
Researcher; LTC → Undergraduate Research Assistant Oct 2025–Sep 2026 plus
Undergraduate Student Researcher Sep 2026–Present; UCR → Undergraduate
Researcher; MP Biomedicals → Data Analyst Jul–Aug 2024 plus Software Engineer
Jul–Aug 2023; new UC Berkeley URAP, Data Science Discovery Program, Rapid
Reviews\Infectious Diseases, CSUSB, Figwork, EBI, Mathnasium, LanguageConnect,
ForeignLanguagePro, Kaggle, Cal Poly Pomona, IEEE Conference, Center for
Compassionate Leadership, George Mason). Education is LinkedIn's 4 entries
(3 UC Berkeley bachelor's — Statistics, Data Science, Economics, Aug 2025–May
2029 — plus St. Margaret's Episcopal School 2021–2025 with SAT 1590). Skills
gained LinkedIn's LLMOps/NLP/LLMs/RLHF/Systems Engineering/Data Cleaning/
Product Analytics; Languages now Chinese + English (native or bilingual),
Japanese (limited working). Honors now include the publication, IEEE '26 and
3x Presidential Service Gold Medalist. Profile photo replaced with the
LinkedIn headshot as `photo-2026-09.jpg` (new filename to dodge caches; old
`photo.jpeg` left in the repo, unreferenced). Contact email unchanged
(gary_wang@berkeley.edu). No theme/JS changes.

## 2026-09-14 — Slower glitch, static on hover, grey-shaded rain

Hero-name glitch slowed to a 4.8s loop with its own slightly different palette
(pale blue-white, rose / sky channels). Any text under a mouse or pen pointer
now gets the static glitch (pure red / white / blue, 3.2s loop; off for touch
and reduced motion). Matrix rain kept at its original strength and now shaded
white → grey → dark grey along each trail. Matches gariyuuu.com.

## 2026-09-14 — RGB static glitch on the hero name

"Gary Wang" in the hero is wrapped in `.glitch`: white text with a red/blue
channel split that hard-cuts to red or blue while sliced red/blue copies jump
sideways (steps(1), 2.4s loop, under 3 flashes/s). Sits inside the existing
`fx-crt` h1, so the CRT flicker and scanlines still apply. Reduced motion keeps
only the still RGB split. Matches gariyuuu.com's hero highlight.

## 2026-09-14 — Monochrome palette, nonchalant boot intro

On the owner's request ("just black, not green"; loading page "way more
nonchalant", same effects, no changes to the transition or animation):
palette is now black / white / greys only — tokens, avatar and hero/welcome
glows, `#a9c9b2` body greys, crash flicker (red → dark greys). Boot intro
copy rewritten lowercase and deadpan ("loading. take your time.", "welp.",
"oh. hey."), skip hint now "click anywhere if you're bored". Every phase
array kept its length, so all timings, keyframes and transitions are
unchanged. Verified locally in Playwright across boot / flood / crash /
recover / page, zero console errors.

## 2026-09-02 — Content update from the September 2026 resume

Updated `index.html` résumé content to match the owner's updated resume
(Gary_Wang_Resume.SEP.pdf), on the owner's explicit request. Changes:
new hero headline + About; Experience gained Accio Work (Full-Stack
Engineer Intern, Jun 2026–Present) and got corrected titles/end dates
for Alibaba (Business Analyst Intern, ended Aug 2026), UC Riverside
(Undergraduate Researcher in ML, ended Jun 2026), Leonard
Transportation Center (ended Jun 2026), and MP Biomedicals (Full-Stack
Developer Intern, May–Aug **2024**, was wrongly 2023); Projects now
lists Independent AI Web-app & App Development (40+ products) and the
Language Learning App & Research Paper (dates corrected to Aug 2024–
May 2025, 10+ journals), dropping the Job Salary Prediction project
(no longer on the resume); Education coursework updated to the resume's
list; Skills expanded to six rows (adds TypeScript/JavaScript/Swift,
Web Dev and Data & Cloud rows, DevOps row); Honors reworded to resume
phrasing; **contact email changed from gywng006@gmail.com to
gary_wang@berkeley.edu** (the resume's listed email) in all three
places; meta/OG/Twitter descriptions updated. No theme/JS changes.

## 2026-08-07 — Documentation refresh + supersession flag

Verified the 16-file doc set against the actual repo (which had
drifted significantly — see the entries below), corrected stale claims,
added the missing `README.md`, and flagged this repo as possibly
superseded by `~/Projects/gariyuu-web` pending the owner's decision. No
application code changed. See `SESSION_LOG.md` for full detail.

## 2026-08-07 — Make the hacker-log flood fill the whole screen with a shake

Commit `813e215`. Expanded the "flood" phase of the boot/hack intro
animation to fill the full screen and added a shake effect.

## 2026-08-07 — Turn the hacker-log flood into scattered black-and-white terminal windows

Commit `88b465d`. Changed the flood-phase visual from a single log
stream into multiple scattered, rotated terminal-window panels.

## 2026-08-07 — Slow the rain, extend the boot sequence, add a hacked red screen

Commit `c324c71`. Slowed the canvas rain animation, lengthened the
boot-sequence text, and added a red "crash"/compromised screen phase to
the intro sequence.

## 2026-08-07 — Add terminal boot-up intro animation

Commit `eff4591`. Added the first version of the skippable JS
terminal boot sequence that plays before the résumé content is shown.

## 2026-08-07 — Rework site into a dark hacker theme, add OpenReview link

Commit `9778732`. Replaced the light-theme design tokens with a dark,
near-black "hacker" palette (green/cyan accents), switched the font
stack to the `Share Tech Mono` Google Fonts webfont, added a canvas
"digital rain" background effect, and added an OpenReview link to the
social icons and Contact section.

## 2026-08-06 — Documentation handoff (previous audit)

Added a full 16-file documentation system (`CLAUDE.md`,
`PROJECT_STATE.md`, `ARCHITECTURE.md`, `FILE_MAP.md`, `FEATURES.md`,
`TASKS.md`, `ROADMAP.md`, `DECISIONS.md`, `DATABASE.md`,
`API_REFERENCE.md`, `UI_SYSTEM.md`, `SECURITY.md`, `TESTING.md`,
`DEPLOYMENT.md`, `CHANGELOG.md`, `SESSION_LOG.md`, `HANDOFF.md`) by
directly auditing the repo. Committed as `b27b9c9`.

## 2026-08-06 — Add favicon

Commit `f344976`. Added an inline SVG favicon (`data:image/svg+xml,...`
data URI, blue rounded square with "GW") so the site shows an icon in
the browser tab. One line added to `index.html`'s `<head>`; no new
files.

## 2026-08-03 — Ignore .DS_Store

Commit `aa8b157`. Added `.DS_Store` to `.gitignore` (repo hygiene, no
content change).

## 2026-07-27 — Update profile photo

Commit `bc9786d`. Replaced `photo.jpeg` with a new profile photo
(19,187 bytes → 31,967 bytes). No `index.html` changes.

## 2026-07-25 — Update resume content, drop GPA, add GitHub link

Commit `2d4d662`. Refreshed Experience/Projects/Skills/Honors content
to match an updated resume; removed GPA from the Education section;
added a GitHub link alongside LinkedIn and email in both the header
social icons and the Contact section; updated the contact email
address. 40 insertions, 30 deletions across `index.html`.

## 2026-07-24 — Initial commit

Commit `9869c4a`. First version of the site: `.gitignore`,
`index.html` (234 lines — full page structure, nav, hero, all content
sections, styling), and `photo.jpeg`.
