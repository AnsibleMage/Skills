# Claude Code Skills

> A collection of custom skill definitions for Claude Code, enabling structured AI-assisted workflows through slash commands.

## Overview

This repository contains reusable **Claude Code Skills** -- modular instruction sets that extend Claude Code's capabilities with specialized workflows. Each skill is invoked via a slash command (e.g., `/commit-push`, `/translation-specialist`) and provides a structured, repeatable process for common development tasks.

## Skills

| Skill | Command | Description |
|-------|---------|-------------|
| **Analyze** | `/analyze` | Run 4-Layer prompt analysis (Lexical, Syntactic, Discourse, Pragmatic) and recommend optimal chains/agents/skills |
| **Claude Strategy** | `/claude-strategy` | Generate a project-optimized Claude Code usage strategy document mapping chains, agents, and skills to project needs |
| **Commit Push** | `/commit-push` | Stage, commit (Conventional Commits format), and push changes to origin |
| **Memory Save** | `/memory-save` | Save session work to `~/.claude/memory/` with deduplication and `YYMM_SEQ_keyword.md` naming |
| **PR Review** | `/pr-review` | Review a PR or git diff, producing a structured report in `.pr-reviews/` |
| **Project Review** | `/project-review` | Full project review covering architecture, structure, and maintainability |
| **README Gen** | `/readme-gen` | Analyze a project folder and auto-generate README.md (English) and README_KO.md (Korean) |
| **Translation Specialist** | `/translation-specialist` | Context-aware professional translation with 4-Layer linguistic analysis, supporting 6 domains and 4 translation strategies |
| **Vibe Dev** | `/vibe-dev` | Document-driven AI pair programming methodology across 4 phases: Investigate, Define, Develop, Report |

## Project Structure

```
Skills/
├── analyze/
│   └── SKILL.md              # 4-Layer prompt analysis skill
├── claude-strategy/
│   ├── SKILL.md               # Project strategy generator
│   └── references/
│       └── strategy-template.md   # 12-section strategy template
├── commit-push/
│   └── SKILL.md               # Git commit & push automation
├── memory-save/
│   └── SKILL.md               # Session memory persistence
├── pr-review/
│   └── SKILL.md               # Pull request review workflow
├── project-review/
│   └── SKILL.md               # Full project audit workflow
├── readme-gen/
│   └── SKILL.md               # README auto-generation
├── translation-specialist/
│   ├── SKILL.md               # Professional translation engine
│   ├── reference.md           # Classification systems & keyword dictionaries
│   ├── examples.md            # 4 real-world translation examples
│   └── linguistic_analysis.py # Automated linguistic analysis tool
└── vibe-dev/
    ├── SKILL.md               # Document-driven development methodology
    ├── REVIEW.md              # Review guidelines
    └── references/
        ├── checkpoint-protocol.md  # Resume protocol for interrupted sessions
        ├── document-templates.md   # Templates for all project documents
        ├── error-recovery.md       # Error handling & recovery procedures
        ├── phase1-investigate.md   # Phase 1: Research & investigation
        ├── phase2-define.md        # Phase 2: Specification & planning
        ├── phase3-develop.md       # Phase 3: TDD development
        ├── phase4-report.md        # Phase 4: Review & reporting
        ├── usage-examples.md       # Practical usage examples
        └── zero-guess-protocol.md  # Zero-assumption coding protocol
```

## Key Features

- **Modular Design**: Each skill is self-contained with its own `SKILL.md` definition file
- **Slash Command Integration**: All skills are invokable via Claude Code's `/command` system
- **Structured Workflows**: Skills define step-by-step processes with clear inputs, outputs, and quality checks
- **Reference Materials**: Complex skills include supporting documentation in `references/` subdirectories
- **Multilingual Support**: Translation skill supports 6 domains with academic-grade methodology (ISO 17100, Nida's Functional Equivalence)
- **Quality Assurance**: Built-in review and verification steps in each workflow

## Usage

### In Claude Code

Skills are loaded by placing them in the Claude Code skills directory. Once installed, invoke any skill by typing its slash command:

```
/analyze "Build a REST API for user management"
/commit-push
/vibe-dev Create a weather dashboard app
/translation-specialist
```

### Skill Definition Format

Each skill is defined in a `SKILL.md` file with YAML frontmatter:

```yaml
---
name: skill-name
description: What the skill does
user-invocable: true
allowed-tools: [Bash, Read, Write]
---

# Skill instructions follow in Markdown...
```

## License

MIT

---

*Built for [Claude Code](https://claude.ai/code) by AnsibleMage*
