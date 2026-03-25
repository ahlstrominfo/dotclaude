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
local plan directory). Fetch the PRD using the tracker instructions.

### 2. Explore the codebase (optional)
If you have not already explored the codebase, do so to understand
the current state of the code.

### 3. Draft vertical slices
Break the PRD into tracer bullet work items. Each item is a thin
vertical slice that cuts through ALL integration layers end-to-end,
NOT a horizontal slice of one layer.

Slices may be 'HITL' or 'AFK'. HITL slices require human interaction,
such as an architectural decision or a design review. AFK slices can
be implemented and merged without human interaction. Prefer AFK over
HITL where possible.

<vertical-slice-rules>
- Each slice delivers a narrow but COMPLETE path through every layer
  (schema, API, UI, tests)
- A completed slice is demoable or verifiable on its own
- Prefer many thin slices over few thick ones
</vertical-slice-rules>

### 4. Quiz the user
Present the proposed breakdown as a numbered list. For each slice:
- Title: short descriptive name
- Type: HITL / AFK
- Blocked by: which other slices must complete first
- User stories covered: which user stories from the PRD

Ask the user:
- Does the granularity feel right?
- Are the dependency relationships correct?
- Should any slices be merged or split further?
- Are the correct slices marked as HITL and AFK?

Iterate until the user approves the breakdown.

### 5. Create the work items
For each approved slice, create a work item using the tracker
instructions. Create in dependency order (blockers first) so you
can reference real identifiers.

<item-template>
## What to build
A concise description of this vertical slice. Describe the
end-to-end behavior, not layer-by-layer implementation.
Reference specific sections of the parent PRD rather than
duplicating content.

## Acceptance criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Blocked by
- Blocked by <item-identifier> (if any)
Or "None - can start immediately"

## User stories addressed
Reference by number from the parent PRD:
- User story 3
- User story 7
</item-template>

### 6. Link as children
After creating each work item, link it as a child of the PRD
using the tracker instructions.

Do NOT close the parent PRD item.
