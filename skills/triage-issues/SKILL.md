---
name: triage-issues
description: Review the dependency graph of issues from a PRD, update their blocked/ready status, and recommend which issue to work on next. Use when user wants to triage issues, check what's unblocked, update issue status, or find the next thing to work on.
---

# Triage Issues

Walk the dependency graph of issues spawned from a PRD, reconcile
their status against reality, and recommend what to work on next.

## Process

### 1. Gather the issues
Ask the user for the parent PRD issue number (or a milestone/label
to filter by). Fetch the PRD with `gh issue view <number>`.

Fetch sub-issues of the PRD using the GraphQL API:
```
gh api graphql -f query='query {
  repository(owner: "<owner>", name: "<repo>") {
    issue(number: <prd-number>) {
      subIssues(first: 100) {
        nodes { number title state labels(first: 10) { nodes { name } } }
      }
    }
  }
}'
```

### 2. Fetch dependency status
For each child issue, fetch it with `gh issue view <number>` and
parse its "Blocked by" section. Check whether each blocker is open
or closed.

Classify every issue into one of:
- **Done** — issue is closed
- **In Progress** — issue is open and has an `in-progress` label or
  an associated open PR
- **Ready** — issue is open and all blockers are closed (or has no
  blockers)
- **Blocked** — issue is open and at least one blocker is still open

### 3. Present the status overview
Display a table or grouped list:

```
Done:
  - #12 Set up database schema ✓

Ready (can start now):
  - #14 Add API endpoint for widget creation
    (was blocked by #12, now resolved)

In Progress:
  - #13 Auth middleware refactor

Blocked:
  - #15 Frontend widget form
    blocked by #13 (still open), #14 (still open)
```

Call out any issues whose status has changed since they were last
updated (e.g. a blocker closed but the issue still has a `blocked`
label).

### 4. Update labels
Propose label changes to reflect current reality:
- Add `ready` and remove `blocked` for newly unblocked issues
- Add `blocked` for issues with open blockers that aren't labeled

Ask the user to confirm before applying. Apply with:
```
gh issue edit <number> --add-label <label> --remove-label <label>
```

### 5. Recommend next issue
Suggest which ready issue to pick up next, considering:
- Dependency order — prefer issues that unblock the most other work
- Slice type — prefer AFK slices the user can hand off to Claude
- Complexity — if multiple are equivalent, suggest the simplest first

Ask the user if they want to jump straight into `/work-issue` with
the recommended issue.
