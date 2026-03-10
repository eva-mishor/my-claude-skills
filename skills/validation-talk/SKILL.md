---
name: validation-talk
description: Use when creating interview questionnaires to validate assumptions, customer discovery, or problem-solution fit. Triggers on Mom Test, JTBD interviews, problem discovery, lean validation.
---

# Validation Talk

Interview questionnaires that produce go/kill signals. Mom Test (past behavior, never pitch) + JTBD + Sean Ellis PMF.

**Every question maps to an assumption with a quantified kill threshold. No mapping = cut it.**

## Process

### 1. Extract Assumptions

From the business plan/pitch, list every assumption with: **ID**, **assumption text**, **criticality** (Fatal=pivot, High=redesign, Medium=signal only), **kill threshold** (e.g., "<30% express active pain").

### 2. Design Questions (~25 total, 6-10 sections)

**Funnel order** — never violate:
```
Context/Profile → Current Behavior → Pain → Capabilities → Model Fit → Commitment
```
Pain before fees. Always. Commitment section always last.

### 3. Mom Test Discipline

| Rule | Do | Don't |
|---|---|---|
| Past behavior | "Walk me through your last sale" | "Would you use a platform that..." |
| Specific stories | "Tell me about last time you threw away produce" | "Do you ever have waste?" |
| Facts & numbers | "How much per kilo?" | "Are your margins good?" |
| No pitching | Never describe your solution | "We're building X, would you?" |
| Follow emotions | Dig deeper on frustration/excitement | Move to next scripted question |

### 4. Per-Question Metadata

| Field | Content |
|---|---|
| Assumption | Which assumption IDs this tests |
| Good/Bad signal | Observable (not "seems interested" — "names dollar amounts") |
| Disqualify if | Wrong segment entirely |
| Follow-up | Probe for ambiguous signals |
| Score | specific story=5, vague=3, none=1 |
| Mom Test note | Risk of hypothetical territory |

### 5. Scoring Framework

**Per-interview:** 5-7 dimensions matching assumption clusters, 60% pass threshold per dimension.

**4-tier classification:**

| Tier | Action |
|---|---|
| Hot (top 25%) | Recruit for pilot |
| Warm (50-75%) | Follow up |
| Cold (25-50%) | Monitor only |
| Disqualified (<25%) | Wrong segment |

**Commitment signals:** referral+intro / product commitment (strong), time commitment (medium), vague agreement (weak — ignore).

### 6. Aggregate Thresholds (across 20-30 interviews)

Fatal: 30%+ showing pain. Tech/capability: 50%+. Commitment: 20%+.

### 7. Kill Signals

5 hard-stop criteria: "If [metric] crosses [threshold], [component] breaks." Any ONE triggers pivot.

### 8. Bilingual (if applicable)

Spoken language first (casual/colloquial), translation in parentheses. Metadata in analysis language.

## Output Structure

Single markdown: protocol → questions w/ metadata → scoring + tiers → aggregate thresholds → kill signals → logistics → scoring sheet.

## Common Mistakes

| Mistake | Fix |
|---|---|
| "Would you use X?" | "Have you tried to solve X? What happened?" |
| Fees before pain | Business model after pain |
| No kill thresholds | Fatal/high assumptions need quantified kill |
| Generic signals | "names dollar amounts" not "seems interested" |
| >30 questions | ~25 max, each maps to assumption |
| No commitment section | End with time/referral/product asks |
