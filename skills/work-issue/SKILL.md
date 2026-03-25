---
name: work-issue
description: Pick up a work item that has no blocking dependencies and implement it end-to-end. Use when user wants to start working on an issue, implement a ticket, or grab an unblocked item.
---

# Work Item

Implement a work item end-to-end: understand context, branch, code,
test, and open a PR.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

### 1. Identify the item
Fetch the work item using the tracker instructions. Verify any
"Blocked by" items are resolved. Assign to yourself if the tracker
supports it.

### 2. Gather context from the parent PRD
Find the parent PRD reference in the item body (look for PRD
references or parent links). Fetch the parent and extract:
- **Implementation decisions** relevant to this slice
- **Testing decisions** (what to test, how, prior art)
- **Out of scope** — so you don't accidentally build it

Items often reference specific PRD sections. Follow those pointers —
they are the design constraints for this slice.

### 3. Learn from sibling items
Fetch all children of the parent PRD using the tracker instructions.

For completed siblings, find their merged PRs and study the patterns
they established: naming, file structure, abstractions, test
approach. Be consistent with what came before — do not reinvent
patterns or introduce competing abstractions.

### 4. Read referenced code patterns
Items and PRDs often point to existing code to follow. Find these
references and read that code before planning. They are deliberate
design constraints.

### 5. Plan the implementation
Present a plan covering: files to create/modify, approach per
acceptance criterion, alignment with PRD decisions and sibling
patterns, and tests to write. Wait for user approval.

### 6. Implement
Branch, implement acceptance criteria one by one, write tests,
verify they pass. Keep commits atomic.

### 7. Open a PR
Use the **create-pr** skill. Reference the work item identifier
so the PR links back to it (e.g., "Closes #<number>" for GitHub).
