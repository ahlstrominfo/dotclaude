# Local Plans Tracker

All work items are markdown files in the `plans/` directory at the repo
root. No external services required.

## Directory structure

```
plans/
  <feature-name>/
    prd.md              # The PRD
    001-<slice-name>.md # Child work items, numbered by dependency order
    002-<slice-name>.md
  rfcs/
    <rfc-name>.md       # Standalone RFCs
```

## Work item format

Every child work item file uses this frontmatter:

```yaml
---
title: <descriptive title>
status: pending | ready | blocked | in-progress | done
blocked-by: [001-<name>]  # list of sibling filenames, or empty
---
```

Followed by the work item body (description, acceptance criteria, etc.).

PRD files (`prd.md`) do not need status frontmatter.

## Create a work item

### PRD
Create `plans/<feature-name>/prd.md` with the PRD content.

### Child item
Create `plans/<feature-name>/NNN-<slice-name>.md` with frontmatter
and body. Number sequentially starting from 001.

### RFC
Create `plans/rfcs/<rfc-name>.md` with the RFC content.

## Fetch a work item

Read the file directly.

## Fetch children of a parent item

List all numbered files in the feature directory:
```bash
ls plans/<feature-name>/[0-9]*.md
```

## Link a child to a parent

No explicit linking needed — children live inside the parent's
directory. Use the `blocked-by` frontmatter field to express
dependencies between siblings.

## Update status

Edit the `status` field in the file's frontmatter. Valid values:
- `pending` — not yet ready to start
- `ready` — all blockers resolved, can start
- `blocked` — waiting on other items
- `in-progress` — currently being worked on
- `done` — completed

## Assign an item

Not applicable for local plans. Optionally add an `assignee` field
to frontmatter if working in a team.

## Search / list items

```bash
grep -l "status: ready" plans/<feature-name>/*.md
grep -l "status: blocked" plans/<feature-name>/*.md
```
