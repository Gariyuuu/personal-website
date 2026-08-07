# TESTING.md

**No automated tests exist, and none are recommended at this scope.**
There is no logic to unit-test, no components to snapshot-test, and no
backend to integration-test — the entire site is static markup. Manual
verification is the appropriate (and sufficient) way to confirm changes
here.

## Manual smoke-test checklist

Run this after any content or markup change to `index.html`:

1. **Page loads.** Open `index.html` directly in a browser (`open
   index.html`) or via a local server (`python3 -m http.server 8000`).
   Confirm the page renders with no visible errors.
2. **Image renders.** Confirm the circular avatar photo shows
   `photo.jpeg` correctly (not a broken-image icon) — this depends on
   `photo.jpeg` existing at the repo root alongside `index.html`.
3. **Favicon renders.** Confirm the browser tab shows the icon from
   `favicon.ico` (a real committed file, not an inline `data:` URI).
4. **Boot/hack intro plays and is skippable.** Reload the page and
   confirm the terminal boot animation plays (boot text → flood of
   fake terminal windows → red "crash" screen → "reboot"/welcome →
   fades out into the résumé). Confirm clicking anywhere or pressing
   any key skips straight to the résumé. Confirm it doesn't play again
   on an in-page anchor click, only on a fresh page load.
5. **Canvas rain renders.** Confirm the full-screen "digital rain"
   background animates behind the content and doesn't block clicks on
   any link (it's `pointer-events: none`).
6. **`prefers-reduced-motion` respected.** With the OS/browser
   "reduce motion" setting on, confirm the boot intro is skipped
   entirely (page shows the résumé immediately) and the rain canvas
   doesn't animate.
7. **Nav anchors work.** Click every nav link (About, Experience,
   Projects, Education, Skills, Honors, Contact) and confirm the page
   smooth-scrolls to the matching section — no dead/mismatched anchors.
8. **External links resolve.** Confirm the GitHub, LinkedIn, OpenReview,
   and email icons/links (hero + Contact section) all point to the
   correct, live destinations. (A full live-HTTP check of these URLs is
   optional — visually confirming the `href` values match the intended
   destinations is normally sufficient.)
9. **Responsive check.** Resize the browser (or use dev tools' device
   toolbar) below ~560px width and confirm the Experience/Projects/
   Education entries stack into a single column instead of the
   date/content grid, and that the nav row scrolls horizontally instead
   of breaking.
10. **Print check (optional).** Use the browser's print preview and
    confirm the sticky nav and rain canvas are hidden (per the
    `@media print` rule).
11. **No console errors.** Open browser dev tools' console — should be
    empty. (There are now two small `<script>` blocks, so this check
    actually matters — confirm neither throws, and that this also
    catches things like a missing/404'd `photo.jpeg`/`favicon.ico`.)

## What this checklist does NOT cover

- Cross-browser/cross-device testing beyond whatever browser is used
  locally — not currently done, and probably unnecessary given the
  page uses only well-supported, basic CSS/HTML features.
- Accessibility testing with an actual screen reader — see
  `UI_SYSTEM.md`'s accessibility notes; semantic HTML is used, but this
  hasn't been independently verified.
- Live production verification (checking the actual deployed Vercel
  URL) — see `DEPLOYMENT.md`; the production URL itself is currently
  unrecorded in this repo.
