---
name: repo-tidy-up
description: Use when performing repo maintenance, or when the user asks to clean up branches, dependencies, stale code, memory, or docs. Also use when "tidy up", "hygiene", "cleanup", or "maintenance" is mentioned.
---

# Repo Tidy-Up

Run through each section. Report findings, fix what's safe, flag what needs user decision.

**Default to reporting.** Every deletion here is someone's work until proven
otherwise. Batch the findings, get a decision, then act.

Examples below write the integration branch as `origin/dev`. Substitute yours
(`origin/main`, `origin/trunk`) throughout.

## 0. Safety preflight — run this BEFORE any destructive step

These rules exist because each one has already caused a real loss or near-loss.

### 0.1 Assume other agents are working in this repo right now

Claude Code sessions, Codex sessions, and background agents all share one
checkout and its worktrees. Codex sessions live in `~/.codex/sessions/YYYY/MM/DD/`,
Claude Code's in `~/.claude/projects/<slug>/`.

```bash
# Snapshot the inventory at the START of the run, and diff it before deleting.
git worktree list > /tmp/wt-before.txt
# ... later, immediately before any removal:
git worktree list | diff /tmp/wt-before.txt - || echo "INVENTORY DRIFTED — another session is active"
```

**A worktree, branch, or dirty file that appears mid-session is in use. Exclude
it.** Do not rationalise it as noise. If you notice drift and then delete the
drifted item anyway, that is the failure mode — noticing is not the hard part.

Deleting a running agent's `cwd` does not lose committed files, but it poisons
that session: every relative path and `git` call in it fails, and only a restart
fixes it.

### 0.2 `git status --porcelain` cannot see ignored files

This is the single most dangerous default in this skill. In-progress agent work
routinely lives in gitignored paths — `docs/superpowers/plans/`,
`docs/superpowers/specs/`, `.superpowers/`, `.claude/`, `.env.local`.

```bash
# WRONG — reports 0 on a worktree full of unsaved plan work
git -C "$wt" status --porcelain | wc -l

# RIGHT — the check that actually decides removal
git -C "$wt" status --porcelain --ignored=matching | wc -l
```

`git worktree remove` shares the same blind spot, so **its success is not
independent confirmation** — it refuses on tracked modifications and untracked
files, and happily deletes ignored ones. Two checks that share a weakness are
one check.

When ignored files exist, list them for the user rather than deciding yourself.

### 0.3 "Merged into main/dev" ≠ "finished"

`git merge-base --is-ancestor branch dev` is true in two opposite situations:
the branch landed, **and the branch was just cut and has no commits yet**. A
freshly created worktree passes the "safe to delete" test trivially.

```bash
# Distinguish them: a branch with no unique commits is NOT finished work
git rev-list --count origin/dev..$branch   # 0 for both cases
git log -1 --format=%s $branch             # a merge commit from dev => freshly cut, never worked
```

If the tip is a merge commit that belongs to `dev`, the branch has done nothing.
Treat it as active, not collectable.

### 0.4 Re-derive merge status immediately before deleting

Merge status is a snapshot, not a property — PRs merge while you work. Any list
computed at the start of the run is stale by the time you act.

```bash
git fetch --prune -q
while read b; do
  git merge-base --is-ancestor "origin/$b" origin/dev || { echo "ABORT: $b no longer merged"; exit 1; }
done < todelete.txt
```

### 0.5 Exclude open-PR **bases**, not just heads

Stacked PRs target another feature branch. That base is not the head of any PR,
so a head-only filter marks it deletable and deleting it breaks the stack.

```bash
gh pr list --state open --limit 100 --json headRefName,baseRefName \
  --jq '.[] | .headRefName, .baseRefName' | sort -u > protected.txt
```

### 0.6 Only delete branches whose author is the user

`git for-each-ref --format='%(authoremail)'` gives the tip author. Other
people's branches on a shared remote are theirs to clear; ask, never assume.

### 0.7 Prefer reversible

`git stash push -u -m "<why, dated>"` instead of discarding. Stashes live in the
shared object store and survive worktree removal, so they outlive the directory.
Removing a worktree with `--force` is almost never right in a tidy-up.

## 1. Branch Cleanup

```bash
git fetch --prune

# Inventory with tip author and merge status (substitute your integration branch)
git for-each-ref --format='%(refname:short)|%(authoremail)|%(committerdate:short)' \
  refs/remotes/origin/ | while IFS='|' read b e d; do
    case "$b" in origin/dev|origin/main|origin/HEAD) continue;; esac
    git merge-base --is-ancestor "$b" origin/dev 2>/dev/null \
      && echo "MERGED|$d|$e|$b" || echo "open|$d|$e|$b"
  done | sort
```

Classify before proposing anything:

| Bucket | Action |
|---|---|
| Merged + user's + no open PR + not a PR base | Safe to delete — still confirm the batch |
| Merged + someone else's | Report only; not yours to touch |
| Open + has a PR | Live work. Leave it |
| Open + no PR + >60d | Check whether it landed by another route (§1.1), then ask |
| Merged but branch has no own commits | Freshly cut — active, per §0.3 |

