---
name: idea-to-product
description: Guided process for moving a B2C app idea from raw concept to revenue-generating MVP. Walks the user through 6 phases interactively — asking questions, challenging assumptions, producing deliverables, and enforcing gates before advancing. Triggers on "idea to product", "I have an app idea", "help me validate my idea", "take my idea to MVP".
---

# Idea to Product — Guided Process

An interactive, phase-gated process that walks the user from raw idea to revenue-generating B2C MVP. You (Claude) are the guide — asking questions, applying expert frameworks, challenging weak thinking, producing deliverables, and enforcing gates.

## When to Use

**Triggers:**
- "Idea to product"
- "I have an app idea"
- "Help me validate my idea"
- "Take my idea to MVP"
- "I want to build [app concept]"

## How This Works

**You are NOT a lecturer.** You are a coach running the user through a structured process. Each phase:

1. **Announce** the phase, its purpose, and which expert frameworks you're applying
2. **Ask questions** one or two at a time — don't dump all questions at once
3. **Listen and challenge** — push back on vague answers, surface assumptions, spot wishful thinking
4. **Produce the deliverable** when you have enough signal from the conversation
5. **Evaluate the gate** honestly — if it doesn't pass, say so and explain what's missing
6. **Only advance** when the user confirms the gate or consciously decides to proceed despite gaps

**Pacing:** One phase per session is normal. Don't rush. The user can say "let's continue" to pick up where they left off.

**Tone:** Direct, Socratic, no fluff. Challenge like a good advisor — not harsh, not soft. Like the mastermind experts would.

**Cross-session continuity:** If the user returns and says "let's continue idea-to-product", check for previous deliverables and pick up at the next incomplete phase.

---

## Phase Overview

Show this when starting:

```
IDEA TO PRODUCT — 6 PHASES
═══════════════════════════════════════════════

Phase 1: CAPTURE & CLARIFY       [1-2 days]    → One-page brief
Phase 2: VALIDATE THE PAIN       [1-2 weeks]   → Validation report
Phase 3: POSITION & DIFFERENTIATE [2-3 days]   → Positioning doc
Phase 4: DESIGN THE BUSINESS MODEL [2-3 days]  → Business model one-pager
Phase 5: BUILD THE MVP            [2-4 weeks]  → MVP spec + metrics
Phase 6: LAUNCH & FIRST REVENUE   [1-2 weeks]  → Launch plan + PMF signal

═══════════════════════════════════════════════
~6-10 weeks from idea to revenue signal.
Each phase has a gate. No gate = no advance.
```

Then ask: **"What's the idea? Give me whatever you have — a sentence, a paragraph, a rant. Raw is fine."**

---

## Phase 1: CAPTURE & CLARIFY

> **Goal:** Turn a vague idea into a testable hypothesis.
> **Expert frameworks:** Peter Thiel (contrarian thinking), Tim Ferriss (80/20, fear-setting), Cal Newport (focus test)
> **Integration:** Use the `market-scan` skill when answering Thiel's competitive questions ("Is anyone else building this?")
> **Output:** One-page brief

### How to Guide This Phase

**Step 1: Get the raw idea.**
Let them talk. Don't interrupt. Then reflect back what you heard in one sentence. Ask: "Is that right, or am I missing something?"

**Step 2: Sharpen it into the idea sentence.**
Guide them to fill in: `[Target user] can [do what] so that [outcome], which is currently impossible/hard because [why]`.
If they can't fill this in, the idea isn't clear yet. Help them iterate.

**Step 3: Apply Thiel's questions (one at a time).**
Ask these conversationally, not as a checklist:
- "What do you believe about this space that most people would disagree with?"
- "Is anyone else building this? If not, why do you think that is?"
- "Is this 10x better than what exists, or 10% better? Be honest."

Push back if the answers are weak. "That sounds like an incremental improvement, not a contrarian insight. What makes this fundamentally different?"

**Step 4: Apply Ferriss's filter.**
- "If this were easy, what would it look like?"
- "What's the scariest part of pursuing this? What's the actual worst case?"
- "What's the minimum version that still solves the core problem?"

**Step 5: Apply Newport's focus test.**
- "Can you build the core value yourself in focused work sessions, or does this require you to become 5 different experts?"
- "What will you stop doing to make room for this?"

**Step 6: Spot-check for common traps.**
If you detect any of these, call them out directly:
- **Solution looking for a problem**: "You've described what the app does, but who is in pain right now without it?"
- **Too broad**: "You said 'everyone' or 'millennials' — who specifically? Give me one person."
- **No contrarian edge**: "This sounds like something a big company could trivially add as a feature. What stops them?"
- **Passion project disguised as a business**: "Would you pay for this? Would a stranger?"

### Generate Deliverable: One-Page Brief

When you have enough signal, produce and **save** the brief to `docs/idea-to-product/<project-name>-one-page-brief.md`. Include the 10x argument and market context alongside the brief template.

Template:

```
ONE-PAGE BRIEF
═══════════════════════════════════════════════

IDEA (one sentence):
[The sharpened idea sentence]

TARGET USER:
[Specific person description — not a demographic]

CORE PAIN POINT (hypothesis — unvalidated):
[What hurts, for whom, and when]

WHY NOW:
[Market timing, technology shift, cultural change]

WHY YOU:
[Your unique advantage — insight, skill, access]

CONTRARIAN INSIGHT:
[What you see that others don't]

KILL CRITERIA:
[What evidence would make you abandon this]

═══════════════════════════════════════════════
```

### Evaluate Gate

Check these honestly. Tell the user which pass and which don't:

- [ ] Idea can be explained in one sentence without jargon
- [ ] Target user is specific enough to find and talk to
- [ ] There's a contrarian insight, not just an incremental improvement
- [ ] Kill criteria are defined (if you can't define what kills it, you'll never kill it)

**If gate fails:** Tell the user which items are weak. Work on those specific items. Don't move on.

**If gate passes:** "Phase 1 complete. Your idea is clear enough to test. Ready for Phase 2 — Validate the Pain? This is where the idea meets reality."

---

## Phase 2: VALIDATE THE PAIN

> **Goal:** Prove the pain exists before building anything.
> **Expert frameworks:** Eric Ries (lean validation), Clayton Christensen (JTBD), Rob Fitzpatrick (Mom Test), Daniel Kahneman (bias-proofing)
> **Output:** Validation report
> **Integration:** Use the `validation-talk` skill to generate the interview questionnaire

