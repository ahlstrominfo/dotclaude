# Vertical Slicing Guide

## Rules

- Each slice delivers a narrow but COMPLETE path through every layer
  (schema, API, UI, tests)
- A completed slice is demoable or verifiable on its own
- Prefer many thin slices over few thick ones
- Slices are NOT horizontal layers — they cut end-to-end

## Slice types

- **AFK** — can be implemented and merged without human interaction.
  Prefer these.
- **HITL** — requires human interaction (architectural decision,
  design review, etc.)

## Work item template

Use this template for each vertical slice work item:

```markdown
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
```
