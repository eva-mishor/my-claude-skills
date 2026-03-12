---
name: wait-what
description: Use when the user asks for a session summary, wants to know what changed and why, or needs a checkpoint before committing/pushing/merging. Trigger phrases: "wait what did we do", "summarize the changes", "what's the status", "are we done?", "what's left?"
---

# Wait What

Generate a structured high-level overview of the session's work: what was done, why, and what's next.

## When to Use

- User returns after a break and needs context
- Handoff summaries between sessions

## Output Structure

Three sections, each 2-5 bullet points max:

### What we did
- Name the change at the level a teammate would understand
- Mention the scope (files, systems, PR) without listing every file

### Why
- The motivation: bug, code review, feature request, tech debt
- Connect to the triggering event (PR feedback, failing test, user request)

### What's next
- Immediate follow-ups (retrain, deploy, verify)
- Deferred items if any were explicitly noted (link to TODO/issue)
- Nothing speculative — only items that were discussed or documented

## Guidelines

- **Concise over complete.** If it takes more than 30 seconds to read, it's too long.
- **No file lists.** Summarize by component/concern, not by path.
- **Use the repo's language.** Match terminology from CLAUDE.md, PR descriptions, commit messages.
- **Honest about gaps.** If something was skipped or deferred, say so.
- **No fluff.** No "great progress" or "exciting changes." Just facts.