### 1.1 "Stale" often means "already landed under another name"

Before proposing deletion of an unmerged branch, check whether its *content* is
on the integration branch — squash merges and successor branches both break
ancestry. Grep for a distinctive string or filename from the diff:

```bash
git diff --stat origin/dev...origin/$b        # what it claims to add
git ls-tree -r --name-only origin/dev | grep <its new file>
git show origin/dev:<file> | grep -F "<distinctive line>"
```

Report *superseded* vs *genuinely unlanded* separately. Only the second needs a
decision about the work itself.

## 2. Worktrees

Usually the real story — worktrees pin branches, so branch cleanup stalls until
they are resolved.

```bash
git worktree list --porcelain | awk '/^worktree /{w=$2} /^branch /{print w" "$2}' \
| while read w b; do
    br=${b#refs/heads/}
    dirty=$(git -C "$w" status --porcelain --ignored=matching 2>/dev/null | wc -l)
    own=$(git rev-list --count origin/dev..$br 2>/dev/null)
    git merge-base --is-ancestor "$br" origin/dev 2>/dev/null && m=MERGED || m=open
    echo "$m own_commits=$own dirty=$dirty $br <- $w"
  done | sort
```

**The dangerous quadrant is merged + dirty**: the branch reads "safe to delete"
while the directory holds the only copy of live work. Never remove one; report
it so the user can commit or stash first.

`merged + own_commits=0` is §0.3 — freshly cut, leave alone.

## 3. Dependency Health

```bash
npm outdated
npm audit --audit-level=moderate
gh pr list --state open --json headRefName --jq '.[].headRefName' | grep -i depend
```

- Check for open Dependabot PRs first — the outdated list is usually already handled
- `MISSING` in `npm outdated` for installed packages means `node_modules/.package-lock.json`
  is absent, not that packages are gone. `npm ci` restores the metadata
- Report majors vs minors separately

## 4. Dead Code & Unused Exports

```bash
npx knip --no-exit-code 2>/dev/null || echo "knip unavailable"
```

If knip is not a devDependency and the repo has no knip config, it is not part
of this project's toolchain. **Report it as not-runnable and move on** — adding
a config is scope creep on a maintenance pass. Known to fail loading
`playwright.config.ts`.

Never auto-delete. Present findings.

## 5. Stale TODOs

```bash
grep -rn "TODO\|FIXME\|HACK\|XXX" src/ --include="*.ts" --include="*.tsx"
```

Flag anything older than 60 days via `git blame`. Ask: resolve, ticket, or remove.

## 6. Instruction-File Audit

```bash
# Referenced paths that no longer resolve
grep -ohE '`[a-zA-Z0-9_./-]+\.(ts|tsx|md|sql|sh|yml)`' CLAUDE.md AGENTS.md | tr -d '`' | sort -u

# Env vars read in code but documented nowhere
grep -rhoE 'env\.get\("[A-Z][A-Z0-9_]+"\)' <functions dir> | sed 's/.*"\(.*\)".*/\1/' | sort -u
```

Relative shorthand (`chat/index.ts`) is normal, not a defect — resolve by
basename before reporting a break. Check prose mentions in sibling docs before
calling an env var undocumented.

## 7. Memory Pruning

```bash
M=~/.claude/projects/<slug>/memory
cd "$M"
for f in *.md; do [ "$f" = MEMORY.md ] && continue; grep -q "($f)" MEMORY.md || echo "ORPHAN: $f"; done
grep -o '](\([^)]*\.md\))' MEMORY.md | sed 's/](//;s/)//' | while read f; do [ -f "$f" ] || echo "DANGLING: $f"; done
grep -o '\[\[[a-z0-9_]*\]\]' *.md | sort -u   # wikilink targets
```

An orphan file is **not automatically stale** — compare dates and content
against the file that supposedly supersedes it. Newer orphan content gets folded
into the consolidated file, not deleted. Repair dangling wikilinks to real
targets while you are there.

## 8. Untracked Files

```bash
git status --short
git status --short --ignored=matching | head -40   # what the first command hides
```

Decide: commit, gitignore, or leave. Watch for research/analytics output holding
user data — the rule is usually "commit the script, ignore the output", and the
ignore rule must be verified with `git check-ignore -v <a real output file>`
rather than assumed.

## Output Format

| Area | Status | Action Needed |
|------|--------|---------------|
| Branches | N merged (yours), M stale | Delete merged; separate superseded from unlanded |
| Worktrees | N total, M merged-but-dirty | ⚠️ uncommitted work at risk — list, don't remove |
| Dependencies | N outdated, 0 vulns | Check open bot PRs first |
| Dead code | tool not in toolchain | Skipped, not configured |
| TODOs | N stale | Resolve, ticket, or remove |
| Instruction files | N env vars undocumented | Needs a branch |
| Memory | 1 orphan, newer than its consolidation | Folded in, not deleted |
| Untracked | agent scratch dir | Another session's output — leave |

Lead with anything at risk of loss. A clean sweep that destroys one unsaved plan
is a failed run.
