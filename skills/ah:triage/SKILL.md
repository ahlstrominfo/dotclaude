---
name: triage-issues
description: Review the dependency graph of work items from a PRD, update their blocked/ready status, and recommend which item to work on next. Use when user wants to triage issues, check what's unblocked, update item status, or find the next thing to work on.
---

# Triage Work Items

Walk the dependency graph of work items spawned from a PRD, reconcile
their status against reality, and recommend what to work on next.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

### 1. Gather the work items
Ask the user for the parent PRD identifier (issue number, ticket key,
or local plan directory). Fetch the PRD using the tracker instructions.

Fetch all child items of the PRD using the tracker instructions.

### 2. Fetch dependency status
For each child item, fetch it and parse its "Blocked by" section.
Check whether each blocker is resolved.

Classify every item into one of:
- **Done** — item is closed/completed
- **In Progress** — item is open and actively being worked on
- **Ready** — item is open and all blockers are resolved (or has no
  blockers)
- **Blocked** — item is open and at least one blocker is still unresolved

### 3. Present the status overview
Display a table or grouped list:

```
Done:
  - Set up database schema

Ready (can start now):
  - Add API endpoint for widget creation
    (was blocked by schema setup, now resolved)

In Progress:
  - Auth middleware refactor

Blocked:
  - Frontend widget form
    blocked by auth refactor (still open), API endpoint (still open)
```

Call out any items whose status has changed since they were last
updated.

### 4. Update status
Propose status changes to reflect current reality:
- Mark newly unblocked items as `ready`
- Mark items with open blockers as `blocked`

Ask the user to confirm before applying. Apply using the tracker
instructions.

### 5. Recommend next item
Suggest which ready item to pick up next, considering:
- Dependency order — prefer items that unblock the most other work
- Slice type — prefer AFK slices the user can hand off to Claude
- Complexity — if multiple are equivalent, suggest the simplest first

Ask the user if they want to jump straight into `/ah:work-issue` with
the recommended item.
