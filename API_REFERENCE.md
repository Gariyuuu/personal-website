# API_REFERENCE.md

**There are no API routes.**

This project has no backend of any kind — no Next.js API routes, no
Express server, no serverless/edge functions, no GraphQL endpoint. It
is two static files (`index.html`, `photo.jpeg`) served directly by
Vercel's static hosting.

There are no outbound calls to third-party APIs either — every `href`
in `index.html` is either an in-page anchor (`#about`, etc.), a static
external profile link (GitHub, LinkedIn), or a `mailto:` link. None of
these are programmatic API calls; they're plain navigation links a
browser follows directly.

If backend functionality is ever added (e.g. a contact-form submission
handler), document the new endpoint(s) here at that time, including
method, request/response shape, and auth (if any).
