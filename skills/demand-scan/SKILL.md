---
name: demand-scan
description: Use when you need to validate demand signals for a product idea by researching specific competitors, user complaints, existing workarounds, and DIY behavior patterns. Complements market-scan (broad landscape) with targeted depth. Triggers on "is there demand for this", "what do users complain about", "how do people solve this today", "validate the demand", "dig into competitor X", "find pain signals".
---

# Demand Scan

Targeted web research to find evidence that people already want what you're building — or evidence that they don't. Focuses on **demand signals**, not landscape breadth.

**Pairs with `market-scan`:** market-scan finds WHO is in the space. Demand-scan finds WHETHER users are actively seeking what you'd offer and WHERE existing solutions fall short.

**Every finding must have a source. No source = cut it.**

## When to Use

- After a `market-scan` identifies a closest competitor — deep-dive on their weaknesses
- When you need to prove/disprove demand before building
- When the user says "is anyone actually asking for this?"
- When you need to validate a 10x claim with evidence, not just intuition

## Process

### 1. Define What You're Looking For

From the idea/brief and any prior market scan, extract:
- **The specific value prop** you're testing demand for
- **The closest competitor(s)** to deep-dive on
- **The output/artifact** the user would get (what does "solved" look like?)

### 2. Competitor Deep-Dive

For each close competitor (max 2-3), run targeted searches:

| Angle | Query Pattern | What you're looking for |
|---|---|---|
| **App store reviews** | "[competitor] app reviews complaints" | Pain points, frustrations, what's missing |
| **Paywall frustration** | "[competitor] paywall OR subscription OR expensive OR free" | Pricing friction = demand behind a wall |
| **Reddit/forum mentions** | "[competitor] reddit review OR alternative" | Unfiltered user opinions, switching intent |
| **TikTok/social proof** | "[competitor] tiktok OR review honest" | Real usage patterns, confusion signals |
| **"Alternative to"** | "[competitor] alternative" | People actively looking for something better |

**What to extract from reviews:**
- Specific feature complaints (buried, confusing, broken)
- Paywall resentment (= proven demand, bad monetization)
- "I wish it could..." statements (= unmet needs)
- "I switched to..." statements (= competitor movement)

### 3. DIY Behavior Hunt

Search for evidence that people are already solving this problem with workarounds:

| Signal Type | Where to Search | Query Pattern |
|---|---|---|
| **Manual workarounds** | Reddit, forums | "[problem] how to DIY OR manually OR spreadsheet" |
| **Paid workarounds** | Etsy, Gumroad, marketplaces | "[output format] template OR printable OR guide" |
| **Community help** | Reddit, Facebook groups, Discord | "[problem] help OR advice OR "what should I"" |
| **Professional services** | Google | "[problem] consultant OR coach OR service" |

**Key insight:** If people are paying for templates, asking strangers for help, or hiring professionals — the demand is real. The question becomes whether your solution is better than the workaround.

### 4. Output Demand Validation

Search for evidence that the specific OUTPUT/ARTIFACT your product creates is something people want:

- Do people search for it? (Google Trends, search suggestions)
- Do people make it manually? (Etsy, Pinterest, templates)
- Do people ask for it? (Reddit, forums, Q&A sites)
- Do people pay for a worse version? (existing products, services)

### 5. Synthesize Signals

Classify everything you found:

| Signal | Strength | Evidence |
|---|---|---|
| **Strong demand** | People paying for workarounds | [source] |
| **Moderate demand** | People asking but not paying | [source] |
| **Weak demand** | Related interest but not direct | [source] |
| **Counter-signal** | Evidence against demand | [source] |

## Output: Demand Signal Report

```
DEMAND SCAN — [Product/Feature]
═══════════════════════════════════════════════

WHAT WE'RE VALIDATING:
[The specific value prop or 10x claim being tested]

COMPETITOR DEEP-DIVE:
┌────────────┬───────────────────────────┬──────────────┐
│ Competitor │ Key weakness found        │ Source       │
├────────────┼───────────────────────────┼──────────────┤
│            │                           │              │
└────────────┴───────────────────────────┴──────────────┘

USER COMPLAINTS (from reviews/forums):
• [Complaint] — [source]
• [Complaint] — [source]
• "I wish..." statements: [list with sources]

DIY WORKAROUNDS FOUND:
• [Workaround] — [where, how many people, paid/free] — [source]

OUTPUT DEMAND:
• People searching for this output: [Y/N, evidence]
• People making it manually: [Y/N, evidence]
• People paying for worse version: [Y/N, evidence]

SIGNAL STRENGTH:
┌──────────────────┬──────────┬──────────────────────────┐
│ Signal           │ Strength │ Evidence                 │
├──────────────────┼──────────┼──────────────────────────┤
│                  │          │                          │
└──────────────────┴──────────┴──────────────────────────┘

VERDICT:
• Demand: Proven / Likely / Uncertain / Weak
• Willingness to pay: [evidence for/against]
• 10x claim: Supported / Partial / Unsupported
• Key risk: [what could still disprove demand]

═══════════════════════════════════════════════
```

## Common Mistakes

| Mistake | Fix |
|---|---|
| Searching only for positive signals | Actively search for counter-evidence too |
| "No complaints found" = good | Could mean no one uses it enough to complain |
| Confusing interest with willingness to pay | Upvotes ≠ credit cards. Look for payment signals |
| Only checking one platform | Reddit + app stores + marketplaces + social = full picture |
| Ignoring DIY workarounds | Manual solutions are the strongest demand signal |
| Treating competitor weakness as your strength | Their weakness only matters if users care about it |
