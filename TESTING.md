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
3. **Favicon renders.** Confirm the browser tab shows the blue "GW"
   icon (inline SVG `data:` URI, no separate file needed).
4. **Nav anchors work.** Click every nav link (About, Experience,
   Projects, Education, Skills, Honors, Contact) and confirm the page
   smooth-scrolls to the matching section — no dead/mismatched anchors.
5. **External links resolve.** Confirm the GitHub icon, LinkedIn icon,
   email icon (in the hero) and the GitHub/LinkedIn/email links (in the
   Contact section) all point to the correct, live destinations. (A
   full live-HTTP check of these URLs is optional — visually confirming
   the `href` values match the intended destinations is normally
   sufficient.)
6. **Responsive check.** Resize the browser (or use dev tools' device
   toolbar) below ~560px width and confirm the Experience/Projects/
   Education entries stack into a single column instead of the
   date/content grid, and that the nav row scrolls horizontally instead
   of breaking.
7. **Print check (optional).** Use the browser's print preview and
   confirm the sticky nav is hidden (per the `@media print` rule).
8. **No console errors.** Open browser dev tools' console — should be
   empty (there's no JavaScript to throw errors, but this also catches
   things like a missing/404'd `photo.jpeg`).

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
