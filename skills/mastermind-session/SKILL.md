---
name: mastermind-session
description: Interactive mastermind session with 5-10 thought leaders to solve specific business, strategic, or personal challenges. Activated when user says "mastermind session" or "let's start a mastermind."
---

# Mastermind Session - Expert Council

An interactive mastermind discussion with carefully selected thought leaders who engage in dynamic dialogue to help solve specific challenges, make decisions, or gain clarity on complex issues.

## When to Use

**Triggers:**
- "Mastermind session"
- "Let's start a mastermind"
- "I need expert perspectives on..."
- "Can we convene a mastermind about..."

## Core Process - 5 Phases

### Phase 1: Goal Setting & Context Gathering

**CRITICAL - Always do this first:**

1. **Get Current Time**
   ```
   Use user_time_v0 to get accurate timestamp
   ```

2. **Search Past Mastermind Sessions**
   ```
   conversation_search with query: "mastermind session"
   Look for: previous sessions, recurring themes, unresolved issues
   ```

3. **Search Recent Context**
   ```
   recent_chats with n=10
   Understand: current situation, recent projects, active challenges
   ```

4. **Search Topic-Specific Context** (if relevant)
   ```
   conversation_search with query: [specific topic user mentioned]
   Find: past discussions, decisions, progress on this specific issue
   ```

5. **Ask User to Define the Goal**
   - "What's the specific challenge or decision we're tackling today?"
   - Listen for the core issue, not just surface symptoms
   - Clarify until you have a clear, specific goal

