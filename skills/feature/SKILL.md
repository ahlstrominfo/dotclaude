---
name: feature
description: Orchestrate the full feature delivery pipeline from rough idea to merged PRs. Walks the user through design interrogation, PRD creation, issue breakdown, triage, and implementation. Use when user wants to build a feature end-to-end, start a new feature from scratch, or run the full delivery pipeline.
---

# Feature Pipeline

Orchestrate the full delivery pipeline for a new feature, from rough
idea to merged pull requests. This skill guides the user through each
phase, invoking the appropriate skill at each step.

## Pipeline

### Phase 1: Design Interrogation
Use the **grill-me** skill to interview the user about their idea.
The goal is to reach a shared understanding of the problem and
solution before writing anything down formally.

When the user is satisfied that the idea is well-understood,
proceed to Phase 2.

### Phase 2: PRD Creation
Use the **write-a-prd** skill to formalize the design into a PRD.
This will interview the user further, explore the codebase, sketch
modules, and submit the PRD as a GitHub issue.

When the PRD issue is created, note the issue number and proceed
to Phase 3.

### Phase 3: Issue Breakdown
Use the **prd-to-issues** skill to break the PRD into vertical
slice issues. This will draft thin end-to-end slices, quiz the user
on the breakdown, and create the GitHub issues in dependency order.

When all issues are created, proceed to Phase 4.

### Phase 4: Triage and Work Loop
This is the iterative phase. Repeat until all issues are closed:

1. Use the **triage-issues** skill to review the dependency graph,
   update labels, and identify which issues are ready to work on.

2. When a ready issue is identified, use the **work-issue** skill
   to implement it — branch, code, test, commit, and open a PR.

3. After the PR is opened, loop back to step 1 to re-triage.
   Completing one issue may unblock others.

## Guidelines

- **Don't skip phases.** Each phase builds on the previous one.
  Rushing to code without a clear PRD leads to rework.
- **Pause between phases.** After each phase completes, briefly
  summarize what was accomplished and confirm with the user before
  moving on.
- **The user drives the pace.** Some sessions may only cover one
  phase. That's fine — the GitHub issues preserve state between
  sessions. Pick up where you left off.
- **Adapt to context.** If the user already has a PRD, skip to
  Phase 3. If issues already exist, skip to Phase 4. Ask the user
  where they are if unclear.
