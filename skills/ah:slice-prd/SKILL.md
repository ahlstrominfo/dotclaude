---
name: ah:slice-prd
description: Break a PRD into independently-grabbable work items using tracer-bullet vertical slices. Use when user wants to convert a PRD to work items, create implementation tickets, or break down a PRD into tasks.
---

Break a PRD into vertical slice work items.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

1. Fetch the PRD. Explore the codebase if needed.
2. Draft slices following the
   [vertical slicing guide](../_resources/vertical-slicing.md).
3. Present the breakdown to the user — iterate until approved.
4. Create items in dependency order using the template from the
   [vertical slicing guide](../_resources/vertical-slicing.md).
   Link each as a child of the PRD. Do NOT close the parent.
