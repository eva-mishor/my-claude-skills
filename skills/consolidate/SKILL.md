---
name: consolidate
description: Post-session learning extraction and memory management. Use when wrapping up a session, after significant discoveries, or when the user says "consolidate", "save learnings", "update memory", "extract insights", "what did we learn". Auto-detects sessions with 3+ corrections, new conventions, hard debugging solved, or explicit preferences stated.
---

# Consolidate -- Session Learning Extraction

Systematically extract learnings from the current session and route them to the correct persistent storage. Complements native auto memory with a deliberate review pass.

## Phase 1: Extract

Scan the full conversation for learning types:

| Type | What to look for |
|------|-----------------|
| Convention | Coding standards, naming patterns, file organization rules established or clarified |
| Correction | User corrected Claude's assumption, approach, or output |
| Preference | Explicit workflow, tool, style, or interaction preferences |
| Debug insight | Non-obvious root cause, diagnostic technique, environment quirk |
| Tool/env | CLI flags, config settings, build commands, dependency notes |
| Architecture | System design decisions, data flow, component relationships explained |

For each learning, record:
- **What**: imperative one-liner (<15 words when possible)
- **Type**: from table above
- **Evidence**: brief quote or reference from conversation
- **Scope**: project or global

**Skip**: obvious-from-code facts, ephemeral state (current branch, in-progress work), non-actionable observations.

## Phase 2: Route

Determine the correct destination for each learning:

### Global CLAUDE.md (`~/.claude/CLAUDE.md`)
Personal interaction and workflow preferences that apply across all projects.
Examples: "Be direct, critique first", "Always use bun instead of npm", "Skip closing encouragement".

### Project MEMORY.md (`~/.claude/projects/<project>/memory/MEMORY.md`)
Repo-specific conventions, architecture notes, project tooling, debug insights.
Examples: "Tests use vitest not jest", "API responses are snake_case", "Build requires NODE_ENV=production".

### Memory topic file (e.g., `debugging.md`, `patterns.md`)
Use when MEMORY.md already links to an existing topic file for the category, or when MEMORY.md is at 180+ lines and needs offloading. Always link new topic files from MEMORY.md.

### Project CLAUDE.md (`./CLAUDE.md`)
Team-shared project instructions checked into git. Build commands, coding standards, conventions worth sharing with collaborators.
Examples: "Run `make lint` before committing", "All API handlers must return JSON-API format".

### Rules (`.claude/rules/*.md`)
Path-scoped instructions with `paths` frontmatter for targeted guidance.
Example: "API handlers must validate input" scoped to `src/api/**`.

### Distinguishing instructions from learnings
- **Instructions** belong in CLAUDE.md or rules -- user-written, team-shared, prescriptive
- **Learnings** belong in auto memory -- Claude-written, machine-local, descriptive
- When ambiguous, ask the user which type the item is

For edge cases, read `references/routing-heuristics.md`.

## Phase 3: Deduplicate

Read each target file fully before proposing changes.

For each learning, classify against existing content:
- **Exact duplicate**: skip silently
- **Partial overlap**: propose update-in-place (merge into existing entry)
- **Contradicts existing**: flag both versions, ask user which is current
- **Novel**: add as new entry

### MEMORY.md capacity management
- Check current line count against 200-line limit (lines past 200 are truncated)
- If at 180+ lines: propose removals of stale entries before adding new ones
- Suggest offloading dense categories to topic files linked from MEMORY.md
- Stale indicators: merged branches, resolved issues, superseded conventions, completed migration notes

## Phase 4: Present Proposal

Show a grouped diff-style summary per target file:

```
## ~/.claude/CLAUDE.md (1 addition)
```diff
+ - Use bun instead of npm for all package management
```

## memory/MEMORY.md (2 additions, 1 removal)
```diff
+ - API responses use snake_case keys (confirmed in session)
+ - vitest runs with --pool=forks flag for stability
- - Investigating flaky test in auth module (resolved)
```
```

End with a summary line:
> **Total**: N additions, N updates, N removals across N files. MEMORY.md: X/200 lines after changes.

Then wait for explicit approval. Accept:
- **yes** -- apply all changes
- **selective** -- user picks which changes to apply; present numbered list
- **no** -- discard all

## Phase 5: Write

1. Apply only approved changes using Edit tool (prefer surgical edits over full rewrites)
2. For new topic files, create them and add a link from MEMORY.md
3. Confirm what was written and where
4. Report final MEMORY.md line count vs 200-line limit

## Auto-Detection

This skill can suggest itself when session signals indicate valuable unrecorded learnings.

### Rules
- Do NOT interrupt user flow -- accumulate signals silently
- Suggest only at natural pauses (task completion, user asks "anything else?")
- Suggest at most once per session
- Phrasing: "This session produced learnings worth saving. Run /consolidate?"

### Signals (need 2+ to trigger suggestion)
- User corrections that Claude adopted
- Non-obvious root cause discovered during debugging
- Explicit preference or convention stated by user
- New architectural pattern explained
- Repeated workflow established ("always do X before Y")
