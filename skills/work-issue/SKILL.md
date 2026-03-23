---
name: work-issue
description: Pick up a GitHub issue that has no blocking dependencies and implement it end-to-end. Use when user wants to start working on an issue, implement a ticket, or grab an unblocked issue.
---

# Work Issue

Implement a GitHub issue end-to-end: understand context, branch, code,
test, and open a PR.

## Process

### 1. Identify the issue
Fetch with `gh issue view <number>`. Verify any "Blocked by" issues
are closed. Assign to yourself.

### 2. Gather context from the parent PRD
Find the parent PRD reference in the issue body (look for "PRD #NNN",
"Se PRD #NNN", or similar). Also check sub-issue relationships via
the GitHub API. Fetch the parent and extract:
- **Implementation decisions** relevant to this slice
- **Testing decisions** (what to test, how, prior art)
- **Out of scope** — so you don't accidentally build it

Issues often reference specific PRD sections (e.g., "See PRD #7665,
sections: Tool Definition, Tool Execution"). Follow those pointers —
they are the design constraints for this slice.

### 3. Learn from sibling issues
List sub-issues of the parent PRD:
```
gh api graphql -f query='query {
  repository(owner: "<owner>", name: "<repo>") {
    issue(number: <prd-number>) {
      subIssues(first: 50) {
        nodes { number title state }
      }
    }
  }
}'
```

For closed siblings, find their merged PRs and study the patterns
they established: naming, file structure, abstractions, test
approach. Be consistent with what came before — do not reinvent
patterns or introduce competing abstractions.

### 4. Read referenced code patterns
Issues and PRDs often point to existing code to follow (e.g.,
"follow the store pattern like klipparenStore", "reuse SSE
streaming from Chattis"). Find these references and read that
code before planning. They are deliberate design constraints.

### 5. Plan the implementation
Present a plan covering: files to create/modify, approach per
acceptance criterion, alignment with PRD decisions and sibling
patterns, and tests to write. Wait for user approval.

### 6. Implement
Branch, implement acceptance criteria one by one, write tests,
verify they pass. Keep commits atomic.

### 7. Open a PR
Use the **create-pr** skill. Include "Closes #<issue-number>".
