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

## Installation

### Add this Marketplace to Claude Code

```bash
claude plugin marketplace add /Users/user/Documents/Code/my-claude-skills
```

### Install Skills

After adding the marketplace, you can install skills using:

```bash
claude plugin install skill-creator
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
│   └── marketplace.json      # Marketplace configuration
├── skills/
│   └── skill-creator/         # Skill creation guide and tools
│       ├── SKILL.md           # Main skill documentation
│       ├── LICENSE.txt        # Apache 2.0 license
│       ├── scripts/           # Python utilities
│       └── references/        # Workflow and pattern guides
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