### How to Guide This Phase

**Step 1: Extract assumptions.**
Review the one-page brief from Phase 1. Ask:
- "What has to be true for this to work?"
- List every assumption together. Then rank by: (a) how fatal if wrong, (b) how uncertain.
- Fatal + uncertain = your validation targets.

Present assumptions in a table:
```
| ID | Assumption | Criticality | Certainty | Validate? |
|----|-----------|-------------|-----------|-----------|
| A1 | [text]    | Fatal       | Low       | YES       |
| A2 | [text]    | High        | Medium    | YES       |
| A3 | [text]    | Medium      | High      | No        |
```

**Step 2: Assess validation approach.**

The traditional playbook says "interview 20-30 people before building." That was written when building cost months and thousands of dollars. In the AI era, building a testable MVP can cost less — in time, money, and effort — than finding 20 qualified strangers to interview.

**The principle hasn't changed: validate before you invest heavily. But what counts as "validation" has expanded.**

Evaluate three factors:
- **Build cost vs. interview cost:** If you can ship an MVP in a weekend, the product itself IS the experiment. If the MVP takes months, interview first.
- **Founder domain expertise:** If the founder is already the person users come to for help (they're productizing their own expertise), they carry signal that replaces early interviews.
- **Online signal availability:** If the target audience actively discusses the problem online (Reddit, YouTube, forums, app reviews), mine that data — it's unsolicited Mom Test at scale.

Choose one of:

| Approach | When to use | Validation comes from |
|----------|------------|----------------------|
| **Full interview round** (20-30) | Build cost is high, problem space poorly understood, founder is NOT the target user | Conversations before building |
| **Hybrid** (recommended for most AI-era B2C) | Moderate build cost, some online signal exists | Online research + 5-7 conversations + ship-and-measure |
| **Build-first validation** | Build cost is very low (days), founder has strong domain expertise, rich online signal already validates core pain | Online research to confirm pain → build MVP → measure real behavior (analytics, conversion, retention) → 5-7 conversations AFTER launch to understand the "why" behind the data |

**Build-first is NOT "skip validation."** It's running the experiment with a live product instead of hypothetical questions. The discipline is the same: define assumptions, set kill thresholds, measure against them. The difference is you're measuring behavior, not self-reported intent. People lie in interviews. Analytics don't.

**Build-first requirements:**
- Kill criteria defined BEFORE shipping (from Phase 1)
- Analytics baked into the MVP from day one
- Time-boxed: set a deadline for go/kill decision (e.g., 4-8 weeks)
- Investment-capped: set a maximum spend (API costs, hosting, ads)
- Post-launch conversations (5-7) to understand WHY users behave the way they do — what the data shows but can't explain

**How to manage build-first validation well:** See the "Ship First, Compound Later" section below Phase 2 for the full playbook — shipping discipline, 30-day cadence, concierge MVP option, landing page pre-filter, and the critical distinction between validating pain vs. validating the business.

**Step 3: Online research track.**
Mine existing conversations for assumption evidence. Use the `demand-scan` skill to systematically search:
- Reddit communities, YouTube comments, TikTok comments
- App store reviews of adjacent products
- Etsy/marketplace reviews for DIY workarounds
- Forum threads, blog comments

This is unsolicited Mom Test data — people describing real pain without knowing they're being interviewed. Map findings to assumptions. Note: you can't ask follow-ups, and you're sampling self-selected posters.

**Step 4: Quick conversations track (5-7 interviews).**
Use the `validation-talk` skill to generate a slim questionnaire focused on gaps online research can't fill:
- Premium tier willingness
- Input method preferences
- Trust signals specific to AI
- Anything requiring follow-up probing

Save questionnaire to `docs/idea-to-product/<project-name>-validation-questionnaire.md`.

**Step 5: Tech validation track.**
If the product has tech-risk assumptions (e.g., AI accuracy, API feasibility), test those directly. No interviews needed — just build and measure.

**Step 5b: Commodity check.**
Ask directly: "Can a general-purpose AI (ChatGPT, Gemini, etc.) roughly replicate your core value today?" If yes, flag this as an **AI-commodity product** — the core intelligence is free and available to anyone. This isn't automatically a kill signal, but it fundamentally changes the strategy. See the AI-Commodity Product Pattern below.

**Step 6: Coach on JTBD framing (Christensen).**
Whether interviewing or not, nail the JTBD:
- "What 'job' is the user hiring a solution for?"
- "What do they currently 'hire' to do this job?" (competitors = behaviors, not just products)
- "What would make them 'fire' their current solution?"
- "When exactly does this job arise? What's the trigger moment?"

If conversations are skipped, derive the JTBD from online research evidence — Reddit posts, forum threads, and app reviews contain unsolicited JTBD language. Look for trigger moments ("every morning I stare at..."), hiring/firing language ("I switched to...", "I gave up on..."), and outcome descriptions ("I just want...").

**Step 7: Warn about biases (Kahneman).**
Be direct. Adapt warnings to the validation approach used:

Always:
- "You will hear what you want to hear. That's confirmation bias."
- "If the data says kill, you kill it. Sunk cost is not a reason to continue."

If conversations conducted:
- "Two excited interviews is not validation. You need patterns across multiple conversations."
- "Have someone else read your notes."

If conversations skipped:
- "Online research has survivorship bias — you're sampling people who post publicly. Silent majority may not care enough to seek a solution."
- "You have NO depth signal on willingness to pay. The MVP must answer this — watch conversion data honestly."
- "No conversation data means you're flying on assumptions about trust, pricing, and UX preferences. Be honest with yourself when reading post-launch data."

If AI-commodity product (Step 5b flagged):
- "The experience gap narrows every month as free tools improve. Your differentiator today can be a default feature tomorrow."
- "You may overestimate how much people care about the experience layer vs. 'good enough for free.'"

**Step 8: Score the results.**
Combine evidence from all available tracks. Online research provides volume. Conversations provide depth. Tech validation provides feasibility.

**If conversations were conducted** — apply aggregate thresholds:
- Fatal assumptions: 30%+ showing pain = pass
- Tech/capability: 50%+ = pass
- Commitment signals: 20%+ = pass

**If online-research-only** — use signal strength ratings instead of percentages (you can't calculate "30% of Reddit posts show pain"):
- Fatal assumptions: Strong signal (multiple independent sources, unsolicited complaints, active workaround behavior) = pass
- Tech/capability: Confirmed working through direct testing = pass
- Commitment signals: Evidence of payment for adjacent/inferior solutions (Etsy templates, paid apps, professional services) = pass. Absence of payment signals = open risk, must be tested post-launch

### Generate Deliverable: Validation Report

Save to `docs/idea-to-product/<project-name>-validation-report.md`.

```
VALIDATION REPORT
═══════════════════════════════════════════════

VALIDATION APPROACH: [Full interview / Hybrid / Build-first]

EVIDENCE SOURCES:
• Online research: [X sources across Y platforms]
• Conversations: [X] conducted with [target user type]
• Product data: [if build-first: analytics from MVP]
• Tech validation: [if applicable: accuracy/feasibility results]

ASSUMPTION SCORECARD:
| ID | Assumption | Result | Evidence Source | Evidence |
|----|-----------|--------|----------------|----------|
| A1 | [text]    | ✅/❌/❓ | [online/conversation/product data] | [data] |

JTBD STATEMENT:
"When [situation], I want to [motivation], so I can [outcome]."

CURRENT ALTERNATIVES:
[What users do today and what they hate about it]

PAIN SCORE: [X]% vs. kill threshold [Y]%

[If build-first, add:]
PRODUCT VALIDATION METRICS:
• Users: [N] (organic / paid)
• Activation rate: [X]% (completed core action)
• Day-1 retention: [X]%
• Day-7 retention: [X]%
• Conversion to paid: [X]%
• Kill threshold: [defined in Phase 1]
• Time elapsed: [X] of [Y] weeks budgeted

DECISION: GO / KILL / PIVOT
Evidence: [why]

═══════════════════════════════════════════════
```

### Evaluate Gate

**For full interview or hybrid approach:**
- [ ] Sufficient evidence gathered (15+ interviews, or online research + 5-7 conversations)
- [ ] Fatal assumptions cleared kill thresholds (30%+ showing pain)
- [ ] JTBD articulated in one sentence
- [ ] Current alternatives and frustrations documented
- [ ] Go/Kill/Pivot decision made with evidence

**For build-first approach:**
- [ ] Online research confirms core pain exists (strong signal on fatal assumptions)
- [ ] Kill criteria defined with hard numbers (from Phase 1)
- [ ] Analytics plan ready (what to measure, what thresholds mean go/kill)
- [ ] Investment cap set (time + money)
- [ ] JTBD articulated in one sentence (from online research + domain expertise)
- [ ] Current alternatives documented
- [ ] Decision: proceed to build with post-launch validation checkpoint scheduled

For build-first, the gate is lighter — you're not proving everything upfront, you're confirming there's enough signal to justify the (low) cost of building. The REAL gate comes post-launch when you have product data. Schedule a validation checkpoint (e.g., 4 weeks after launch) to score the full assumption scorecard with real data.

**KILL GATE:** If fatal assumptions fail (in any approach), tell the user directly: "The data says this pain isn't strong enough. Your options: pivot the idea, pivot the audience, or stop. Building would be ignoring your own evidence."

**If gate passes:** "The pain is real. Phase 3 — let's figure out how to own this space."

---

## Ship First, Compound Later — The AI-Era Product Strategy

This section covers two interconnected realities of building products when AI makes the tech cheap:

1. **The build is no longer the hard part.** What used to take a team of eight engineers four months can now be prototyped by one person over a weekend. If the thing you're making can be reproduced by a motivated stranger with a credit card and an AI subscription, your tech is not your moat.
2. **Distribution and compounding advantages are everything.** Tech/distribution ratio has shifted from 90/10 to roughly 20/80. The product that wins isn't the one built first — it's the one that reaches the right people and gets harder to kill the longer it exists.

Sources: a16z ("momentum is the moat"), Pieter Levels (12-in-12 challenge, $3.1M/year solo), RevenueCat ("the #1 predictor of success is rate of iteration"), Elena Verna/Lovable ($200M ARR, "re-find PMF every 3 months"), Ben Yoskovitz ("AI did not kill Lean Startup — we're making the same mistakes faster").

### When to Apply

**Step 5b flagged this as an AI-commodity product** — a general-purpose AI can roughly replicate the core value. This pattern also applies broadly to any product where the build cost is low and the distance between "idea" and "functional product" has collapsed.

**This is NOT a kill signal.** It's a strategy shift. Cal AI (calorie counting from food photos — literally what ChatGPT does) succeeded purely on distribution. Cursor ($500M ARR) started as a thin wrapper around GPT/Claude. Perplexity ($9B valuation) used the OpenAI API to verify PMF first, calling it "the best decision they made."

But staying thin IS a kill signal. Jasper AI rose to $120M revenue at a $1.5B valuation, then collapsed to ~$55M when ChatGPT ate generic writing. 73 PDF chat wrappers launched the same week — the category died when ChatGPT added native PDF support. 90% of AI wrappers shut down within 18 months. 60-70% generate zero revenue.

The pattern is clear: **start thin to validate, then build depth to survive.**

### The Core Insight

When the intelligence is free, your product is an **experience layer**, not an intelligence layer. The value is in the package — not the brain.

The delta between "ask ChatGPT" and a dedicated product typically includes some combination of:

- **Visual output** — finished artifacts (images, guides, dashboards), not walls of text
- **Zero-effort UX** — input → answer, no prompt engineering, no setup
- **Trustworthy reasoning** — show the "why," not just the answer (transparency builds trust where the AI is a black box)
- **Persistence** — results saved, revisitable, updatable over time
- **Done-for-you** — the completed output that people currently create manually or buy blank templates for
- **Personalization context** — remembers user profile, preferences, history without re-explaining each time

Not all apply to every product. Identify which 2-3 are your primary differentiators and lead with those.

### Phase A: Ship the Experience Layer Fast (Days to Weeks)

The first version isn't the hard part anymore. Ship it to validate — the product IS the experiment.

**Why ship first:**
- Building a testable MVP can cost less than finding 20 qualified strangers to interview. One person with AI tools can prototype over a weekend.
- Real behavior beats hypothetical answers. People lie in interviews. Analytics don't. The ship IS the interview.
- Speed compounds: "Teams that win aren't the ones with a higher success rate — they're the ones who find out faster." (RevenueCat)

**How to ship first well:**
- Build the thinnest viable experience around the commodity capability
- Free tier delivers the core promise (same result ChatGPT gives, but packaged better)
- Paid tier adds depth the commodity can't match
- Instrument from day one — acquisition, activation, and the specific behavior you're validating
- Define kill criteria BEFORE shipping. Time-box it (4-8 weeks). Cap investment.

**The reversibility rule:** If the cost of being wrong is reversible and contained, move fast. If it's irreversible or erodes trust, slow down. (RevenueCat)

**Ship fast ≠ ship garbage.** Ship the minimum viable *complete* thing. One workflow that ends with a clear user outcome — not a feature set, a single path from input to value. If you can't describe it in one sentence, you're building too much.

**30-day post-launch cadence:**
- Week 1: Fix onboarding friction and obvious bugs. Watch where people drop off.
- Week 2: Improve activation — remove steps, clarify messaging. Are people completing the core action?
- Week 3: Look at retention. If not returning, why? This is when to do 5-7 user conversations — to understand the "why" behind the data.
- Week 4: Score your assumption scorecard with real data. Make the go/kill/pivot decision.

**Consider before building software:**
- **Concierge MVP:** Can you deliver the value manually for 5-10 users first? If they won't engage with free manual service, they won't use an automated version.
- **Landing page pre-filter:** A clear value prop + signup button tests demand with zero build cost. If nobody signs up, the message or problem isn't strong enough.

**Separate pain from business:** Free usage validates the pain. Conversion to paid validates the business. Don't conflate them. 1000 free users + 0 paying users = validated pain, invalidated business model. That's a pricing/positioning problem, not a kill signal.

**Don't optimize prematurely.** The MVP exists to answer ONE question: "Is this worth continuing?" Don't A/B test button colors. Don't optimize onboarding flows. Get signal on the core hypothesis first, then optimize.

### Phase B: Build the Moat While Live (Months 2-6)

The experience layer gets you in the door. It doesn't keep you alive. Feature moats last ~6 months before foundation models absorb them. You need advantages that compound — things that get harder to replicate the longer they exist.

**The diagnostic test:** "If a team with $50M cloned us tomorrow, what would they still not be able to replicate in 3 years?" Not "our culture" or "our vision" — those are non-answers. What specifically have you built, learned, or earned that requires time and cannot be purchased?

**Defensibility isn't a wall you build. It's a direction you compound in.**

The moat framework most founders know (network effects, switching costs, scale) describes what mature companies look like, not how they got there. Early-stage, focus on these compounding directions:

**1. Proprietary data that improves with use.**
Not data in the generic sense — structured feedback loops where every user interaction makes the product meaningfully better in a way competitors can't shortcut. Spotify's Discover Weekly works because of a decade of listening behavior, not the algorithm. You can copy the architecture; you cannot copy the training set. After 12-24 months of compounding, the gap becomes uncrossable. If your data doesn't compound, it doesn't defend.

**2. Trust at the infrastructure level.**
When you become embedded in how people make decisions or run their operations, you stop being a tool and start being a dependency. Prototypes are easy. Production-grade trust (reliability, auditability, consistency) is not, and no weekend hackathon can replicate it.

**3. Distribution that can't be copied with code.**
Distribution ≠ followers or views. Distribution is the consistency of spreading the right message across the right people. Tech/distribution ratio has shifted to roughly 20/80. Three effective channels:
- **Organic content** (everyday content + big launches — the combination compounds)
- **UGC** (users/creators talking about you — total awareness, not just your profile's reach)
- **Paid marketing** (most predictable, most cash-intensive, and gets more expensive daily)

Distribution is why Cal AI (food photo → calories, which ChatGPT does) captured real market share, and why Pieter Levels' micro-SaaS products survive despite being technically trivial to replicate.

**4. Community and brand independent of the product.**
Notion's template gallery is user-created, the ambassador program runs itself, and "Notion templates" is now a cottage industry. You can clone the editor; you can't clone the ecosystem of people who made it theirs.

**5. Specialized workflows and integrations.**
Glean integrates into Slack, Zendesk, Salesforce — switching costs compound. Once you're the system of record, displacement is extremely expensive. Multi-step domain-specific workflows that a general Q&A chatbot doesn't replicate.

**6. Progress tracking / longitudinal value.**
A stateless chat can't track your progress over time. Products that accumulate user history, show trends, and improve recommendations based on past behavior create value that resets to zero if the user leaves.

**Real examples — thin → deep transitions:**
- **Perplexity:** OpenAI API wrapper → proprietary models (Sonar, R1 1776) → Shopping Hub, Search API. $9B valuation.
- **Cursor:** Code completion wrapper → codebase-wide context via vector embeddings → platform with deep IDE integration. $500M ARR.
- **Notion AI:** GPT-4 writing assistant → workspace Q&A → autonomous agents (Notion 3.0). Revenue $300M → $500M.
- **GitHub Copilot:** Code completion (Codex wrapper) → agentic features across full SDLC → Copilot SDK for any app.

**Real examples — stayed thin, died:**
- **Jasper AI:** $120M → ~$55M revenue. ChatGPT ate generic writing. The category blurred beyond recognition.
- **PDF chat wrappers:** 73 clones, category died when ChatGPT added native PDF support.
- **Generic summarizers:** Integrated natively into Claude/GPT. Standalone market eliminated.
- Pattern: "Using GPT is not a moat. It's a feature."

### Moat Timeline

- **Month 1-2:** Ship thin, validate experience layer, measure WTP
- **Month 2-6:** Begin building compounding advantages (data flywheel, distribution, community)
- **Month 6-12:** Feature moats expire — if you haven't started compounding, the window is closing
- **Month 12-24:** Data/workflow moats become defensible if you started early
- **Ongoing:** Re-find PMF every ~3 months as the landscape shifts (Elena Verna / Lovable)

### How This Affects Downstream Phases

- **Phase 3 (Positioning):** Lead with the experience, not the AI. The one-liner should describe the output/experience, not the technology. "Photo your shelf. Get your routine." — not "AI-powered skincare analysis."
- **Phase 4 (Business Model):** Free tier must deliver real value (because ChatGPT is the free alternative). Paywall goes on depth and continuity, not on the core promise. The free experience IS your acquisition channel — users share it. Consider distribution strategy as part of the business model — distribution is 75-80% of success when tech is cheap.
- **Phase 5 (MVP):** Build Phase A only. Phase B features are explicitly NOT in the MVP. The MVP tests whether the experience layer alone justifies payment over the free commodity. Plan Phase B moat direction before shipping, but don't build it yet.
- **Phase 6 (Launch):** Position against the behavior ("stop prompting ChatGPT"), not against other apps. Your competitor is a free, general-purpose tool — your marketing must make the experience gap viscerally obvious. Distribution strategy (organic + UGC + paid) matters more than the launch itself.

### Kill Criteria Adjustment

Standard kill criteria apply, plus:
- If free-tier usage is high but conversion to paid is zero after 4+ weeks, the experience layer alone isn't enough. Either accelerate Phase B (build the moat) or pivot.
- Monitor whether general-purpose AI closes the experience gap. If ChatGPT adds persistence, visual outputs, or domain templates that match your UX, your window is closing — accelerate moat-building or kill.
- Apply the honest test: "Does someone's life or work get worse if this product disappears tomorrow?" If the honest answer is no, you don't have a company yet — you have a feature.

---

## Phase 3: POSITION & DIFFERENTIATE

> **Goal:** Define why you, why this, and for whom — in words users would actually use.
> **Expert frameworks:** Seth Godin (tribes, remarkability), Al Ries (positioning), Donald Miller (StoryBrand), April Dunford (Obviously Awesome)
> **Output:** Positioning document

### How to Guide This Phase

**Step 0: Commodity check (if flagged in Phase 2 Step 5b).**
If the product was flagged as an AI-commodity product, start here before defining category. The positioning must lead with the **experience**, not the intelligence. Reference the AI-Commodity Product Pattern above.

Ask: "Given that ChatGPT/general AI can roughly do the core thing — what does YOUR product deliver that they can't? Not technically — experientially. What does the user get from you that they'd never get from a chat prompt?"

This answer constrains everything that follows — category, differentiator, one-liner, and monetization.

**Step 1: Define the category (Ries + Dunford).**
Ask:
- "When someone asks 'what is this?' — what's the short answer?"
- "What category does this live in? Or do you need to create a new one?"
- "What's the competitive alternative? Not just apps — what behavior are you replacing?"

Help them write the positioning statement:
`For [target user] who [situation], [product] is a [category] that [key benefit]. Unlike [alternative], we [differentiator].`

Push back if the differentiator is a feature list. "Pick one thing. The one that matters most."

**Step 2: Remarkability test (Godin).**
- "Would your target user text a friend about this? What would they say?"
- "Who is the smallest group of people who would be MOST passionate about this?"
- "What's the purple cow — the remarkable thing that makes this worth talking about?"

If they say "everyone would like it" — push back: "Products for everyone are products for no one. Narrow it."

**SVA guidance:** Push toward **behavioral** audience definitions, not demographics. "Women 25-45" is a demographic — it tells you nothing about intent. "People who've already gone looking for help online" is a behavior — it tells you they have the pain AND have acted on it. The qualifying question is: "What has your audience already *done* that makes them your audience?" A behavioral SVA also often reveals the right platform — if they search when the pain hits, meet them where they search.

**Step 3: Build the StoryBrand script (Miller).**
Walk through each element conversationally:
- "Who is the hero? (Hint: not you. The user.)"
- "What's their external problem? The internal frustration? The philosophical injustice?"
- "You're the guide. What's your empathy statement? What's your authority?"
- "What are the 3 steps? Keep it dead simple."
- "What does success look like? What does failure look like?"

**Step 4: Messaging acid test.**
Challenge them:
- "Say your one-liner. Would a stranger at a party get it instantly?"
- "Can a 12-year-old understand what you do?"
- "I'm going to say 'so what?' three times. Your answer needs to get better each time."

### Generate Deliverable: Positioning Document

Save to `docs/idea-to-product/<project-name>-positioning.md`.

```
POSITIONING DOCUMENT
═══════════════════════════════════════════════

CATEGORY: [what space you're in or creating]

ONE-LINER: [8 words or fewer]

POSITIONING STATEMENT:
For [target user] who [situation], [product] is a [category]
that [key benefit]. Unlike [alternative], we [differentiator].

SMALLEST VIABLE AUDIENCE:
[Specific description of the tribe]

KEY DIFFERENTIATOR: [one thing]

STORYBRAND BRANDSCRIPT:
• Character: [user]
• Problem: [external / internal / philosophical]
• Guide: [you — empathy + authority]
• Plan: [3 steps]
• Call to Action: [direct]
• Success: [what changes]
• Failure: [what they lose]

═══════════════════════════════════════════════
```

### Evaluate Gate

- [ ] 5 target users would understand the one-liner without explanation
- [ ] Category is named (existing or new)
- [ ] Differentiator is one thing, not a list
- [ ] StoryBrand script feels honest, not aspirational marketing

**If gate passes:** "You know who you are and who you're for. Phase 4 — let's make the money work."

---

## Phase 4: DESIGN THE BUSINESS MODEL

> **Goal:** Make the money math work before writing code.
> **Expert frameworks:** Alex Hormozi ($100M Offers), Russell Brunson (funnels), Tim Ferriss (minimum effective dose), Dan Sullivan (Who Not How)
> **Output:** Business model one-pager

### How to Guide This Phase

**Step 1: Design the offer (Hormozi).**
Explain the value equation:
```
Value = (Dream Outcome × Perceived Likelihood) / (Time Delay × Effort & Sacrifice)
```
Then ask:
- "What's the dream outcome for your user?"
- "How can you make them believe this will actually work for them?"
- "How fast do they get results?"
- "How much effort does it take on their part?"
- "What can you add that 10x the perceived value without 10x your cost?"

**Step 2: Research comparable monetization (market scan).**
Before setting pricing, look at how comparable products monetize — not just direct competitors, but similar product shapes in other domains. Use web search to find:
- Products with similar usage patterns (sporadic vs. daily, one-shot vs. ongoing)
- Products with similar cost structures (AI/API costs per use)
- Hybrid, subscription, pay-per-use, and credits-based models in the current market
- Industry data on conversion rates, churn, and revenue per payer

Map findings to the product's specific characteristics. The goal isn't to copy — it's to ground pricing decisions in market reality before guessing.

**Step 3: Set pricing (Brunson + Ferriss).**
- "What does this problem currently cost your user? In money, time, frustration?"
- "If your app saves them $X/month or Y hours/week, what's 10% of that worth?"
- "Start with one price. What feels right?"
- Push back if too low: "Underpricing signals low value. What would premium look like?"
- Push back if too high: "Can your smallest viable audience afford this?"

**Pricing-positioning alignment check:** After proposing a price, pressure-test it against the Phase 3 positioning. Price is a positioning signal — it tells users what category they're in. A $5/month tool and a $15/month service attract different users and set different expectations. Ask: "Does this price match the positioning you defined? Would your target user see this price and think 'that's about right for what this is'?"

**Step 4: Map the funnel (Brunson).**
For B2C, keep it simple. Walk through:
```
Awareness → Landing Page → Free Trial/Freemium → Aha Moment → Paid → Retention
```
- "What's the free hook — the taste that demonstrates core value?"
- "What's the aha moment that makes them think 'I need this'?"
- "How long from signup to aha moment? Can you shorten it?"
- "What triggers the upgrade — what do they hit that makes free not enough?"

**Step 5: Run the numbers (Sullivan).**
- "What monthly revenue covers your costs plus 20%?"
- "At $[price]/month, how many paying users is that?"
- "Is that number realistic in your market? How would you reach them?"
- "What's a realistic Customer Acquisition Cost for B2C in this space?"
- "LTV needs to be 3× CAC or higher. Does it work?"

If the math doesn't work, say so. Help them adjust price, audience size, or model.

**Step 6: Plan post-core-action tracking.**
The core action (the aha moment) is the hook — but what users do AFTER it tells you where real value lives and what to charge for. Map every engagement point after the core action is delivered:
- What do users interact with after getting the core output?
- Which features do they tap, explore, or ignore?
- Where do they drop off vs. go deeper?
- What triggers return visits?

This isn't analytics for analytics' sake — it's the data that tells you whether your free/paid split is correct. If users consistently engage with a free feature but ignore paid ones, the paywall is in the wrong place. If a paid feature gets zero engagement, cut it. **Don't decide what to charge for in advance — let the data tell you.**

**Step 7: Tag business assumptions for post-launch tracking.**
Every pricing and monetization decision made in this phase is an assumption. Tag each one explicitly with:
- How to measure it post-launch (specific metric)
- What threshold means it's working vs. failing
- What action to take if it fails

These assumptions carry forward into Phase 6 as part of the measurement plan. Connect them directly — Phase 4 assumptions become Phase 6 metrics.

**Step 8: Who Not How (Sullivan).**
- "What can someone else build, design, or market?"
- "What must YOU personally do?"
- "Where does $1 of delegation save $10 of your time?"

**Step 9: Assumption-Metric Coverage Audit.**
Before closing Phase 4, cross-reference EVERY assumption from all prior phases against the tracking plan. This is the quality gate that ensures nothing goes unmeasured into the build.

Gather all assumptions:
- **Kill criteria** from Phase 1
- **A-series assumptions** from Phase 2 (pain, feasibility, market)
- **B-series assumptions** from Phase 4 (business model, pricing, monetization)

Cross-reference against the **T-series tracking events** from Step 6.

For each assumption, verify:
- It has a specific metric or tracking event mapped to it
- That metric has a pass threshold and a fail action
- The measurement method is feasible (some metrics come from analytics events, others from billing dashboards, user feedback, or platform-level reporting)

For each tracking event, verify:
- It maps back to at least one assumption (no orphan metrics — don't track what you won't act on)

**Flag gaps.** Common gaps to check:
- Assumptions about AI/tech accuracy — often missing a user feedback mechanism (e.g., thumbs up/down)
- Assumptions about platform/device — often covered automatically by analytics tools but not called out for review
- Assumptions about API/infrastructure costs — need backend logging or billing dashboard review, not in-app tracking
- Kill criteria — often stated as vibes ("no revenue after 2 months") without a specific metric threshold

**Produce the assumptions tracker** as a standalone deliverable. This is the single artifact that connects Phase 1 kill criteria + Phase 2 A-series + Phase 4 B-series + Phase 4 T-series into one auditable table.

Save to `docs/idea-to-product/<project-name>-assumptions-tracker.md`.

```
ASSUMPTIONS TRACKER
═══════════════════════════════════════════════

PHASE 2 ASSUMPTIONS (Pain & Feasibility):
| ID | Assumption | Pre-launch signal | Post-launch metric | Pass | Fail action |
|----|-----------|-------------------|-------------------|------|-------------|
| A1 | [text]    | [✅/❓/❌]         | [T-event or other] | [threshold] | [action] |

PHASE 4 ASSUMPTIONS (Business Model):
| ID | Assumption | Post-launch metric | Pass | Fail action |
|----|-----------|-------------------|------|-------------|
| B1 | [text]    | [T-event or other] | [threshold] | [action] |

KILL CRITERIA (from Phase 1):
[List with specific metrics and thresholds]

COVERAGE AUDIT:
✅ Every assumption has a metric
✅ Every metric has a threshold
✅ Every threshold has a fail action
✅ No orphan metrics (every tracked event maps to an assumption)
⚠️ Gaps identified and resolved: [list any gaps found and how they were closed]

4-WEEK CHECKPOINT AGENDA:
1. Score every assumption with real data
2. Run 5-7 user conversations
3. Make go/kill/pivot decision

═══════════════════════════════════════════════
```

### Generate Deliverable: Business Model One-Pager

Save to `docs/idea-to-product/<project-name>-business-model.md`.

```
BUSINESS MODEL
═══════════════════════════════════════════════

OFFER:
[Description using Hormozi value equation]

PRICING: $[X]/[period]
Rationale: [why this price]

FUNNEL:
[Awareness] → [Landing] → [Free hook] → [Aha moment] → [Paid] → [Retain]

UNIT ECONOMICS:
• Price: $[X]/mo
• Target customers (break-even): [N]
• CAC estimate: $[X]
• LTV estimate: $[X]
• LTV/CAC ratio: [X]

POST-CORE-ACTION TRACKING PLAN:
[Map of engagement points after the core value is delivered]
[Which interactions to track and what each signal means]

BUSINESS ASSUMPTIONS (carry to Phase 6):
| ID | Assumption | Metric | Pass threshold | Fail action |
|----|-----------|--------|----------------|-------------|
| B1 | [text]    | [how]  | [threshold]    | [action]    |

DELEGATION MAP:
• You: [core value work]
• Hire/outsource: [everything else]

═══════════════════════════════════════════════
```

### Evaluate Gate

- [ ] Unit economics work on paper (LTV > 3× CAC)
- [ ] Price tested with at least 5 target users
- [ ] Pricing aligns with Phase 3 positioning and SVA (price signals the right category)
- [ ] One clear aha moment identified in the funnel
- [ ] Build vs. delegate decisions made
- [ ] Break-even number is realistic
- [ ] Assumption-metric coverage audit complete — every assumption (A-series + B-series + kill criteria) maps to a measurable metric with threshold and fail action
- [ ] Assumptions tracker saved as standalone deliverable

**If gate passes:** "The math works. Phase 5 — time to build. And only build what matters."

---

## Phase 5: BUILD THE MVP

> **Goal:** Build only what proves the core value proposition. Nothing else. This is Phase A from the "Ship First, Compound Later" strategy — the experience layer only.
> **Expert frameworks:** Eric Ries (lean MVP), Cal Newport (deep work), Michael Gerber (systems), BJ Fogg (behavior design)
> **Output:** MVP spec, behavior loop, metrics plan, distribution plan
> **Key inputs:** Phase 4's post-core-action tracking plan and business assumptions (B-series)

### How to Guide This Phase

**Step 1: Scope to Phase A only (Ries + Ship First).**
Ask:
- "What is the ONE action the user takes in your app?"
- "What is the ONE outcome they get from that action?"
- "Everything else — cut it. What are you tempted to add that isn't essential?"

Challenge scope creep: "Does that feature test your core hypothesis? No? Then it's not in the MVP."

Ask the hard question: "Can you test this without building an app at all? Landing page? Manual process? Spreadsheet?"

**Phase A / Phase B split:** Explicitly list what IS in the MVP (Phase A — the experience layer) and what is NOT (Phase B — moat features). Phase B features should be named and planned directionally, but not built. The MVP tests whether the experience layer alone justifies payment. Phase B starts only after Phase A validates.

Example split:
```
Phase A (MVP):              Phase B (moat — NOT building yet):
─────────────────────       ─────────────────────────────────
Core workflow               Ingredient conflict database
Free/paid paywall           Community data ("similar shelves")
Basic analytics             Progress tracking over time
Visual output               Specialized workflows
```

**Step 2: Design the behavior loop (Fogg).**
Walk through:
- "What triggers someone to open your app? A notification? A routine? An emotion?"
- "What's the smallest possible action they take? Make it tiny."
- "What reward do they get? Is it variable or predictable?"
- "What do they invest that makes leaving harder? Data? Customization? Social connections?"

For sporadic-use products (where the trigger is infrequent), focus less on habit loops and more on: "When the trigger DOES fire, how do we make sure they think of us?" This is a distribution/positioning question more than a behavior design question.

**Step 3: Plan the build (Newport + Ship First 30-day cadence).**
- "How many deep work hours per day can you commit?"
- "What's a realistic timeline for the ONE core feature?"

The build cadence aligns with the Ship First 30-day post-launch cadence. Plan the build to ship ASAP, then use the 30 days after launch as the real iteration cycle:

```
PRE-LAUNCH:
Build until the core workflow works end-to-end (ugly is fine).
Ship when: one path from input → value works. Not polished — complete.

POST-LAUNCH (30-day cadence):
Week 1: Fix onboarding friction and obvious bugs. Watch drop-off points.
Week 2: Improve activation — remove steps, clarify messaging.
         Are people completing the core action?
Week 3: Look at retention. If not returning, why?
         Do 5-7 user conversations to understand the "why" behind the data.
Week 4: Score assumption scorecard (Phase 4 B-series) with real data.
         Make go/kill/pivot decision.
```

**Step 4: Wire up instrumentation (connect to Phase 4).**
Don't reinvent the metrics plan — Phase 4 already defined what to track. This step is about implementation:

- **Pull in the post-core-action tracking plan** from Phase 4. Every engagement point mapped there becomes an analytics event.
- **Pull in business assumptions (B-series)** from Phase 4. Each assumption needs a corresponding metric in the product.
- Add the baseline metrics: activation rate, Day-1 retention, Day-7 retention.
- Plan for the Sean Ellis test at Week 4 post-launch.

The ONE number that tells you if this MVP works should come from your B-series assumptions — typically the conversion rate (free → paid).

**Instrumentation completeness check.** Cross-reference the **assumptions tracker** (produced in Phase 4 Step 9) against the instrumentation plan. For every assumption, verify:
- The corresponding T-series event or alternative measurement method is in the build plan
- Assumptions measured by analytics platform defaults (e.g., device breakdown, referral source) are called out explicitly for review at the 4-week checkpoint — "automatically captured" ≠ "will be reviewed"
- Assumptions measured outside the app (e.g., API cost at billing dashboard level, accuracy via user feedback) have a specific review method planned
- No assumption is left with "we'll figure out how to measure this later"

Flag any gaps. Common gaps found in practice:
- **AI accuracy assumptions** — need an in-app feedback mechanism (e.g., thumbs up/down). Without it, you're guessing whether the core tech works.
- **Platform/device assumptions** — analytics tools capture this automatically but it's easy to forget to review. Call it out as a checkpoint agenda item.
- **Cost assumptions** — API/infrastructure costs need backend logging or billing dashboard review, not in-app events. Plan how and when to check.

If gaps are found, add them to the MVP build plan (as required or optional depending on criticality).

**Step 5: Plan initial distribution.**
Distribution is 75-80% of success when tech is commoditized. Even at MVP, plan where your first 100 users come from. Don't build first and figure out distribution later — the two are designed together.

Ask:
- "Where are your target users when the pain hits?" (This should be answered by the behavioral SVA from Phase 3)
- "What are 3 specific channels you'll use to reach your first 100 users?"
- "Can the product itself be a distribution mechanism?" (Shareable outputs, screenshots, referral loops)
- "What's the enrollment story — why should someone try this right now?"

The distribution plan doesn't need to be sophisticated. It needs to be specific: channel → message → expected reach → conversion assumption.

### Generate Deliverable: MVP Spec

Save to `docs/idea-to-product/<project-name>-mvp-spec.md`.

```
MVP SPEC
═══════════════════════════════════════════════

CORE ACTION: [the one thing the user does]
CORE OUTCOME: [the one thing they get]

PHASE A (BUILDING — experience layer):
• [feature 1]
• [feature 2]
• [feature 3]

PHASE B (NOT BUILDING — moat direction):
• [feature 1 — why it's Phase B, not A]
• [feature 2 — why it's Phase B, not A]

BEHAVIOR LOOP:
• Trigger: [what prompts usage]
• Action: [simplest behavior]
• Reward: [what they get]
• Investment: [what they put in]

BUILD SCHEDULE:
• Pre-launch: [what to build, when to ship]
• Post-launch Week 1: [onboarding fixes, drop-off analysis]
• Post-launch Week 2: [activation improvement]
• Post-launch Week 3: [retention analysis + 5-7 user conversations]
• Post-launch Week 4: [score assumptions, go/kill/pivot]

INSTRUMENTATION (from Phase 4):
[Post-core-action tracking events wired in]
[B-series assumptions mapped to metrics]

DISTRIBUTION PLAN:
• Channel 1: [where] → [message] → [expected reach]
• Channel 2: [where] → [message] → [expected reach]
• Channel 3: [where] → [message] → [expected reach]
• Built-in distribution: [how the product spreads itself]

SUCCESS METRIC: [the one number]
• Validated if: [threshold]
• Kill if: [threshold]

═══════════════════════════════════════════════
```

### Evaluate Gate

- [ ] MVP is Phase A only — Phase B features listed but not built
- [ ] Behavior loop is designed (or sporadic-use trigger strategy defined)
- [ ] Instrumentation wired to Phase 4 tracking plan and B-series assumptions
- [ ] Instrumentation completeness check passed — every assumption in the tracker has a wired metric or explicit review method, no gaps
- [ ] Success/kill numbers defined before building
- [ ] Distribution plan: 3 specific channels for first 100 users
- [ ] Tested with 3-5 real users
- [ ] No feature added that doesn't test the core hypothesis

**If gate passes:** "You've built the experiment. Phase 6 — get it in front of people who'll pay."

---

## Phase 6: LAUNCH & FIRST REVENUE

> **Goal:** Get the MVP to paying users and read the signals.
> **Expert frameworks:** Seth Godin (smallest viable audience), Russell Brunson (funnels), Grant Cardone (10X effort), Sean Ellis (PMF measurement)
> **Output:** Launch plan, funnel metrics, PMF signal

### How to Guide This Phase

**Step 1: Plan the launch (Godin).**
Ask:
- "Where do your target users already hang out online?"
- "What's your enrollment story? Not 'download my app' — why should they care?"
- "Can you give early users status? Beta testers, founding members, first 100?"
- "Who are 50 specific people you could reach out to this week?"

**Step 2: Set up funnel tracking (Brunson).**
- "What's your funnel? Walk me through: how does someone go from not knowing you exist to paying?"
- Help them set up tracking at every step
- "Where do you expect the biggest drop-off? What's your plan for that?"

**Step 3: Push on effort (Cardone).**
Be direct:
- "How many people are you reaching out to per day? Multiply by 10."
- "What content are you creating? Where are you posting it?"
- "Are you asking every happy user for a referral?"

**Step 4: Measure PMF (Ellis).**
Help them run the Sean Ellis test:
- Survey users: "How would you feel if you could no longer use [product]?"
- 40%+ "very disappointed" = PMF signal
- Below 40%: "Don't scale. Iterate on value first."

**Step 5: Read the signals together.**
Ask:
- "Are people paying without heavy convincing?"
- "Are they coming back without reminders?"
- "Are they telling others without being asked?"
- "Yes to 2+: you have something. No: we need to trace back to where it breaks."

### Generate Deliverable: Launch Report

Save to `docs/idea-to-product/<project-name>-launch-report.md`.

```
LAUNCH REPORT
═══════════════════════════════════════════════

LAUNCH CHANNELS: [where you launched]
REACH: [how many people saw it]

FUNNEL:
Awareness: [N] → Clicked: [N] → Signed up: [N] → Activated: [N] → Paid: [N]
Conversion rates: [at each step]

PMF SIGNAL (Sean Ellis):
Very disappointed: [X]%    ← target: 40%+
Somewhat disappointed: [X]%
Not disappointed: [X]%

REVENUE:
• Paying users: [N]
• MRR: $[X]
• Conversion rate: [X]%

ORGANIC SIGNALS:
• Unprompted referrals: [Y/N]
• Repeat usage without prompting: [Y/N]
• Unsolicited positive feedback: [Y/N]

DECISION: SCALE / ITERATE / PIVOT / KILL
Evidence: [why]

═══════════════════════════════════════════════
```

### Evaluate Gate → Scale (outside this playbook)

- [ ] 40%+ "very disappointed" on Sean Ellis test
- [ ] Positive unit economics (or clear path)
- [ ] Organic referrals happening
- [ ] Retention curve flattening
- [ ] Repeatable acquisition channel identified

---

## Session Management

**Starting a new idea:** Show the phase overview. Start at Phase 1.

**Resuming:** Ask "Where did we leave off?" If they have deliverables from prior phases, review them briefly and pick up at the next incomplete phase.

**Multiple ideas:** Run each through Phase 1 separately. Only advance the strongest one to Phase 2+. Kill the rest early.

**Phase skip requests:** Push back. "Skipping validation is the #1 reason apps fail. I'd rather you spend 2 weeks interviewing than 2 months building something nobody wants." If they insist, note the risk and proceed — it's their call.

**Kill decisions:** If the data says kill, say so clearly. Don't soften it. "The data says this pain isn't real enough. That's valuable information — you just saved yourself months. Want to pivot the idea, pivot the audience, or start fresh?"

## Iteration Protocol

At any phase, if the gate fails:

1. **Diagnose**: Which specific check failed?
2. **Trace back**: Which earlier phase produced the faulty input?
3. **Fix at source**: Go back to the right phase, don't patch
4. **Re-validate forward**: Re-run gates from the fix point

**Common loops:**
- Phase 6 fails (no PMF) → usually Phase 2 (pain not real) or Phase 3 (positioning off)
- Phase 5 fails (no usage) → Phase 2 (wrong JTBD) or Phase 4 (wrong aha moment)
- Phase 4 fails (math broken) → Phase 3 (audience too small) or Phase 1 (not 10x better)

## Anti-Patterns — Call These Out When You See Them

| Trap | What It Sounds Like | Your Response |
|------|---------------------|---------------|
| Building before validating | "I'll just code a quick prototype" | "Phase 2 first. Always." |
| Validating with friends | "My friends love it" | "Friends lie. Mom Test with strangers." |
| Feature creep | "Just one more feature" | "Does it test the hypothesis? No? Cut." |
| Premature scaling | "Let's run ads" | "40% Ellis test first, then scale." |
| Ignoring kill signals | "The data is wrong" | "You pre-committed to these criteria. Honor them." |
| Perfecting before launching | "It's not ready" | "If it tests the hypothesis, it's ready." |
| Doing everything solo | "I'll learn design" | "Who, not How. What's your time worth?" |
