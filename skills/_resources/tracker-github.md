# GitHub Issues Tracker

All work items are GitHub issues. PRDs and RFCs are issues. Child items
are sub-issues linked via the GraphQL API.

## Create a work item

```bash
gh issue create --title "<title>" --body "<body>" --label "<label>"
```

Capture the returned issue number for linking.

## Fetch a work item

```bash
gh issue view <number>
```

## Fetch children of a parent item

Use the GraphQL sub-issues API:
```bash
gh api graphql -f query='query {
  repository(owner: "<owner>", name: "<repo>") {
    issue(number: <parent-number>) {
      subIssues(first: 100) {
        nodes { number title state labels(first: 10) { nodes { name } } }
      }
    }
  }
}'
```

## Link a child to a parent

First get the node IDs:
```bash
gh api graphql -f query='query {
  repository(owner: "<owner>", name: "<repo>") {
    issue(number: <number>) { id }
  }
}'
```

Then link:
```bash
gh api graphql -f query='mutation {
  addSubIssue(input: {
    issueId: "<parent-node-id>"
    subIssueId: "<child-node-id>"
  }) {
    issue { id }
  }
}'
```

## Update status

Use labels to track status:
```bash
gh issue edit <number> --add-label <label> --remove-label <label>
```

Common labels: `blocked`, `ready`, `in-progress`.

## Assign an item

```bash
gh issue edit <number> --add-assignee @me
```

## Search / list items

```bash
gh issue list --label "<label>" --state open
```

## Determine owner and repo

Extract from the current git remote:
```bash
gh repo view --json owner,name -q '.owner.login + "/" + .name'
```
