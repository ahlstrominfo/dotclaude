# Jira Tracker

All work items are Jira tickets. PRDs and RFCs are tickets. Child items
are subtasks linked to a parent ticket.

Before starting, ask the user for:
- **Jira project key** (e.g., `PROJ`)
- **Jira CLI tool** they have installed (e.g., `jira`, or confirm using REST API via `curl`)

## Create a work item

```bash
jira issue create --project <PROJECT> --type Task --summary "<title>" --description "<body>"
```

Capture the returned ticket key (e.g., `PROJ-123`) for linking.

For PRDs, use type `Story` or `Epic` depending on team convention — ask the user.

## Fetch a work item

```bash
jira issue view <ticket-key>
```

## Fetch children of a parent item

```bash
jira issue list --parent <ticket-key>
```

Or query via JQL:
```bash
jira issue list --jql "parent = <ticket-key>"
```

## Link a child to a parent

Create the child as a subtask:
```bash
jira issue create --project <PROJECT> --type Sub-task --parent <parent-key> --summary "<title>" --description "<body>"
```

If the child already exists, link it:
```bash
jira issue link <child-key> <parent-key> "is child of"
```

## Update status

Transition the ticket to a new status:
```bash
jira issue move <ticket-key> "<status>"
```

Common statuses: `To Do`, `In Progress`, `Blocked`, `Done`.

If the project uses custom statuses, ask the user.

## Assign an item

```bash
jira issue assign <ticket-key> <username>
```

Ask the user for their Jira username if needed.

## Search / list items

```bash
jira issue list --project <PROJECT> --status "To Do"
jira issue list --jql "project = <PROJECT> AND status = 'Open'"
```
