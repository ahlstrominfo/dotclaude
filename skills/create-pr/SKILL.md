---
name: create-pr
description: Create a GitHub pull request that matches the repo's existing PR style, tone, and conventions. Analyzes recent PRs and any PR template before writing. Use when user wants to open a PR, create a pull request, or submit their work for review.
---

# Create PR

Create a GitHub pull request that matches the repo's existing
conventions, tone, and style.

## Process

### 1. Understand the changes
Run these in parallel:
- `git log main...HEAD --oneline` to see all commits on this branch
- `git diff main...HEAD --stat` for a file-level summary
- `git diff main...HEAD` for the full diff
- Check if the branch tracks a remote and whether it needs pushing

If there are uncommitted changes, ask the user if they want to
commit first.

### 2. Check for a PR template
Look for a PR template in the repo. Check these locations:
- `.github/pull_request_template.md`
- `.github/PULL_REQUEST_TEMPLATE.md`
- `.github/PULL_REQUEST_TEMPLATE/` (directory with multiple templates)
- `docs/pull_request_template.md`

If a template exists, use it as the structure for the PR body.

### 3. Study recent PRs
Fetch the last 10 merged PRs:
```
gh pr list --state merged --limit 10 --json number,title,body,author
```

Analyze them for:
- **Title format** — conventional commits? ticket prefix? casing?
  length?
- **Body structure** — what sections do they use? bullet points or
  prose? how detailed?
- **Tone** — formal or casual? first person or third person?
  technical depth?
- **Linking conventions** — do they reference issues? how?
  "Closes #X", "Fixes #X", "Related to #X"?
- **Review hints** — do they include test instructions, screenshots,
  or deployment notes?

### 4. Draft the PR
Write a title and body that:
- Follows the template if one exists
- Matches the tone, structure, and conventions from recent PRs
- Accurately describes the changes in this branch
- Links to any related issues (check commit messages and branch
  name for issue numbers)

**Writing style: distill ruthlessly.** Every word must earn its place.
Cut filler, qualifiers, and anything the reviewer can see from the
diff. No "This PR...", no "In order to...", no restating the title
in the body. Lead with what changed and why. Bullet points over
prose. If a section adds no information beyond the diff, omit it.

Present the draft to the user for review. Show the title and body
clearly so they can request changes.

### 5. Create the PR
After the user approves:
- Push the branch if needed: `git push -u origin HEAD`
- Create the PR: `gh pr create --title "..." --body "..."`

Share the PR URL with the user.