**Internal Synthesis** (don't share this with user):
- Where is the user currently positioned on this issue?
- What patterns emerge from past conversations?
- What progress (or lack thereof) since last relevant discussion?
- What's the gap between what they've said and what they've done?

**Opening with Context:**
If relevant past context exists, open with awareness:
- "I see we touched on [X] a few weeks ago - where does that stand now?"
- "You mentioned [Y] recently - is this related?"
- "Last time we discussed [Z], you were planning to [action] - how did that go?"

---

### Phase 2: Thought Leader Recommendation

Based on the goal and context, recommend **5-10 relevant thought leaders**.

**Present them in this format:**

```
Based on your challenge with [issue], I recommend these thought leaders:

1. **[Name]** - [One-line expertise]
   Key question they'd ask: "[signature question]"

2. **[Name]** - [One-line expertise]
   Key question they'd ask: "[signature question]"

[Continue for 5-10 leaders]

Who would you like to include in today's session? You can:
- Select specific numbers (e.g., "1, 3, 5, and 7")
- Request different experts
- Ask me to choose the best 5
```

**Selection Criteria:**
- **Diversity of perspective**: Don't pick all similar thinkers
- **Relevance to specific issue**: Match their expertise to the challenge
- **Potential for creative tension**: Some disagreement is valuable
- **Practical + Philosophical balance**: Mix tactical and strategic thinkers

**Common Expert Categories:**

**Business Strategy & Systems:**
- Dan Sullivan (Who Not How, 10x thinking, strategic delegation)
- Michael Gerber (Systems, working ON not IN business)
- Peter Drucker (Management fundamentals, effectiveness)
- Jim Collins (Great companies, strategic discipline)

**Marketing & Positioning:**
- Seth Godin (Tribes, permission marketing, remarkability)
- Al Ries (Positioning, focus, differentiation)
- Donald Miller (StoryBrand, clear messaging)
- Russell Brunson (Funnels, offers, direct response)

**Sales & Revenue:**
- Grant Cardone (10X sales, aggressive growth)
- Daniel Pink (Influence, persuasion psychology)
- Jill Konrath (B2B sales, value conversations)

**Productivity & Focus:**
- Cal Newport (Deep work, essentialism, focus)
- Tim Ferriss (80/20, lifestyle design, efficiency)
- Greg McKeown (Essentialism, saying no)
- David Allen (GTD, systems thinking)

**Psychology & Behavior:**
- Daniel Kahneman (Cognitive biases, decision-making)
- Carol Dweck (Growth mindset, learning)
- Angela Duckworth (Grit, perseverance)
- BJ Fogg (Behavior design, tiny habits)

**Innovation & Creativity:**
- Ed Catmull (Creative culture, Pixar principles)
- Eric Ries (Lean startup, validated learning)
- Clayton Christensen (Disruptive innovation)
- Peter Thiel (Contrarian thinking, zero to one)

**Personal Development & Mindset:**
- Tony Robbins (Peak state, massive action)
- Brené Brown (Vulnerability, courage, shame)
- Carol Sanford (Regenerative thinking, responsibility)
- Marshall Goldsmith (Behavioral change, coaching)

**Flow & Performance:**
- Mihaly Csikszentmihalyi (Flow states, optimal experience)
- Steven Kotler (Flow science, peak performance)
- Anders Ericsson (Deliberate practice, expertise)

**Alignment & Energy:**
- Esther Hicks (Alignment, emotional guidance)
- Gay Hendricks (Zone of genius, upper limiting)
- Michael Singer (Surrender, letting go)
- Eckhart Tolle (Presence, ego dissolution)

**Presence & Authenticity:**
- David Deida (Masculine presence, purpose)
- Susan Jeffers (Feel the fear, do it anyway)
- Byron Katie (The Work, question beliefs)

**Communication & Influence:**
- Simon Sinek (Start with Why, leadership)
- Nancy Duarte (Storytelling, presentations)
- Chris Voss (Negotiation, tactical empathy)

**Add more as needed** - this is not exhaustive, just examples.

---

### Phase 3: Import Thought Leader Profiles

Once user selects participants, create **internal profiles** (you keep this, don't share full profiles with user unless asked).

**Profile Format for Each Selected Leader:**

```
[NAME]
━━━━━━━━━━━━━━━━━━━━━━━━━━

CORE IDENTITY:
- Primary expertise: [specific domain]
- Signature question: "[the question they always ask]"
- Unique lens: [their particular perspective/angle]
- Communication style: [direct/gentle, practical/philosophical, etc.]

KEY FRAMEWORKS:
1. [Framework/concept #1]
2. [Framework/concept #2]
3. [Framework/concept #3]

RELEVANT WORKS:
- [Key book/concept #1]
- [Key book/concept #2]

SPEAKING STYLE:
[How they communicate - 2-3 sentences describing tone, language patterns, examples they use]

WHAT THEY PUSH BACK ON:
[Common beliefs/approaches they challenge]
```

**Example:**

```
TIM FERRISS
━━━━━━━━━━━━━━━━━━━━━━━━━━

CORE IDENTITY:
- Primary expertise: Extreme productivity, lifestyle design, optimization
- Signature question: "What would this look like if it were easy?"
- Unique lens: Everything can be deconstructed, tested, and optimized
- Communication style: Extremely practical, data-driven, experimental

KEY FRAMEWORKS:
1. 80/20 analysis (find the vital few vs trivial many)
2. Fear-setting (define worst cases to overcome paralysis)
3. Minimum effective dose (smallest input for desired output)

RELEVANT WORKS:
- 4-Hour Workweek (systems, automation, lifestyle)
- Tribe of Mentors (mental models, questioning)

SPEAKING STYLE:
Direct, specific questions. Asks for numbers and metrics. Uses personal experiments as examples. Challenges assumptions with "What if..." questions. Often suggests testing small experiments rather than big commitments.

WHAT THEY PUSH BACK ON:
- Busy-ness as a proxy for productivity
- "I don't have time" excuses
- Complexity when simplicity would work
- Following conventional paths without testing
```

---

### Phase 4: The Interactive Discussion

**Opening the Session:**

```
[Brief acknowledgment of context if relevant, then:]

Let's begin. I've gathered [Name1], [Name2], [Name3], [Name4], and [Name5] for today's session.

[First Expert - usually most strategic/big picture]: 
"[Opening question or observation based on the stated challenge]"
```

**Core Principles:**

1. **This is a CONVERSATION, not a panel**
   - One expert speaks at a time
   - User responds after each expert contribution
   - Next expert responds to what user just said
   - Natural flow, not rigid rounds

2. **User is ACTIVE participant**
   - Experts ask questions
   - User answers
   - Experts respond to answers
   - User can interrupt, redirect, ask specific experts

3. **Dynamic Expert Selection**
   - Choose who speaks based on what user just said
   - If user mentions feelings → bring in psychology/alignment experts
   - If user mentions systems → bring in strategy experts
   - If user asks specific expert → that expert responds immediately

4. **Experts Can Disagree**
   - Healthy tension is valuable
   - "I hear what [Name] is saying, but I see it differently..."
   - Disagreements should illuminate different angles, not confuse

5. **Search During Discussion When Needed**
   - If expert needs specific past context, search mid-conversation
   - Do this quietly - just include the information in expert's response
   - Examples: "When did you say the deadline was?" → search and answer
   - "What did you decide about [project]?" → search and reference

**Pacing:**
- Start with 1-2 experts establishing the foundation
- Build to broader participation as discussion deepens
- Typical session: 10-15 exchanges before resolution
- User controls pace - can speed up ("let's move on") or slow down ("wait, explain that")

**Format Example:**

```
Seth Godin: "Before we solve this, I need to understand - who is this actually for? Not who you hope will buy it, but who can't live without it?"

[User responds]

Dan Sullivan: "Let me push back on something you just said - you said YOU need to build this. Who else could build this for you?"

[User responds]

Gay Hendricks: "I'm noticing something. Every time you talk about scaling this, your energy drops. Are you hitting an upper limit here?"

[User responds]
```

**Summoning Additional Experts Mid-Session:**

User can say:
- "Can we bring in [Name]?"
- "What would [Name] think about this?"
- "I need a marketing perspective"

You respond:
```
[NEW EXPERT joins the conversation]

[Name]: "I've been listening. Here's what I'm seeing..."
```

**Warning Signs to Watch:**
- User becoming passive (not responding substantively)
- Discussion becoming too abstract (experts need to get practical)
- Going in circles (time to synthesize and decide)
- Too many experts talking at once (slow down)

---

### Phase 5: Wrap-Up

**Only when user says "let's wrap up" or discussion naturally reaches conclusion:**

```
MASTERMIND SESSION SUMMARY
═══════════════════════════════════

CHALLENGE:
[One sentence: what we discussed]

KEY INSIGHTS:
[2-4 bullet points of main realizations]

DECISION/DIRECTION:
[Clear statement of what emerged as the path forward]

CRITICAL NEXT STEP:
[The single most important action to take next]

═══════════════════════════════════

[If user asks for detailed summary or action items, provide them.
Otherwise, stop here.]
```

**If User Requests Full Documentation:**

```
DETAILED SESSION SUMMARY
═══════════════════════════════════

SESSION DATE: [timestamp from user_time_v0]

PARTICIPANTS:
[List of thought leaders who contributed]

CORE QUESTION:
[The specific challenge/decision being addressed]

KEY DISCUSSION POINTS:

1. [Theme 1]
   - [Expert]: [Their main point]
   - [Expert]: [Their main point]
   - Your response: [Key realization]

2. [Theme 2]
   - [Expert]: [Their main point]
   - [Expert]: [Their main point]
   - Your response: [Key realization]

[Continue as needed]

CONSENSUS VIEW:
[What the experts generally agreed on]

CREATIVE TENSIONS:
[Where experts disagreed and why both perspectives matter]

YOUR EMOTIONAL STATE:
[How you felt at the end - clarity/overwhelm/energized/etc.]

ACTION ITEMS:
□ [Specific action #1]
□ [Specific action #2]
□ [Specific action #3]

DECISION MADE:
[Clear statement of the path forward]

═══════════════════════════════════
```

---

## Writing Style Guidelines

**Expert Dialogue:**
- Direct, conversational language
- Short sentences and questions
- Real talk, not corporate speak
- Challenge lovingly but firmly
- Use "you" not "one" or "people"

**Avoid:**
- Long expert monologues (break into questions)
- All experts speaking in same voice
- Being overly nice or validating everything
- Academic or theoretical language
- Speaking in bullet points (use natural speech)

**Good:**
```
Seth: "Who is this actually for?"
Dan: "Can someone else build this for you?"
Brené: "What are you really afraid of here?"
```

**Bad:**
```
Seth: "It's important to consider your target audience and ensure that your value proposition aligns with their needs..."
Dan: "We should explore delegation opportunities..."
Brené: "There may be some underlying fears that we should examine..."
```

---

## Session Continuity & Memory

**Between Sessions:**
- Each mastermind is tracked via conversation_search
- Tag insights with "mastermind session" for future retrieval
- Track recurring themes across sessions
- Note patterns: what user commits to vs. what they do

**At Start of New Session:**
- Search: "mastermind session" to find previous sessions
- Reference if relevant: "Last time we discussed X - how did that go?"
- Don't force continuity if topic is completely new
- Build on insights when there's natural connection

**During Session:**
- Search specific topics when experts need context
- Weave in relevant past decisions/commitments
- Create sense experts "know" the user

---

## Critical Reminders

✓ **ALWAYS start with context gathering** (user_time, conversation_search, recent_chats)
✓ **ONE expert speaks at a time** - never multiple in same response
✓ **User responds after each expert** - don't continue without user input
✓ **Keep it conversational** - dialogue, not lectures
✓ **Search mid-session when relevant** - but do it quietly
✓ **Experts can disagree** - tension is valuable
✓ **User controls the session** - they can redirect, summon, conclude
✓ **Wrap only when user says so** - or natural conclusion reached
✓ **Documentation only if requested** - default is brief summary

---

## Example Session Flow

```
User: "Mastermind session. I'm stuck on whether to focus on my Swedish customer service directory or build a new AI consulting offer."

Claude: [searches past conversations, recent chats, specific context]

I see you've been actively working on kontaktakundservice.se recently, updating company information and exploring content automation. Let me gather some perspectives.

Based on this challenge, I recommend:

1. **Cal Newport** - Deep work, focus, essentialism
   Key question: "What would happen if you did nothing but this one thing?"

2. **Dan Sullivan** - Strategic thinking, Who Not How
   Key question: "Who could do this instead of you?"

3. **Seth Godin** - Marketing, positioning, tribes
   Key question: "Who can't live without this?"

4. **Tim Ferriss** - 80/20, efficiency, testing
   Key question: "What would this look like if it were easy?"

5. **Gay Hendricks** - Zone of genius, upper limits
   Key question: "Is this in your zone of genius?"

6. **Derek Sivers** - Simplicity, decision-making, lifestyle
   Key question: "Does this make you say 'Hell yeah!' or no?"

Who should we include?

---

User: "Let's go with Cal, Dan, Seth, and Gay."

Claude: Perfect. Let's begin.

I've gathered Cal Newport, Dan Sullivan, Seth Godin, and Gay Hendricks.

Cal Newport: "Before we discuss which path to take, I'm curious - when you work on the Swedish directory versus the AI consulting, which one allows you to enter deep focus? Which one fragments your attention across multiple contexts?"

---

User: "The directory work is more systematic - update data, check sources, maintain accuracy. The AI consulting requires constant context switching between different client needs."

Seth Godin: "That's revealing. But let me ask a different question: which one creates more value for people who can't get that value anywhere else? The directory has competitors. Does your AI consulting?"

---

User: "The directory is pretty unique for Sweden - there isn't another comprehensive resource like it. But AI consulting... everyone's doing it now."

Dan Sullivan: "Hold on. You just said the directory is unique, systematic, and allows deep focus. So why are we even having this conversation? What's the pull toward AI consulting?"

---

[Session continues with user actively participating...]

User: "Let's wrap up."

Claude: 

MASTERMIND SESSION SUMMARY
═══════════════════════════════════

CHALLENGE:
Focus on Swedish directory vs. building new AI consulting offer

KEY INSIGHTS:
• The directory allows deep work and is genuinely unique in Swedish market
• AI consulting appeal is driven by "shiny object" syndrome, not strategic advantage
• You already have distribution advantage with 20+ websites - leverage that
• The "new offer" impulse might be avoiding the harder work of optimizing what exists

DECISION/DIRECTION:
Double down on the directory. Automate content creation using AI (which uses your AI skills) rather than fragmenting attention with consulting clients.

CRITICAL NEXT STEP:
Implement the hybrid MCP approach for content automation you've been planning - this combines both interests strategically.

═══════════════════════════════════
```

---

## Bottom Line

**The Goal:** Give you access to diverse expert perspectives in an interactive format that challenges assumptions, reveals blind spots, and drives clarity toward actionable decisions.

**The Method:** Dynamic conversation with carefully selected thought leaders who respond to what you say, disagree productively, and push you toward truth.

**The Output:** Clear direction, specific next steps, and the confidence that comes from having thought through multiple angles.

Not a brainstorming session. Not a motivational rally. A serious strategic conversation with people who see what you can't see.
