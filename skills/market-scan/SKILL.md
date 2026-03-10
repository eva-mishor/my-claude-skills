---
name: market-scan
description: Use when researching competitive landscape, market sizing, or existing solutions for a product idea. Triggers on competitor analysis, market research, "who else is building this", landscape scan, competitive intel.
---

# Market Scan

Structured competitive and market research using web search. Produces a decision-ready landscape report, not a narrative essay.

**Every finding must have a source. No source = cut it.**

## Process

### 1. Define Search Targets

From the idea/brief, extract:
- **Core problem** being solved
- **Target user** description
- **Solution approach** (what the product does)
- **Category** (what shelf it sits on)

### 2. Run Multi-Angle Search Queries

Run WebSearch with **all five angles** — not just the obvious one:

| Angle | Query Pattern | Example |
|---|---|---|
| **Solution-based** | "[what it does] app/tool/platform" | "skincare shelf scanner app" |
| **Problem-based** | "[user problem] solution/help" | "how to build skincare routine from products I own" |
| **Audience-based** | "[target user] + [category] tools" | "skincare routine builder for beginners" |
| **Funding-based** | "[category] startup funding/raised" | "skincare AI startup funding 2024 2025" |
| **Graveyard-based** | "[category] app shut down/failed/pivoted" | "skincare app failed shut down" |

Also check:
- **App stores** — search iOS/Android app stores for direct competitors
- **Product Hunt** — recent launches in the category
- **Reddit/forums** — how users currently solve the problem DIY
- **Google Trends** — search volume trajectory for key terms

### 3. Classify Competitors

Sort every finding into four buckets:

| Bucket | Definition | What to capture |
|---|---|---|
| **Direct** | Same problem, same approach | Features, pricing, positioning, traction signals (downloads, reviews, funding) |
| **Indirect** | Same problem, different approach | What users do today (manual, workarounds, communities) |
| **Adjacent** | Different problem, could pivot/expand here | Capability, incentive to enter, strategic fit |
| **Dead** | Tried this, failed or pivoted | What they built, why they died (if knowable) |

### 4. Analyze Pricing Landscape

For each direct/adjacent competitor with a product:
- Free / freemium / paid?
- Price point and billing model
- What's behind the paywall?
- What's the free hook?

### 5. Assess Structural Threats

For each adjacent player, answer:
- **Capability:** Could they build this? (technical ability)
- **Incentive:** Would they? (does it align with their business model?)
- **Speed:** How fast? (months vs. years)

Key insight: capability without incentive is not a threat. If building your product cannibalizes their revenue, they won't do it.

### 6. Identify the Gap

From all findings, articulate:
- What no one is doing (or doing poorly)
- Why it hasn't been done (incentive misalignment? timing? tech not ready?)
- Whether the gap is defensible or trivially closable

## Output: Landscape Report

```
MARKET SCAN — [Product Name]
═══════════════════════════════════════════════

SEARCH SUMMARY: [X] queries across [Y] angles, [date]

DIRECT COMPETITORS:
| Name | What they do | Pricing | Traction | Gap vs. you |
|------|-------------|---------|----------|-------------|

INDIRECT COMPETITORS (current behaviors):
| Behavior | Where | Friction | Scale |
|----------|-------|----------|-------|

ADJACENT PLAYERS:
| Name | Capability | Incentive | Threat level |
|------|-----------|-----------|-------------|

DEAD/PIVOTED:
| Name | What they tried | Why it died |
|------|----------------|-------------|

PRICING LANDSCAPE:
[Summary of how competitors monetize]

MARKET SIGNALS:
• Market size: [TAM/SAM with sources]
• Growth: [CAGR or trend direction]
• Google Trends: [rising/flat/declining for key terms]
• Community size: [Reddit, forums, etc.]

GAP ANALYSIS:
• White space: [what nobody owns]
• Why it's open: [incentive/timing/tech explanation]
• Defensibility: [how closable is the gap?]

VERDICT:
• Crowded / Emerging / White space
• Biggest threat: [who and why]
• Timing: [early / right time / late]

═══════════════════════════════════════════════
```

## Common Mistakes

| Mistake | Fix |
|---|---|
| One search query, declare "no competitors" | All five angles minimum |
| Miss indirect competitors | People solve problems today — find how |
| Ignore dead competitors | Failures teach more than successes |
| "Big company could build this" = threat | Check incentive, not just capability |
| Narrative output | Use the structured report — it's for decisions |
| No sources | Every claim needs a URL or verifiable reference |
| Confuse "has the feature" with "owns the positioning" | A feature buried in a larger app ≠ a focused competitor |
