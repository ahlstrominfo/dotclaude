---
name: ah:triage
description: Review the dependency graph of work items from a PRD, update their blocked/ready status, and recommend which item to work on next. Use when user wants to triage issues, check what's unblocked, update item status, or find the next thing to work on.
---

Walk the dependency graph of work items from a PRD, reconcile status
against reality, and recommend what to work on next.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

1. Fetch the parent PRD and all its child items.
2. For each child, check whether its blockers are resolved. Classify
   as done, in progress, ready, or blocked.
3. Present status overview. Propose and apply status updates with
   user confirmation.
4. Recommend a ready item to pick up next — prefer items that unblock
   the most other work. Offer to jump into `/ah:work-issue`.
