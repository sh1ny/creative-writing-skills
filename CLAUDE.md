# CLAUDE.md

This file provides guidance to Claude Code (and compatible agents like opencode) when working with this repository.

## Repository Overview

This repository contains a Claude Code plugin providing a **complete novel-writing workflow** with Obsidian-compatible vault output. It covers the full arc from first pitch to beat-level prose writing, with a structured Codex for all world-building.

**Key insight:** Skills are composable and designed to work top-down: `/novel-init` → `/pitch` → `/codex` → `/outline` → `/style` → `/beat`. You can also enter at any level.

## Plugin Architecture

### Structure
- `creative-writing-skills/` - Contains eight skill directories (cw-*)
- Each skill directory contains:
  - `SKILL.md` - The main skill prompt/instructions (read by the AI)
  - `references/` - Reference documentation used by the skill
- `.claude-plugin/marketplace.json` - Plugin manifest (v1.0.0)
- `.claude/commands/` - Slash commands for each skill
- `zips/` - Packaged `.skill` files for Claude.ai users
- `scripts/` - Build utilities
- `.opencode/agents/` - Specialized agents for opencode users

### The Eight Skills

1. **cw-novel-init** — Initializes the vault scaffold, picks structure template, generates first logline
2. **cw-codex** — Creates/updates Codex entries (characters, locations, items, events, factions, concepts)
3. **cw-pitch** — Develops logline, elevator pitch, premise, synopses
4. **cw-outline** — Builds story outline top-down (act → chapter → scene → beats)
5. **cw-beat** — Writes beat prose with lean context loading
6. **cw-brainstorming** — Captures exploratory ideas in minimal working notes
7. **cw-story-critique** — Critiques at any scope (beat/scene/chapter/act/outline)
8. **cw-style-skill-creator** — Creates/updates `Style/master.md` from sample writing

### Vault Structure (Obsidian-compatible)

Every novel project is a vault:
```
MyNovel/
├── Codex/
│   ├── Characters/         # [[CharacterName]] wiki links
│   ├── Locations/
│   ├── Items/
│   ├── Events/
│   ├── Factions/
│   └── Concepts/
├── Story/
│   ├── Pitch/              # logline, elevator pitch, premise
│   ├── Synopsis/           # short and long synopsis
│   ├── Outline/            # act-structure.md, Act1/chapter-01.md, etc.
│   └── Chapters/           # Act1/Chapter01/Scene01.md (actual prose)
├── Style/
│   └── master.md           # AI-directive style guide (loaded by /beat)
├── Notes/                  # brainstorming dumps, critique outputs
└── Meta/
    └── project.md          # title, genre, premise, structure template, status
```

All files use YAML frontmatter. Obsidian wiki links (`[[FileName]]`) connect related entries for graph view.

### Composability & Workflow

**Standard novel workflow:**
```
/novel-init → /pitch → /codex (populate world) → /outline (act → chapters → scenes)
           → /style (from sample writing) → /beat (write prose beat by beat)
           → /critique (review) → /bs (rethink) → /beat (revise)
```

**Enter at any level** — you don't have to start from `/novel-init` if the project already exists.

## opencode Agents

Four specialized agents ship with this plugin for opencode users. They live in `.opencode/agents/`.

| Agent | Mode | Purpose | Suggested Model |
|-------|------|---------|----------------|
| `cw-write` | primary | Prose writing, vault file management | Claude Opus 4.6 |
| `cw-plan` | primary | Outlining, structure decisions, critique | Claude Sonnet 4.5 |
| `cw-brainstorm` | subagent | Free-form ideation, no file writes | Claude Sonnet 4.5 |
| `cw-explore` | subagent | Read-only vault navigation | Claude Haiku 4 |

**Usage:**
- Switch between primary agents with **Tab**
- Invoke subagents: `@cw-brainstorm what if the antagonist...` or `@cw-explore find codex entry for Marcus`
- Primary agents automatically delegate to subagents when useful

**Model recommendations** (2026 creative writing benchmarks):
- **Claude Opus 4.6** — #1 Mazur Writing Score, best character consistency → use for `/beat`
- **Gemini 3 Pro** — #1 LM Arena human preference, most natural prose voice → good alternative primary
- **Claude Sonnet 4.5** — strong prose at lower cost → use for planning, brainstorming
- **GPT-5.2** — best for marketing copy, weaker for fiction voice

See `.opencode/agents/README.md` for full details and model ID formats.

## Custom Slash Commands

| Command | Skill | Purpose |
|---------|-------|---------|
| `/novel-init` | cw-novel-init | Initialize new novel vault |
| `/codex` | cw-codex | Create/update world-building entries |
| `/pitch` | cw-pitch | Develop pitch, logline, synopses |
| `/outline` | cw-outline | Build outline top-down |
| `/beat` | cw-beat | Write beat prose |
| `/bs` | cw-brainstorming | Brainstorm ideas |
| `/critique` | cw-story-critique | Get feedback at any scope |
| `/style` | cw-style-skill-creator | Create/update style guide |

## Development Commands

### Building Skill Packages
```bash
python scripts/create_skill_zips.py
```
Creates individual `.skill` files (ZIP format) in `zips/` for uploading to Claude.ai.

### Testing the Plugin Locally
```bash
# Add as local marketplace
claude plugin marketplace add .

# Install the plugin
claude plugin install creative-writing-skills

# List installed plugins
claude plugin
```

### Making Changes to Skills

When modifying a skill:
1. Edit the `SKILL.md` in the appropriate skill directory
2. Update `references/` files if adding/changing reference documentation
3. Rebuild packages: `python scripts/create_skill_zips.py`
4. Test in an actual novel project directory

## Skill Design Patterns

### Source Tagging (Brainstorming)
- **Untagged** = user stated this
- **`<AI>...</AI>`** = AI suggestions/possibilities (max 2-3 options)
- **`<hidden>...</hidden>`** = Author-only secrets (twists, reveals)

### Style Guide Format
Style guides (`Style/master.md`) are **AI instructions** (directive), not human documentation:
- Use imperative form: "Use short sentences during action"
- Always include examples extracted from the author's own prose
- Pattern + Example format throughout

### Beat Context Loading (Lean by Design)
The `/beat` skill loads ONLY:
- Beat description + scene outline
- Chapter outline (scene summaries only — no prose)
- Relevant Codex entries (characters in scene + location)
- `Style/master.md`
- Last ~500 words of previous scene

This keeps context lean and costs manageable. Regeneration is at the beat level only.

### Obsidian Compatibility
- All frontmatter uses standard YAML
- Relationships use `[[WikiLinks]]`
- Tags in frontmatter drive filtering
- Folder structure matches vault conventions

## Version Management

Version is defined in `.claude-plugin/marketplace.json` under `metadata.version`.

When releasing:
1. Update version in `marketplace.json`
2. Run `python scripts/create_skill_zips.py` to rebuild packages
3. Create GitHub release with updated `.skill` files from `zips/`
4. Update README.md if functionality changes
