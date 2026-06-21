# AGENTS.md

Guidelines for AI agents working in this repository.

## Repository Overview

This repository contains **Agent Skills** for AI agents following the [Agent Skills specification](https://agentskills.io/specification.md). Skills install to `.agents/skills/` (the cross-agent standard). This repo also serves as a **Claude Code plugin marketplace** via `.claude-plugin/marketplace.json`.

- **Name**: Social Media Content Creation Skills
- **GitHub**: [davideak22/Social-Media-Content-Creation-Skill](https://github.com/davideak22/Social-Media-Content-Creation-Skill)
- **Creator**: David Deak
- **License**: MIT

## Repository Structure

```
Social-Media-Content-Creation-Skill/
├── .claude-plugin/
│   └── marketplace.json   # Claude Code plugin marketplace manifest
├── skills/                # Agent Skills
│   └── skill-name/
│       └── SKILL.md       # Required skill file
├── README.md
├── LICENSE
└── AGENTS.md
```

## Build / Lint / Test Commands

**Skills** are content-only (no build step). Verify manually or with the validation script:
- Run `bash validate-skills.sh`
- Ensure YAML frontmatter is valid
- `name` field matches directory name exactly
- `name` is 1-64 chars, lowercase alphanumeric and hyphens only
- `description` is 1-1024 characters and includes trigger phrases

## Agent Skills Specification

Skills follow the [Agent Skills spec](https://agentskills.io/specification.md).

### Required Frontmatter

```yaml
---
name: skill-name
description: What this skill does and when to use it. Include trigger phrases.
metadata:
  version: 1.0.0
---
```

### Frontmatter Field Constraints

| Field         | Required | Constraints                                                      |
|---------------|----------|------------------------------------------------------------------|
| `name`        | Yes      | 1-64 chars, lowercase `a-z`, numbers, hyphens. Must match dir.   |
| `description` | Yes      | 1-1024 chars. Describe what it does and when to use it.          |
| `license`     | No       | License name (default: MIT)                                      |
| `metadata`    | No       | Key-value pairs (author, version, etc.)                          |

### Name Field Rules

- Lowercase letters, numbers, and hyphens only
- Cannot start or end with hyphen
- No consecutive hyphens (`--`)
- Must match parent directory name exactly

**Valid**: `short-form-content-structures`
**Invalid**: `Short-Form-Content-Structures`, `-short-form-content`, `short--form`

### Optional Skill Directories

```
skills/skill-name/
├── SKILL.md        # Required - main instructions (<500 lines)
├── references/     # Optional - detailed docs loaded on demand
├── scripts/        # Optional - executable code
└── assets/         # Optional - templates, data files
```

## Writing Style Guidelines

### Structure

- Keep `SKILL.md` under 500 lines (move details to `references/` if it grows)
- Use H2 (`##`) for main sections, H3 (`###`) for subsections
- Use bullet points and numbered lists liberally
- Short paragraphs (2-4 sentences max)

### Tone

- Direct and instructional
- Second person ("You are a short-form content creation expert")
- Professional but approachable

### Formatting

- Bold (`**text**`) for key terms
- Code blocks for examples and templates
- Tables for reference data
- No excessive emojis
- **No Em Dashes (Oxford Dashes):** Never use em dashes (—) or Oxford dashes in any copy, templates, or scripts generated. Use other punctuation (colons, commas, hyphens, or parentheses) instead.

### Clarity Principles

- Clarity over cleverness
- Specific over vague
- Active voice over passive
- One idea per section

### Description Field Best Practices

The `description` is critical for skill discovery. Include:
1. What the skill does
2. When to use it (trigger phrases)
3. Related skills for scope boundaries

```yaml
description: "Apply this skill whenever a user wants to generate, brainstorm, or write short-form social media content (TikTok, Reels, Shorts) using proven viral structures. Trigger when the user mentions content templates, video scripts, short-form hooks, or asks how to quickly produce content for a niche. Also use when the user provides a topic and wants a ready-to-film video idea. For general marketing strategy, see social. For video production, see video."
```

## Claude Code Plugin

This repo also serves as a plugin marketplace. The manifest at `.claude-plugin/marketplace.json` lists all skills for installation via:

```bash
/plugin marketplace add davideak22/Social-Media-Content-Creation-Skill
/plugin install social-media-content-creation-skill
```

## Git Workflow

### Branch Naming

- New skills: `feature/skill-name`
- Improvements: `fix/skill-name-description`
- Documentation: `docs/description`

### Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

- `feat: add skill-name skill`
- `fix: improve clarity in hook structures`
- `docs: update README`

### Versioning Rules

Every time a skill or configuration is changed, updated, or fixed, version numbers must be bumped:
1. Increment the skill's local version under the YAML `metadata: version:` field in its `SKILL.md` (e.g., from `1.0.0` to `1.0.1`).
2. Increment the global plugin version in `.claude-plugin/marketplace.json` (e.g., from `1.5.1` to `1.5.2`).

### Pull Request Checklist

- [ ] `name` matches directory name exactly
- [ ] `name` follows naming rules (lowercase, hyphens, no `--`)
- [ ] `description` is 1-1024 chars with trigger phrases
- [ ] `SKILL.md` is under 500 lines
- [ ] Version numbers are updated in both the affected skill's frontmatter and `.claude-plugin/marketplace.json`
- [ ] No sensitive data or credentials
# File Path Conventions

When referencing skill files within this repository, always use **relative paths** to ensure portability and easier navigation. For example, a skill located at:

```
skills/short-form-video-formats/SKILL.md
```

should be linked in markdown as:

[short-form-video-formats](skills/short-form-video-formats/SKILL.md)

**Do NOT** use absolute paths such as `file:///Users/deakdavid/Documents/Portfolio/Social-Media-Content-Creation-Skill/skills/short-form-video-formats/SKILL.md`. Relative links work across different machines and maintain the repository’s self‑contained nature.

This guideline applies to all future additions to the **Related Skills** section or any other place where skill files are referenced.
