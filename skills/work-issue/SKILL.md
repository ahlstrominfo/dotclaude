---
name: work-issue
description: Pick up a GitHub issue that has no blocking dependencies and implement it end-to-end. Use when user wants to start working on an issue, implement a ticket, or grab an unblocked issue.
---

# Work Issue

Pick up a GitHub issue with no unresolved blockers and implement it
end-to-end: branch, code, test, commit, and open a PR.

## Process

### 1. Identify the issue
Ask the user for the issue number (or URL). Fetch it with
`gh issue view <number>`.

If the issue has a "Blocked by" section, verify each blocker is
closed. If any blocker is still open, STOP and tell the user which
issues need to be resolved first.

### 2. Understand the context
- Read the issue thoroughly, including any linked parent PRD.
- Explore the codebase to understand the areas that need to change.
- If anything in the issue is ambiguous, ask the user to clarify
  BEFORE writing code. Keep clarification questions focused and
  batched — don't ask one at a time.

### 3. Plan the implementation
Write a brief implementation plan covering:
- Which files will be created or modified
- The approach for each acceptance criterion
- Which tests to write

Present the plan to the user. Wait for approval before proceeding.

### 4. Create a branch
Create a feature branch from the main branch:
```
git checkout -b <issue-number>-<short-description>
```

### 5. Implement
Work through the acceptance criteria one by one. For each criterion:
- Write the implementation
- Write or update tests
- Verify tests pass

Keep commits atomic and focused. Commit after completing each
meaningful unit of work, not everything at the end.

### 6. Final verification
- Run the full test suite to catch regressions
- Review your own diff with `git diff main...HEAD` — look for
  anything you missed, debug code left in, or unnecessary changes

### 7. Open a PR
Use the **create-pr** skill to open the pull request. Ensure the
PR body includes "Closes #<issue-number>" to link it to the issue.
