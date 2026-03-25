---
name: prd-to-issues
description: Break a PRD into independently-grabbable work items using tracer-bullet vertical slices. Use when user wants to convert a PRD to work items, create implementation tickets, or break down a PRD into tasks.
---

# PRD to Work Items

Break a PRD into independently-grabbable work items using vertical
slices (tracer bullets).

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

### 1. Locate the PRD
Ask the user for the PRD identifier (issue number, ticket key, or
local plan directory). Fetch it using the tracker instructions.

### 2. Explore the codebase (optional)
If you have not already explored the codebase, do so to understand
the current state of the code.

### 3. Draft vertical slices
Break the PRD into work items following the
[vertical slicing guide](../_resources/vertical-slicing.md).

### 4. Quiz the user
Present the proposed breakdown as a numbered list. For each slice:
- Title, Type (HITL/AFK), Blocked by, User stories covered

Ask: Does the granularity feel right? Are dependencies correct?
Should any slices be merged or split? Iterate until approved.

### 5. Create the work items
For each approved slice, create a work item using the tracker
instructions and the template from the
[vertical slicing guide](../_resources/vertical-slicing.md).
Create in dependency order (blockers first).

### 6. Link as children
Link each work item as a child of the PRD using the tracker
instructions. Do NOT close the parent PRD item.
