# Routing Heuristics -- Edge Cases

Decision guide for ambiguous routing scenarios in the consolidate skill.

## Instruction vs Learning

| Signal | Destination | Why |
|--------|-------------|-----|
| User says "always do X" | CLAUDE.md or rules | Prescriptive instruction |
| Claude discovers X works better | Auto memory | Descriptive learning |
| User corrects Claude's approach | Auto memory (correction) | Claude needs to remember |
| Team convention stated | Project CLAUDE.md | Team-shared instruction |
| Personal style preference | Global CLAUDE.md | Cross-project preference |
| Ambiguous | Ask the user | Don't guess intent |

## Project CLAUDE.md vs Global CLAUDE.md

- **Project**: conventions tied to this repo's stack, team, or domain
  - "Use Tailwind v4 utility classes" -- project-specific tooling
  - "API responses use JSON-API format" -- repo convention
- **Global**: personal preferences that follow the user across repos
  - "Be direct, skip padding" -- interaction style
  - "Use bun not npm" -- personal tooling preference
- **Test**: would this matter if the user switched to a different project? Yes → global. No → project.

## CLAUDE.md vs Rules

- **CLAUDE.md**: broad instructions applying to most or all files
  - "All functions must have JSDoc comments"
  - "Use early returns over nested conditionals"
- **Rules** (`.claude/rules/*.md`): instructions scoped to specific paths
  - "Validate all request bodies" → scoped to `src/api/**`
  - "Use test factories, never raw fixtures" → scoped to `tests/**`
- Rules use `paths` frontmatter to specify scope:
  ```yaml
  ---
  paths: ["src/api/**"]
  ---
  ```

## When to Create Topic Files

Create a new memory topic file when:
- 5+ related entries would bloat MEMORY.md
- A category keeps growing across sessions (e.g., debugging notes)
- MEMORY.md exceeds 180 lines and needs offloading

Always:
- Link from MEMORY.md: `See [debugging notes](debugging.md) for details`
- Name descriptively: `debugging.md`, `api-patterns.md`, `tooling.md`
- Keep topic files focused on one category

## Cross-Project Learnings

If the same correction or convention has appeared across multiple projects:
- Promote from project memory to global `~/.claude/CLAUDE.md`
- Remove the project-specific entries to avoid duplication
- Example: "Claude keeps using npm" across 3 projects → add to global CLAUDE.md

## Formatting Rules

- Match the existing file's style (headers, bullets, indentation, spacing)
- One learning per bullet, <15 words when possible
- Use imperative form: "Use X" not "We learned that X"
- No timestamps or session references -- learnings should be timeless
- Group related entries under existing headers when possible
