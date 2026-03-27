---
name: ah:improve-architecture
description: Explore a codebase to find opportunities for architectural improvement, focusing on making the codebase more testable by deepening shallow modules. Use when user wants to improve architecture, find refactoring opportunities, consolidate tightly-coupled modules, or make a codebase more AI-navigable.
---

# Improve Codebase Architecture

Explore a codebase like an AI would, surface architectural friction,
discover opportunities for improving testability, and propose
module-deepening refactors as work item RFCs.

A deep module (John Ousterhout, "A Philosophy of Software Design")
has a small interface hiding a large implementation. Deep modules are
more testable, more AI-navigable, and let you test at the boundary
instead of inside.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

### 1. Explore the codebase
Use the Agent tool with subagent_type=Explore to navigate organically.
Note where you experience friction: bouncing between many files,
shallow modules, tightly-coupled components, untested or hard-to-test
code.

### 2. Present candidates
Present a numbered list of deepening opportunities. For each:
- Cluster: Which modules/concepts are involved
- Why they're coupled: Shared types, call patterns, co-ownership
- Test impact: What existing tests would be replaced by boundary tests

Do NOT propose interfaces yet. Ask: "Which of these would you like
to explore?"

### 3. User picks a candidate

### 4. Frame the problem space
Write a user-facing explanation of the constraints, dependencies,
and a rough illustrative code sketch. Show to user, then immediately
proceed to Step 5.

### 5. Design multiple interfaces
Follow the [interface design agent instructions](../_resources/interface-design-agents.md)
to spawn parallel sub-agents with different design constraints.

### 6. User picks an interface (or accepts recommendation)

### 7. Create work item
Create a refactor RFC as a work item using the tracker instructions.
Do NOT ask the user to review before creating — just create it and
share the identifier.
