# My Claude Skills

Custom repository for personal Claude Code skills.

## About

This repository contains a collection of custom skills for Claude Code, organized as a local marketplace. Skills extend Claude's capabilities with specialized knowledge, workflows, and tool integrations.

## Available Skills

### skill-creator
Guide for creating effective skills. Includes:
- Six-step skill creation process
- Progressive disclosure design patterns
- Bundled resources organization (scripts, references, assets)
- Python utilities for initializing, validating, and packaging skills

### mastermind-session
Interactive mastermind session with 5-10 thought leaders to solve specific business, strategic, or personal challenges. Features:
- Dynamic expert dialogue and interaction
- Context-aware session continuity
- 5-phase structured process (Goal Setting, Expert Selection, Facilitated Discussion, Synthesis, Action Planning)
- Triggered by "mastermind session" or "let's start a mastermind"

### bouncer
Security audit workflow for vetting third-party Claude Code skills, plugins, hooks, and MCP servers before installation. Features:
- 4-phase structured audit (Inventory, Static Analysis, Behavioral Analysis, Verdict)
- 8 threat categories informed by CVE-2025-59536 and Snyk ToxicSkills study
- Grep-able detection patterns for each attack vector
- Reference files for attack patterns and threat taxonomy
- Triggered by "vet this skill", "audit skill security", "is this skill safe", or "scan skill"
- [Install from Gist](https://gist.github.com/eva-mishor/839810fe18d1e8e66cf4a9496ea307e8)

### spring-clean
Audit and optimize Claude Code session context budget. Use when sessions feel sluggish, context compacts too early, or after installing new plugins/MCP servers. Features:
- 4-phase process (Measure, Identify Waste, Optimize, Verify)
- Covers MCP servers, plugins, MEMORY.md, CLAUDE.md, custom agents
- Quick-reference table of common wins with typical token savings
- Triggered by "audit context", "optimize context", "context budget", or "session overhead"

### consolidate
Post-session learning extraction and memory management. Systematically scans the conversation for valuable insights and routes them to the correct persistent storage. Features:
- 5-phase process (Extract, Route, Deduplicate, Present Proposal, Write)
- Auto-detects sessions with significant unrecorded learnings
- Routes to project memory, global CLAUDE.md, project CLAUDE.md, or rules as appropriate
- Diff-style proposals with user approval before any writes
- MEMORY.md capacity management with 200-line limit awareness
- Triggered by "consolidate", "save learnings", "update memory", "extract insights", or "what did we learn"
- [Install from Gist](https://gist.github.com/eva-mishor/2ca6bfe8f3a2ee5170e996b292340ce0)

## Installation

### Add this Marketplace to Claude Code

```bash
claude plugin marketplace add /Users/user/Documents/Code/my-claude-skills
```

### Install Skills

After adding the marketplace, you can install skills using:

```bash
claude plugin install skill-creator
claude plugin install mastermind-session
claude plugin install bouncer
claude plugin install spring-clean
claude plugin install consolidate
```

Or through the Claude Code interface when browsing available skills.

## Creating New Skills

Use the `skill-creator` skill to guide you through creating new skills:

1. Install the skill-creator skill (see above)
2. Use the skill in Claude Code by typing `/skill-creator` or invoking it through the skills menu
3. Follow the six-step process to design and implement your skill

### Manual Skill Creation

You can also use the included Python scripts:

```bash
# Initialize a new skill
python skills/skill-creator/scripts/init_skill.py my-new-skill --path skills/

# Validate your skill
python skills/skill-creator/scripts/quick_validate.py skills/my-new-skill

# Package your skill for distribution
python skills/skill-creator/scripts/package_skill.py skills/my-new-skill
```

## Repository Structure

```
my-claude-skills/
├── .claude-plugin/
│   └── marketplace.json       # Marketplace configuration
├── skills/
│   ├── skill-creator/         # Skill creation guide and tools
│   │   ├── SKILL.md           # Main skill documentation
│   │   ├── LICENSE.txt        # Apache 2.0 license
│   │   ├── scripts/           # Python utilities
│   │   └── references/        # Workflow and pattern guides
│   ├── mastermind-session/    # Mastermind session skill
│   │   ├── SKILL.md           # Main skill documentation
│   │   └── README.md          # Skill-specific documentation
│   ├── bouncer/               # Security audit for third-party skills
│   │   ├── SKILL.md           # 4-phase audit workflow
│   │   └── references/        # Attack patterns and threat taxonomy
│   ├── spring-clean/          # Session context budget optimizer
│   │   └── SKILL.md           # 4-phase audit workflow
│   └── consolidate/           # Post-session learning extraction
│       ├── SKILL.md           # 5-phase consolidation workflow
│       └── references/        # Routing heuristics
└── README.md                  # This file
```

## Contributing

To add a new skill to this repository:

1. Create a new directory under `skills/` with your skill name
2. Add a `SKILL.md` file with YAML frontmatter and skill content
3. Optionally add `scripts/`, `references/`, or `assets/` directories
4. Update `.claude-plugin/marketplace.json` to include your skill
5. Commit and push your changes

## License

Skills in this repository may have individual licenses. See each skill's directory for details.

- `skill-creator`: Apache License 2.0
