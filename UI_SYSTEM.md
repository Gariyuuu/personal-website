# UI_SYSTEM.md

All styling lives in a single inline `<style>` block inside
`index.html`'s `<head>` (lines ~9-85 of the file). There is no
CSS framework, no CSS-in-JS, no preprocessor (no Sass/Less), and no
external stylesheet.

## Design tokens

Declared once as CSS custom properties under `:root`:

```css
:root {
  --text: #1a1a1a;    /* primary text color */
  --muted: #666a70;   /* secondary text — dates, subtitles, nav links */
  --line: #e8e8e8;    /* border/divider color */
  --accent: #1d4ed8;  /* link/accent blue */
  --bg: #ffffff;      /* page background */
  --maxw: 720px;       /* max content width, centered */
}
```

A few additional one-off colors are used inline rather than as tokens
(e.g. `#3a3f45` for item list/skills body text, `#f0f1f3` for the
avatar's empty-state background) — not promoted to `:root` variables,
presumably because they're used in only one or two places each.

## Typography

- **Font stack:** `"Helvetica Neue", -apple-system, BlinkMacSystemFont,
  "Segoe UI", Arial, sans-serif` — system fonts only, no web font
  loading (no `@font-face`, no Google Fonts `<link>`, no `next/font`).
- **Base size/line-height:** `17px/1.7` on `body`.
- **Headings:** `.hero h1` is `2.3rem`, `letter-spacing: -.02em`.
  Section headings (`section h2`) are small-caps-style: `.85rem`,
  `text-transform: uppercase`, `letter-spacing: .12em`, colored
  `var(--muted)` rather than large/bold.
- **Antialiasing:** `-webkit-font-smoothing: antialiased;` on `body`.

## Layout

- Centered single column, `max-width: var(--maxw)` (720px), via `main`,
  `.nav-inner` both using `margin: 0 auto`.
- `header.hero` is a flex row (avatar + text block), wrapping on narrow
  screens (`flex-wrap: wrap`).
- Experience/Projects/Education entries (`.item`) use a 2-column CSS
  grid (`150px 1fr` — date column + content column).
- Skills use a flex-based label/value row pattern (`.skills .row`).

## Color usage

- Links (`a`) use `var(--accent)` (blue `#1d4ed8`), underline only on
  hover.
- Nav links default to `var(--muted)` (gray), darken to `var(--text)`
  on hover — a deliberately subtler treatment than body links.
- Section dividers use 1px solid `var(--line)` borders (`border-top` on
  `section`, `nav`, `footer`).
- **Light theme only.** No dark mode, no `prefers-color-scheme` media
  query, no theme toggle of any kind.

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
@media print { nav { display: none; } }
```

The sticky nav is hidden when the page is printed (e.g. someone
printing the resume to PDF) — everything else prints as normal page
flow.

## Icons

Hand-authored inline `<svg>` elements (GitHub, LinkedIn, envelope/email
glyphs) directly in the HTML — not an icon font, not an icon component
library, not `lucide-react` or similar. Styled via `.social svg { width:
22px; height: 22px; fill: currentColor; }` so their color follows the
surrounding link's color/hover state automatically.

## Accessibility notes

- Social icon links have `aria-label` and `title` attributes (e.g.
  `aria-label="GitHub"`) since the link content is an icon with no
  visible text.
- No formal accessibility audit has been performed. Semantic HTML
  (`<nav>`, `<header>`, `<section>`, `<footer>`) is used throughout,
  which provides reasonable baseline screen-reader structure, but this
  hasn't been independently tested with a screen reader or automated
  a11y tool.
