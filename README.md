# dotclaude

Shared Claude Code commands and skills, designed to be symlinked into one or more Claude Code config directories.

## Structure

```
dotclaude/
  commands/            -> custom slash commands
  skills/
    feature/SKILL.md
    grill-me/SKILL.md
    write-a-prd/SKILL.md
    prd-to-issues/SKILL.md
    triage-issues/SKILL.md
    work-issue/SKILL.md
    create-pr/SKILL.md
    improve-codebase-architecture/SKILL.md
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

### feature (orchestrator)
Full delivery pipeline from rough idea to merged PRs. Walks through each phase in sequence, invoking the skills below:

```
/feature
  → grill-me → write-a-prd → prd-to-issues → triage-issues ↔ work-issue
```

### grill-me
Interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree.

### write-a-prd
Create a PRD through user interview, codebase exploration, and module design, then submit as a GitHub issue.

### prd-to-issues
Break a PRD into independently-grabbable GitHub issues using tracer-bullet vertical slices.

### triage-issues
Review the dependency graph of issues from a PRD, update blocked/ready status, and recommend which issue to work on next.

### work-issue
Pick up an unblocked GitHub issue and implement it end-to-end: branch, code, test, commit, and open a PR.

### create-pr
Create a GitHub PR that matches the repo's existing style. Analyzes the last 10 merged PRs for tone and conventions, checks for PR templates, and drafts a distilled PR with no filler.

### improve-codebase-architecture
Explore a codebase to find opportunities for architectural improvement, focusing on making the codebase more testable by deepening shallow modules. Standalone — can feed new issues back into the pipeline.

## Credits

Several skills here were inspired by Matt Pocock's [5 Claude Code Skills](https://youtu.be/EJyuu6zlQCg) ([blog](https://www.aihero.dev/5-agent-skills-i-use-every-day) | [GitHub](https://github.com/mattpocock/skills)).
