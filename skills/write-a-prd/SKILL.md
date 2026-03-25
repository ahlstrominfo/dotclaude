---
description: Create a PRD through user interview, codebase exploration, and module design, then submit as a work item. Use when user wants to write a PRD, create a product requirements document, or plan a new feature.
---

This skill will be invoked when the user wants to create a PRD. You may
skip steps if you don't consider them necessary.

## Tracker selection

If a tracker has not already been chosen in this conversation, ask the
user which tracker to use: **github**, **jira**, or **local**.

Then read the corresponding resource file for backend-specific commands:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

## Process

1. Ask the user for a long, detailed description of the problem they
   want to solve and any potential ideas for solutions.

2. Explore the repo to verify their assertions and understand the
   current state of the codebase.

3. Interview the user relentlessly about every aspect of this plan
   until you reach a shared understanding. Walk down each branch of
   the design tree, resolving dependencies between decisions one-by-one.

4. Sketch out the major modules you will need to build or modify.
   Actively look for opportunities to extract deep modules that can
   be tested in isolation. Check with the user that these modules
   match their expectations and which they want tests for.

5. Once you have a complete understanding, write the PRD using the
   [PRD template](../_resources/prd-template.md). Create it as a
   work item using the tracker instructions.
