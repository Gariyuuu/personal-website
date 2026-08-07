# API_REFERENCE.md

**There are no API routes.**

This project has no backend of any kind — no Next.js API routes, no
Express server, no serverless/edge functions, no GraphQL endpoint. It
is two static files (`index.html`, `photo.jpeg`) served directly by
Vercel's static hosting.

There are no outbound calls to third-party *APIs* either — every `href`
in `index.html` is either an in-page anchor (`#about`, etc.), a static
external profile link (GitHub, LinkedIn, OpenReview), or a `mailto:`
link. None of these are programmatic API calls; they're plain
navigation links a browser follows directly.

One real (non-API) third-party network request does exist as of
2026-08-07: `index.html`'s `<head>` loads the `Share Tech Mono` webfont
from `fonts.googleapis.com`/`fonts.gstatic.com` (see `ARCHITECTURE.md`,
`SECURITY.md`, `UI_SYSTEM.md`). This is a static font/CSS asset fetch,
not a programmatic API call with request/response data — noted here for
completeness since it's the one outbound network dependency this page
now has.

If backend functionality is ever added (e.g. a contact-form submission
handler), document the new endpoint(s) here at that time, including
method, request/response shape, and auth (if any).
