# Installation Guide

Step-by-step setup for Claude Code, opencode, and Claude.ai.

---

## Claude Code

### Prerequisites

- [Claude Code](https://claude.ai/code) installed and authenticated
- Git (for cloning)

### Install from GitHub

```bash
claude plugin marketplace add sh1ny/creative-writing-skills
claude plugin install creative-writing-skills@creative-writing-skills
```

### Install from local clone

```bash
git clone https://github.com/sh1ny/creative-writing-skills.git
cd creative-writing-skills
claude plugin marketplace add .
claude plugin install creative-writing-skills
```

### Verify

```bash
claude plugin
```

You should see `creative-writing-skills` listed. In any Claude Code session, `/novel-init` should now autocomplete.

### Uninstall

```bash
claude plugin uninstall creative-writing-skills
```

---

## opencode

### Prerequisites

- [opencode](https://opencode.ai) installed
- At least one LLM provider configured (Anthropic recommended — see model notes below)

### Install

```bash
git clone https://github.com/sh1ny/creative-writing-skills.git
```

Copy or symlink the two opencode directories into your novel project:

```bash
cp -r creative-writing-skills/.opencode/commands /your/novel/project/.opencode/commands
cp -r creative-writing-skills/.opencode/agents   /your/novel/project/.opencode/agents
```

Or, if you want the skills available globally, copy them into your opencode config directory:

```bash
cp -r creative-writing-skills/.opencode/agents ~/.config/opencode/agents
```

> **Note:** Commands (`.opencode/commands/`) must live in the project — they're project-specific. Agents can be global or per-project.

### Verify

Open opencode in your novel project directory. Commands should appear as `/project:novel-init`, `/project:beat`, etc. Agents appear in the **Tab** cycle (`cw-write`, `cw-plan`) and via `@` mention (`@cw-brainstorm`, `@cw-explore`).

### Agents setup

Four agents are included in `.opencode/agents/`. They are pre-configured with sensible defaults but you should set the model IDs to match your provider setup.

Edit each `.md` file's `model:` field:

| Agent file | Default model | Recommended |
|-----------|--------------|-------------|
| `cw-write.md` | `anthropic/claude-opus-4-5` | `anthropic/claude-opus-4-5` or `anthropic/claude-opus-4-6` if available |
| `cw-plan.md` | `anthropic/claude-sonnet-4-5` | `anthropic/claude-sonnet-4-5` |
| `cw-brainstorm.md` | `anthropic/claude-sonnet-4-5` | `anthropic/claude-sonnet-4-5` |
| `cw-explore.md` | `anthropic/claude-haiku-4-20250514` | `anthropic/claude-haiku-4-20250514` |

Run `opencode models` to see all model IDs available for your configured providers.

**Gemini alternative:** If you prefer Gemini 3 Pro's more natural prose voice as your primary writing model, swap `cw-write.md` to `google/gemini-3-pro`.

---

## Claude.ai

### Prerequisites

- A Claude.ai account (Pro or higher recommended — Skills require extended context)

### Install

1. Go to the [Releases page](https://github.com/sh1ny/creative-writing-skills/releases)
2. Download the `.skill` files for the skills you want
3. In Claude.ai: **Settings → Capabilities → Skills → Upload skill**
4. Upload each `.skill` file individually

Available skills to upload:

| File | What it installs |
|------|-----------------|
| `cw-novel-init.skill` | `/novel-init` |
| `cw-codex.skill` | `/codex` |
| `cw-pitch.skill` | `/pitch` |
| `cw-outline.skill` | `/outline` |
| `cw-beat.skill` | `/beat` |
| `cw-brainstorming.skill` | `/bs` |
| `cw-story-critique.skill` | `/critique` |
| `cw-style-skill-creator.skill` | `/style` |

Install all eight for the full workflow, or just the ones you need.

### Verify

Start a new Claude.ai conversation. Type `/` — the installed skills should appear in the autocomplete menu.

---

## Obsidian (Optional — Read-Only)

Obsidian is not required but makes your vault navigable as a knowledge graph.

1. Download and install [Obsidian](https://obsidian.md) (free)
2. **Open folder as vault** → select your novel project directory
3. Recommended plugins (all free, via Community Plugins):
   - **Dataview** — query your Codex by frontmatter fields
   - **Graph Analysis** — richer graph view of WikiLink relationships
   - **Templater** — optional, if you want hotkey-based entry creation

No configuration needed beyond opening the folder. WikiLinks and frontmatter work out of the box.

---

## Model Recommendations

Based on 2026 creative writing benchmarks:

| Model | Strength | Use for |
|-------|----------|---------|
| **Claude Opus 4.6** | #1 Mazur Writing Score — best character consistency, structured long-form | `/beat` prose writing |
| **Claude Sonnet 4.5** | Strong prose at ~5× lower cost than Opus | Planning, outlining, brainstorming |
| **Gemini 3 Pro** | #1 LM Arena human preference — most natural-sounding prose voice | Alternative to Opus for `/beat` |
| **Claude Haiku 4** | Fastest and cheapest | Vault exploration, search tasks |
| **GPT-5.2** | Best for marketing copy, weaker fiction voice | Not recommended for novel prose |

---

## Troubleshooting

**Commands don't appear in Claude Code**
- Run `claude plugin` to confirm the plugin is listed
- Try `claude plugin uninstall creative-writing-skills` then reinstall

**Commands don't appear in opencode**
- Confirm `.opencode/commands/` exists in the project root (not a parent directory)
- Restart opencode after adding the commands folder

**Agents don't appear in opencode**
- Confirm `.opencode/agents/` exists in project root or `~/.config/opencode/agents/`
- Check that each agent `.md` file has valid YAML frontmatter (no tabs, correct indentation)
- Run `opencode models` to verify your configured providers match the `model:` fields

**Model ID not found**
- Run `opencode models` to list available IDs for your providers
- Update the `model:` field in the relevant agent `.md` file to match exactly

**Skill files not installing on Claude.ai**
- Ensure the `.skill` file is from the latest release
- Skills require Claude.ai Pro or higher — free tier does not support Skills
