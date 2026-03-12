# My Claude Skills

Custom skills for [Claude Code](https://docs.anthropic.com/en/docs/claude-code), organized by domain.

## Skills

### Product & Validation

| Skill | What it does |
|-------|-------------|
| **idea-to-product** | Guided 6-phase process from raw idea to revenue-generating MVP. Socratic coaching with expert frameworks (Thiel, Ries, Hormozi, Ellis), phase gates, and deliverable templates. *Uses: validation-talk, market-scan, demand-scan.* |
| **validation-talk** | Generates interview questionnaires that produce go/kill signals. Mom Test + JTBD + Sean Ellis PMF — every question maps to an assumption with a kill threshold. |
| **market-scan** | Broad competitive landscape research via web search. Produces a decision-ready report with sourced findings. |
| **demand-scan** | Targeted demand validation — competitor deep-dives, user complaints, DIY workaround patterns. Complements market-scan's breadth with depth. |

### Session & Workflow

| Skill | What it does |
|-------|-------------|
| **mastermind-session** | Interactive roundtable with 5-10 thought leaders to solve business, strategic, or personal challenges. 5-phase structured process. |
| **consolidate** | Post-session learning extraction. Scans conversation for insights and routes them to the correct persistent storage (memory, CLAUDE.md, rules). |
| **wait-what** | Session checkpoint — structured summary of what was done, why, and what's next. Use before committing or when you lose track. |
| **tech-to-social** | Turn technical work (commits, PRs, bug fixes, architecture decisions) into LinkedIn posts. 2-3 draft variations per request with hook patterns, tone selection, and series planning. |

### Meta & Maintenance

| Skill | What it does |
|-------|-------------|
| **skill-creator** | Guide for creating new skills. 6-step process with progressive disclosure patterns and Python utilities for init/validate/package. |
| **bouncer** | Security audit for vetting third-party skills, plugins, hooks, and MCP servers before installation. 4-phase process covering 8 threat categories. |
| **spring-clean** | Audit and optimize Claude Code session context budget. Covers MCP servers, plugins, MEMORY.md, CLAUDE.md, custom agents. |

## Install a skill

```bash
# Install any skill directly from this repo
claude install-skill https://github.com/eva-mishor/my-claude-skills/tree/main/skills/<skill-name>
```

### idea-to-product (full toolkit)

idea-to-product invokes 3 companion skills during its phases. Install all four for the complete experience:

```bash
claude install-skill https://github.com/eva-mishor/my-claude-skills/tree/main/skills/idea-to-product
claude install-skill https://github.com/eva-mishor/my-claude-skills/tree/main/skills/validation-talk
claude install-skill https://github.com/eva-mishor/my-claude-skills/tree/main/skills/market-scan
claude install-skill https://github.com/eva-mishor/my-claude-skills/tree/main/skills/demand-scan
```

> idea-to-product works without the companion skills, but you'll miss the structured research and interview frameworks in Phases 2-3.

### Other examples

```bash
claude install-skill https://github.com/eva-mishor/my-claude-skills/tree/main/skills/bouncer
claude install-skill https://github.com/eva-mishor/my-claude-skills/tree/main/skills/consolidate
```

Some skills are also available as standalone gists:
- [bouncer](https://gist.github.com/eva-mishor/839810fe18d1e8e66cf4a9496ea307e8)
- [consolidate](https://gist.github.com/eva-mishor/2ca6bfe8f3a2ee5170e996b292340ce0)

## Creating new skills

Use the `skill-creator` skill, or manually:

```bash
# Initialize a new skill
python skills/skill-creator/scripts/init_skill.py my-new-skill --path skills/

# Validate
python skills/skill-creator/scripts/quick_validate.py skills/my-new-skill
```

## Repo structure

```
skills/
├── idea-to-product/       # Idea-to-MVP coaching workflow
├── validation-talk/       # Interview questionnaire generator
├── market-scan/           # Competitive landscape research
├── demand-scan/           # Targeted demand validation
├── mastermind-session/    # Expert roundtable sessions
├── consolidate/           # Post-session learning extraction
├── wait-what/             # Session checkpoint summaries
├── skill-creator/         # Skill creation guide + tools
├── tech-to-social/        # Technical work → LinkedIn posts
├── bouncer/               # Security audit for skills/plugins
└── spring-clean/          # Context budget optimizer
```

## License

Skills may have individual licenses. See each skill's directory for details.
