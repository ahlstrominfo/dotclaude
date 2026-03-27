# dotclaude

Shared Claude Code commands and skills, designed to be symlinked into one or more Claude Code config directories.

## Structure

```
dotclaude/
  commands/            -> custom slash commands
  skills/
    ah:new-feature/SKILL.md
    ah:discuss-feature/SKILL.md
    ah:write-prd/SKILL.md
    ah:slice-prd/SKILL.md
    ah:triage/SKILL.md
    ah:work-issue/SKILL.md
    ah:create-pr/SKILL.md
    ah:improve-architecture/SKILL.md
    ah:review-decisions/SKILL.md
```

## Setup

```bash
# Clone the repo
git clone git@github.com:ahlstrominfo/dotclaude.git ~/repos/dotclaude

# Symlink into your Claude config dir
ln -s ~/repos/dotclaude/commands ~/.claude/commands
ln -s ~/repos/dotclaude/skills ~/.claude/skills
```

If you use multiple Claude config directories (e.g. via `CLAUDE_CONFIG_DIR`), symlink into each one.

## Skills

### ah:new-feature (orchestrator)
Full delivery pipeline from rough idea to merged PRs. Walks through each phase in sequence, invoking the skills below:

```
/ah:new-feature
  → ah:discuss-feature → ah:write-prd → ah:slice-prd → ah:triage ↔ ah:work-issue
```

### ah:discuss-feature
Interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree.

### ah:write-prd
Create a PRD through user interview, codebase exploration, and module design, then submit as a work item.

### ah:slice-prd
Break a PRD into independently-grabbable work items using tracer-bullet vertical slices.

### ah:triage
Review the dependency graph of work items from a PRD, update blocked/ready status, and recommend which item to work on next.

### ah:work-issue
Pick up an unblocked work item and implement it end-to-end: branch, code, test, commit, and open a PR.

### ah:create-pr
Create a GitHub PR that matches the repo's existing style. Analyzes the last 10 merged PRs for tone and conventions, checks for PR templates, and drafts a distilled PR with no filler.

### ah:improve-architecture
Explore a codebase to find opportunities for architectural improvement, focusing on making the codebase more testable by deepening shallow modules. Standalone — can feed new issues back into the pipeline.

### ah:review-decisions
Walk through every decision or assumption in a plan, one by one, asking the user to confirm, change, or remove each.

## Credits

Several skills here were inspired by Matt Pocock's [5 Claude Code Skills](https://youtu.be/EJyuu6zlQCg) ([blog](https://www.aihero.dev/5-agent-skills-i-use-every-day) | [GitHub](https://github.com/mattpocock/skills)).
