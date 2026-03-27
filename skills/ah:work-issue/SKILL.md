---
name: ah:work-issue
description: Pick up a work item that has no blocking dependencies and implement it end-to-end. Use when user wants to start working on an issue, implement a ticket, or grab an unblocked item.
---

Implement a work item end-to-end.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

1. Fetch the item and verify blockers are resolved.
2. Fetch the parent PRD — extract implementation decisions, testing
   decisions, and out-of-scope items relevant to this slice.
3. Fetch completed sibling items and study their merged PRs for
   established patterns. Be consistent — don't reinvent.
4. Plan the implementation and wait for user approval.
5. Branch, implement, test, commit atomically.
6. Use **ah:create-pr** to open a PR that links back to the item.
