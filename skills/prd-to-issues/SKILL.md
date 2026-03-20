---
name: prd-to-issues
description: Break a PRD into independently-grabbable GitHub issues using tracer-bullet vertical slices. Use when user wants to convert a PRD to issues, create implementation tickets, or break down a PRD into work items.
---

# PRD to Issues

Break a PRD into independently-grabbable GitHub issues using vertical
slices (tracer bullets).

## Process

### 1. Locate the PRD
Ask the user for the PRD GitHub issue number (or URL).
If the PRD is not already in your context window, fetch it with
`gh issue view <number>` (with comments).

### 2. Explore the codebase (optional)
If you have not already explored the codebase, do so to understand
the current state of the code.

### 3. Draft vertical slices
Break the PRD into tracer bullet issues. Each issue is a thin
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

### 5. Create the GitHub issues as sub-issues
For each approved slice, create using `gh issue create`.
Create in dependency order (blockers first) so you can reference
real issue numbers.

<issue-template>
## What to build
A concise description of this vertical slice. Describe the
end-to-end behavior, not layer-by-layer implementation.
Reference specific sections of the parent PRD rather than
duplicating content.

## Acceptance criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Blocked by
- Blocked by #<issue-number> (if any)
Or "None - can start immediately"

## User stories addressed
Reference by number from the parent PRD:
- User story 3
- User story 7
</issue-template>

### 6. Link as sub-issues
After creating each issue, link it as a sub-issue of the PRD
using the GitHub GraphQL API.

First, get the node IDs:
```
gh api graphql -f query='query {
  repository(owner: "<owner>", name: "<repo>") {
    issue(number: <prd-number>) { id }
  }
}'
```

Then for each child issue, add it as a sub-issue:
```
gh api graphql -f query='mutation {
  addSubIssue(input: {
    issueId: "<parent-node-id>"
    subIssueId: "<child-node-id>"
  }) {
    issue { id }
  }
}'
```

This gives the PRD a native sub-issue list in GitHub's UI —
no manual tracking needed.

Do NOT close the parent PRD issue.
