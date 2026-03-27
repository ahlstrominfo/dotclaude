---
name: ah:new-feature
description: Orchestrate the full feature delivery pipeline from rough idea to merged PRs. Walks the user through design interrogation, PRD creation, issue breakdown, triage, and implementation. Use when user wants to build a feature end-to-end, start a new feature from scratch, or run the full delivery pipeline.
---

# Feature Pipeline

Orchestrate full delivery from rough idea to merged PRs.

## Tracker selection

Ask the user: **github**, **jira**, or **local**.

Read the corresponding resource file:
- GitHub: [tracker-github.md](../_resources/tracker-github.md)
- Jira: [tracker-jira.md](../_resources/tracker-jira.md)
- Local: [tracker-local.md](../_resources/tracker-local.md)

Carry this choice forward — do NOT ask again in sub-skills.

## Pipeline

1. **ah:discuss-feature** — reach shared understanding of the problem
2. **ah:write-prd** — formalize into a PRD
3. **ah:research-prd** — validate approach against codebase and web
4. **ah:slice-prd** — break into vertical slice work items
5. **ah:triage** ↔ **ah:work-issue** — triage and implement in a loop

Pause between phases to confirm with the user. Adapt to context —
skip phases if the user already has a PRD or items.
