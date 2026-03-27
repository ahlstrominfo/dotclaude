---
name: ah:create-pr
description: Create a GitHub pull request that matches the repo's existing PR style, tone, and conventions. Analyzes recent PRs and any PR template before writing. Use when user wants to open a PR, create a pull request, or submit their work for review.
---

Create a GitHub PR that matches the repo's existing conventions.

1. Understand the changes on this branch (commits, diff, uncommitted work).
2. Check for a PR template in the repo.
3. Fetch the last 10 merged PRs and match their title format, body
   structure, tone, and linking conventions.
4. Draft the PR. **Distill ruthlessly** — cut filler, don't restate
   the title, omit sections that add nothing beyond the diff. Show
   draft to user before creating.
5. Push and create the PR after user approves.
