# DEPLOYMENT.md

## Hosting

**Vercel.** Confirmed via `.vercel/project.json` (gitignored,
local-only file, not committed to git):

```json
{"projectId":"prj_H8PE0dzDhR5rA64uqqXrRA0ndVNW","orgId":"team_gofGt63nGGecSpDl9hBbsFWm","projectName":"personal-website"}
```

This proves the local checkout is linked to a Vercel project named
`personal-website` under a specific Vercel team/org. It does not, by
itself, prove anything about *how* deploys are triggered — that's a
Vercel-dashboard-level project setting, not something stored in this
repo's files.

## No `vercel.json`

There is no `vercel.json` in the repo. Since the site is a single
static HTML file with no build step, Vercel's zero-config static-file
detection is sufficient — no custom build command, output directory,
redirects, or headers are configured anywhere.

## How deploys are triggered

**Unverified from within this repo** — could not be confirmed without
querying Vercel directly (out of scope for this non-destructive,
read-only audit; explicitly no deploys were run as part of this
documentation task). Two possibilities, both standard for a
Vercel-linked GitHub repo:

1. **Git-based auto-deploy (most likely default):** Vercel's GitHub
   integration watches `origin/main` and deploys automatically on every
   push, once the Vercel project has been connected to the
   `Gariyuuu/personal-website` GitHub repo via the Vercel dashboard.
   This is Vercel's standard default behavior for GitHub-connected
   projects.
2. **Manual CLI deploy:**
   ```bash
   npx vercel deploy --prod
   ```
   Requires the Vercel CLI to be installed and authenticated
   (`vercel login`) and the directory linked (`.vercel/project.json`
   already exists, so `vercel link` has been done previously).

**To confirm which applies:** check the Vercel dashboard for this
project's "Git" settings, or run `vercel ls`/`vercel inspect
personal-website` with an authenticated CLI. This was not done during
this audit to keep the pass strictly read-only/non-destructive per the
task's instructions — flagged here as the one open item for whoever
needs to actually ship a change.

## Production URL / domain

**Not recorded anywhere in this repo.** No custom domain is referenced
in any tracked file, and Vercel's default project URL (typically something
like `personal-website-<hash>.vercel.app` or `personal-website.vercel.app`)
is not written down anywhere either. Confirm via the Vercel dashboard.

## Rollback

No special rollback tooling exists in this repo. If a bad deploy goes
out, the standard Vercel approach applies: redeploy a previous commit
(via `git revert` + push, if auto-deploy is confirmed active, or `vercel
rollback` / re-running `vercel deploy --prod` against an earlier commit
via the CLI).

## CI/CD

None. No `.github/workflows/` directory, no other CI config exists in
this repo (confirmed by directory listing during this audit). There is
no automated lint/test/build gate before deploy — deploys go out
directly from whatever is in `main` (or whatever a manual `vercel
deploy --prod` picks up from the local working tree).
