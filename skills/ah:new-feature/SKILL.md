---
name: ah:new-feature
description: Orchestrate the full feature delivery pipeline from rough idea to merged PRs. Walks the user through design interrogation, PRD creation, issue breakdown, triage, and implementation. Use when user wants to build a feature end-to-end, start a new feature from scratch, or run the full delivery pipeline.
---

# Feature Pipeline

Orchestrate the full delivery pipeline for a new feature, from rough
idea to merged pull requests. This skill guides the user through each
phase, invoking the appropriate skill at each step.

## Tracker selection

Before starting, ask the user which tracker to use: **github**,
**jira**, or **local**.

Read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

Carry this choice forward through all phases — do NOT ask again when
invoking sub-skills. Tell each sub-skill which tracker is in use.

## Pipeline

### Phase 1: Design Interrogation
Use the **ah:discuss-feature** skill to interview the user about their idea.
The goal is to reach a shared understanding of the problem and
solution before writing anything down formally.

When the user is satisfied that the idea is well-understood,
proceed to Phase 2.

### Phase 2: PRD Creation
Use the **ah:write-prd** skill to formalize the design into a PRD.
This will interview the user further, explore the codebase, sketch
modules, and create the PRD as a work item.

When the PRD is created, note its identifier and proceed to Phase 3.

### Phase 3: Research & Validate
Use the **ah:research-prd** skill to validate the PRD's approach.
This will explore related code in the codebase, search the web for
best practices and how others solve similar problems, and give
concrete feedback on the proposed solution.

Update the PRD based on findings, then proceed to Phase 4.

### Phase 4: Work Item Breakdown
Use the **ah:slice-prd** skill to break the PRD into vertical
slice work items. This will draft thin end-to-end slices, quiz the
user on the breakdown, and create the items in dependency order.

When all items are created, proceed to Phase 4.

### Phase 5: Triage and Work Loop
This is the iterative phase. Repeat until all items are done:

1. Use the **ah:triage** skill to review the dependency graph,
   update statuses, and identify which items are ready to work on.

2. When a ready item is identified, use the **ah:work-issue** skill
   to implement it — branch, code, test, commit, and open a PR.

3. After the PR is opened, loop back to step 1 to re-triage.
   Completing one item may unblock others.

## Guidelines

- **Don't skip phases.** Each phase builds on the previous one.
  Rushing to code without a clear PRD leads to rework.
- **Pause between phases.** After each phase completes, briefly
  summarize what was accomplished and confirm with the user before
  moving on.
- **The user drives the pace.** Some sessions may only cover one
  phase. That's fine — the tracker preserves state between
  sessions. Pick up where you left off.
- **Adapt to context.** If the user already has a PRD, skip to
  Phase 3. If items already exist, skip to Phase 4. Ask the user
  where they are if unclear.
