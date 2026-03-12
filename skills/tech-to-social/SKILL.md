---
name: tech-to-social
description: Translate technical work (commits, PRs, design decisions, bug fixes, architecture changes, benchmarks, refactors) into engaging LinkedIn posts. Use when the user wants to share technical achievements, lessons learned, or project milestones on social media. Triggers on requests like "write a LinkedIn post about...", "turn this into a social post", "help me share this on LinkedIn", "create a post about what I built", or "write up this technical work for social media".
---

# Tech to Social

Transform technical work into compelling LinkedIn posts. Generate 2-3 draft variations per request, and plan multi-post series for larger technical efforts.

## Workflow

1. **Gather source material** — Read the technical input (commits, PRs, code, docs, or user description)
2. **Extract the story** — Identify the human-interesting angle (see "Finding the Angle" below)
3. **Select tone** — Match tone to content type (see "Tone Selection")
4. **Draft 2-3 variations** — Each with a different hook/angle
5. **Add metadata** — Suggest hashtags, image ideas, and posting notes
6. **Plan series** (if applicable) — Break large work into a multi-post arc

## Finding the Angle

Technical work contains hidden stories. Extract them by asking:

- **What surprised you?** Unexpected results, counterintuitive solutions, wrong assumptions
- **What was the before/after?** Performance gains, code reduction, reliability improvements
- **What did you learn?** Transferable lessons, patterns, anti-patterns
- **What would you tell a colleague?** The water-cooler version of the story
- **What almost went wrong?** Near-misses, debugging journeys, pivots

Map source material to angles:

| Source | Best angles |
|--------|------------|
| Bug fix | The debugging journey, the surprising root cause, the lesson |
| New feature | The problem it solves, the design decision, the result |
| Refactor | Before/after contrast, why it was necessary, the measurable improvement |
| Performance work | Specific numbers, the investigation process, what you tried first |
| Architecture decision | The trade-offs considered, why you chose what you chose |
| Benchmark results | Surprising comparisons, practical implications |
| Design doc | The problem framing, what alternatives you rejected and why |

## Tone Selection

Choose tone based on content. Default to the best fit; user can override.

- **Storytelling**: For debugging journeys, project retrospectives, career moments
- **Educational**: For patterns, best practices, comparisons, how-we-solved-X
- **Achievement**: For launches, metrics, milestones, before/after results
- **Reflective**: For lessons learned, mistakes, things you'd do differently

## Output Format

For each request, produce:

```
## Draft 1: [Angle name] ([Tone])

[Full post text, ready to copy-paste]

---

## Draft 2: [Angle name] ([Tone])

[Full post text, ready to copy-paste]

---

## Draft 3: [Angle name] ([Tone])

[Full post text, ready to copy-paste]

---

## Posting Notes
- **Suggested hashtags**: [3-5 hashtags]
- **Image suggestion**: [What visual would complement this post]
- **Best time to post**: [General guidance if relevant]
- **Link placement**: [Put links in first comment, not post body]
```

## Series Planning

For large technical efforts (rewrites, multi-week projects, system designs), plan a series:

```
## Series Plan: [Series Title]

**Arc**: [1-sentence narrative thread connecting all posts]
**Cadence**: [Suggested posting schedule]

### Post 1: [Title] — [Format: Story/Listicle/Show-and-Tell]
[2-sentence summary of this post's focus]

### Post 2: [Title] — [Format]
[2-sentence summary]

[... more posts ...]

### Series Hashtag Strategy
[Consistent hashtags across the series + post-specific ones]
```

Ask the user if they want you to draft all posts in the series or start with the first one.

## Quality Checklist

Before presenting drafts, verify each post:

- [ ] Hook (first 2 lines) creates curiosity or states a surprising fact
- [ ] Contains at least one specific number, metric, or concrete detail
- [ ] No corporate buzzwords or AI-sounding filler phrases
- [ ] Under 3,000 characters
- [ ] Ends with something the reader can use or think about
- [ ] No external links in post body (suggest first-comment placement)
- [ ] 3-5 hashtags at the end

## Platform Reference

Read [references/linkedin-guide.md](references/linkedin-guide.md) for:
- Character limits and formatting constraints
- Hook pattern examples (counterintuitive, specific number, before/after, etc.)
- Post structure templates (story arc, listicle, show-and-tell)
- Tone calibration (do's and don'ts)
- Hashtag strategy by category
- Series planning guidelines

## Examples

**Input**: "We added database indexes and got 10-14x speedup on our benchmark queries"

**Draft 1 (Achievement)**:
```
We cut our benchmark runtime from weeks to days.

The fix? Three database indexes.

Our compression benchmarking system processes thousands of algorithm/file combinations. As the dataset grew to 1.7GB, skip-existing checks became the bottleneck — full table scans on every query.

Three B-tree indexes later:
- Query time: O(n) to O(log n)
- Benchmark runtime: 10-14x faster
- Risk: Near zero (SQL DDL only, no code changes)

We intentionally skipped connection pooling and query batching. Indexes delivered 90% of the benefit with 10% of the risk.

Sometimes the simplest fix is the right one.

#DatabaseOptimization #Performance #SoftwareEngineering #Python #BuildInPublic
```

**Draft 2 (Educational)**:
```
Before you add caching, connection pooling, or query batching — check your indexes.

We had a 1.7GB SQLite database slowing our compression benchmarks to a crawl. The instinct was to add complexity: batch queries, pool connections, refactor the pipeline.

Instead, we added 3 indexes. Total implementation: pure SQL DDL. Zero code changes.

The result? 10-14x speedup.

Here's the lesson I keep re-learning:

Measure first. The bottleneck is rarely where you think.
Start with the lowest-risk, highest-impact fix.
Complexity you don't add can't break.

What's a time you solved a performance problem with something embarrassingly simple?

#Performance #DatabaseDesign #SoftwareEngineering #Optimization
```
