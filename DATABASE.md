# DATABASE.md

**There is no database.**

This project is a single static HTML file with no server-side logic.
There is no relational database, no document store, no key-value
store, no ORM, no schema, no migrations, and no persistence layer of
any kind — client-side or server-side.

Nothing in `index.html` reads or writes any data beyond what's
hardcoded directly in the markup. No `localStorage`/`sessionStorage`/
cookies are used. `index.html` does contain a small amount of inline
JavaScript (a canvas rain effect and a boot-intro animation, added
2026-08-07 — see `ARCHITECTURE.md`/`FEATURES.md`), but neither reads
nor persists any data anywhere; they're purely visual/animation logic
with no storage APIs used.

If this project ever needs to store data (e.g. a contact form, a guest
book, analytics), that would be a significant scope change from "static
resume page" and should be recorded as a new decision in `DECISIONS.md`
at the time, along with a real write-up in this file.
