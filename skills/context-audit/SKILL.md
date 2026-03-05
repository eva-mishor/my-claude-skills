---
name: context-audit
description: Audit and optimize Claude Code session context budget. Use when sessions feel sluggish, context compacts too early, or after installing new plugins/MCP servers. Triggers on "audit context", "optimize context", "context budget", "session overhead".
---

# Context Audit -- Session Budget Optimizer

Measure, identify, and reduce startup context overhead so more budget goes to actual work.

**Target**: <25% of context budget consumed at session start.

## Phase 1: Measure Baseline

1. Run `/context` and record token counts by category
2. Note total budget and startup consumption percentage
3. Record counts for: system prompt, MCP tools, custom agents, memory files, skills, project instructions (CLAUDE.md, TESTING.md, etc.)
4. This is your baseline -- save these numbers for comparison in Phase 4

## Phase 2: Identify Waste

Audit each category for unnecessary overhead:

### MCP Servers
- List all servers in project `.claude/settings.json` and global `~/.claude/settings.json`
- Flag servers with 10+ tools that aren't used in this project (e.g., Linear tools on a solo project)
- Flag servers enabled globally that only apply to specific projects

### Plugins
- List enabled plugins (global + project)
- Flag plugins loading 5+ skills/tools you don't actively use
- Check if any plugin skills overlap with project-specific skills

### MEMORY.md
- Stale entries: old branch status, merged PRs, resolved issues
- Duplication with CLAUDE.md (rules stated in both places)
- Narrative where a one-liner suffices
- Lines past 200 are truncated -- prioritize what's above the fold

### CLAUDE.md & Project Instructions
- Rules Claude already follows by default (don't restate defaults)
- Verbose formatting where semicolons/pipe-delimiters work
- Content that belongs in on-demand files (referenced with `@`) not always-loaded
- Multiple project instruction files (TESTING.md, README.md, etc.) -- do all need `checked into the codebase` always-load?

### Custom Agents
- Check if any always-loaded agents could be on-demand skills instead
- Flag agents with overlapping responsibilities

## Phase 3: Optimize

Apply fixes in order of impact:

1. **Disable unused MCP servers** -- edit `.claude/settings.json`, set `"disabled": true` per server
2. **Disable unused plugins** -- edit `~/.claude/settings.json` or project settings
3. **Compress CLAUDE.md** -- semicolons within rules; line breaks between rules; `@file` imports for refs; remove default-behavior restatements
4. **Prune MEMORY.md** -- remove stale entries; deduplicate with CLAUDE.md; compress narratives to one-liners
5. **Move verbose docs to on-demand** -- large instruction files (TESTING.md, USAGE_GUIDE.md) can be `@`-referenced instead of always-loaded

**Note**: Compression only helps always-loaded files (CLAUDE.md, MEMORY.md, skill definitions). Skip for on-demand files like todo.md.

## Phase 4: Verify

1. Run `/context` again
2. Compare token counts against Phase 1 baseline
3. Calculate reduction percentage
4. If still >25% startup overhead, revisit Phase 2 for deeper cuts
5. Report summary: before/after tokens, percentage saved, changes made

## Quick Reference: Common Wins

| Source | Typical savings | Effort |
|--------|----------------|--------|
| Disable unused MCP server | 2-8k tokens | 30 sec |
| Disable unused plugin | 1-5k tokens | 30 sec |
| Compress CLAUDE.md formatting | 2-6k tokens | 10 min |
| Prune stale MEMORY.md | 0.5-2k tokens | 5 min |
| Move large docs to on-demand | 3-10k tokens | 5 min |
