---
name: ah:improve-architecture
description: Explore a codebase to find opportunities for architectural improvement, focusing on making the codebase more testable by deepening shallow modules. Use when user wants to improve architecture, find refactoring opportunities, consolidate tightly-coupled modules, or make a codebase more AI-navigable.
---

Find opportunities to deepen shallow modules (Ousterhout) — small
interface, large implementation, testable at the boundary.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

1. Explore the codebase. Note friction: bouncing between files,
   shallow modules, tight coupling, hard-to-test code.
2. Present candidates as a numbered list (cluster, why coupled, test
   impact). Do NOT propose interfaces yet — ask which to explore.
3. For the chosen candidate, frame the problem space with constraints
   and a rough code sketch.
4. Design multiple interfaces using the
   [interface design agent instructions](../_resources/interface-design-agents.md).
5. User picks an interface. Create a refactor RFC as a work item.
