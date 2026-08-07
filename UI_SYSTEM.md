# UI_SYSTEM.md

All styling lives in a single inline `<style>` block inside
`index.html`'s `<head>`. There is no CSS framework, no CSS-in-JS, no
preprocessor (no Sass/Less), and no external stylesheet — except the
Google Fonts webfont stylesheet noted below.

**This file was rewritten 2026-08-07** to match the dark "hacker" theme
the site was reworked into that day (commit `9778732` onward). It
previously described a light theme with system fonts only — that
description is no longer accurate; see `DECISIONS.md` for the change
record.

## Design tokens

Declared once as CSS custom properties under `:root`:

```css
:root {
  --text: #d7f5df;     /* primary text color — pale green */
  --muted: #5f7a68;    /* secondary text — dates, subtitles, nav links */
  --line: #16241a;     /* border/divider color — dark green */
  --accent: #00ff8c;   /* primary accent — bright green */
  --accent-2: #00e5ff; /* secondary accent — cyan */
  --bg: #000000;       /* page background — pure black */
  --surface: #060a07;  /* slightly-raised surface (e.g. avatar empty state) */
  --maxw: 720px;        /* max content width, centered */
}
```

A few additional one-off colors are used inline rather than as tokens
(e.g. `#a9c9b2` for item-list/skills body text) — not promoted to
`:root` variables, presumably because they're used in only a couple of
places each.

## Typography

- **Font stack:** `"Share Tech Mono", ui-monospace, "SF Mono", Menlo,
  monospace` — a Google Fonts monospace webfont (loaded via
  `<link rel="preconnect">` + a `fonts.googleapis.com/css2` stylesheet
  in `<head>`) with system-monospace fallbacks if the webfont fails to
  load. This replaced the earlier system sans-serif stack
  (`"Helvetica Neue", -apple-system, ...`) as part of the 2026-08-07
  theme rework.
- **Base size/line-height:** `16px/1.7` on `body`, with `letter-spacing:
  .01em`.
- **Headings:** `.hero h1` is `2.1rem`, `letter-spacing: .04em`, with a
  green text-shadow glow. Section headings (`section h2`) are
  small-caps-style: `.82rem`, `text-transform: uppercase`,
  `letter-spacing: .2em`, colored `var(--accent)`, and prefixed with a
  `// ` comment-style marker via `::before`.
- **Antialiasing:** `-webkit-font-smoothing: antialiased;` on `body`.

## Layout

- Centered single column, `max-width: var(--maxw)` (720px), via `main`,
  `.nav-inner` both using `margin: 0 auto`.
- `header.hero` is a flex row (avatar + text block), wrapping on narrow
  screens (`flex-wrap: wrap`).
- Experience/Projects/Education entries (`.item`) use a 2-column CSS
  grid (`150px 1fr` — date column + content column).
- Skills use a flex-based label/value row pattern (`.skills .row`).
- A full-screen `<canvas id="rain">` sits behind everything
  (`position: fixed; inset: 0; z-index: 0; pointer-events: none;
  opacity: .4;`) rendering a continuous "digital rain" effect. Content
  (`main`, `nav`) sits above it at `z-index: 1`/`10`.
- A full-viewport `<div id="boot">` overlay (`z-index: 50`) covers the
  page on load, showing the boot/hack-intro animation; it's removed
  from the DOM once the sequence finishes or is skipped.

## Color usage

- Links (`a`) use `var(--accent)` (green), switching to `var(--accent-2)`
  (cyan) on hover, underlined on hover.
- Nav links default to `var(--muted)`, switch to `var(--accent)` on
  hover.
- Section dividers use 1px solid `var(--line)` borders (`border-top` on
  `section`, `nav`, `footer`).
- **Dark theme only.** No light mode, no `prefers-color-scheme` media
  query, no theme toggle of any kind — see `ROADMAP.md` for a
  light-mode toggle listed as a possible (unrequested) future idea.
- A pulsing green "status dot" (`.nav-inner .name .dot`) sits next to
  the name in the nav, animated via a `pulse` `@keyframes` rule.
- The boot overlay uses additional one-off colors for its phases:
  green/cyan for the normal boot text, white/gray "terminal window"
  panels for the fake "flood" phase, and a red flicker
  (`bootCrashFlicker` `@keyframes`) for the "crash" phase.

## Responsive behavior

Exactly one responsive breakpoint:

```css
@media (max-width: 560px) {
  .item { grid-template-columns: 1fr; }   /* date/content stack instead of side-by-side */
  header.hero { padding: 48px 0 36px; }    /* tighter vertical padding */
}
```

Additionally, `.nav-inner` uses `overflow-x: auto` so the nav links can
horizontally scroll on narrow viewports rather than wrapping/breaking
layout.

## Print styles

```css
@media print { nav { display: none; } canvas#rain { display: none; } }
```

The sticky nav and the rain canvas are hidden when the page is printed
(e.g. someone printing the resume to PDF) — everything else prints as
normal page flow. (The boot overlay removes itself from the DOM well
before a user would print, so it isn't a print-time concern.)

## Motion / animation

- `canvas#rain`: continuous animation via `requestAnimationFrame`,
  redrawn every 4th frame. Returns early (never starts) if
  `prefers-reduced-motion: reduce` is set.
- `#boot` sequence: a scripted, timed sequence of phases (boot text →
  flood of fake terminal windows with a screen-shake effect → red
  "crash" flicker → "reboot"/welcome text → fade out and DOM removal).
  If `prefers-reduced-motion: reduce` is set, the overlay is removed
  immediately instead of playing.
- A `pulse` `@keyframes` rule drives the small status dot in the nav
  and the boot cursor's blink.

## Icons

Hand-authored inline `<svg>` elements (GitHub, LinkedIn, OpenReview,
envelope/email glyphs) directly in the HTML — not an icon font, not an
icon component library. Styled via `.social svg { width: 20px; height:
20px; fill: currentColor; }` so their color follows the surrounding
link's color/hover state automatically.

## Accessibility notes

- Social icon links have `aria-label` and `title` attributes (e.g.
  `aria-label="GitHub"`) since the link content is an icon with no
  visible text.
- Both animated effects (`canvas#rain`, `#boot`) respect
  `prefers-reduced-motion: reduce` (see "Motion / animation" above) —
  this is a real accessibility accommodation, not just a performance
  optimization.
- The boot overlay is skippable via click or any keypress, so it
  doesn't trap a user who wants to reach the content immediately.
- No formal accessibility audit has been performed beyond the above.
  Semantic HTML (`<nav>`, `<header>`, `<section>`, `<footer>`) is used
  throughout, which provides reasonable baseline screen-reader
  structure, but this hasn't been independently tested with a screen
  reader or automated a11y tool. The boot overlay's text content isn't
  specifically announced to screen readers (no `aria-live` region) —
  worth revisiting if this repo's future is confirmed and accessibility
  becomes a priority.
