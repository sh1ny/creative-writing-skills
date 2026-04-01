# Creative Writing — Agents

Four specialized agents for the novel-writing workflow. Place this folder at `.opencode/agents/` in the novel project root (or in `~/.config/opencode/agents/` to use globally).

---

## Agent Overview

| Agent | Mode | Purpose | Model Suggestion |
|-------|------|---------|-----------------|
| `cw-write` | primary | Prose writing, vault file management | Claude Opus 4.6 |
| `cw-plan` | primary | Outlining, structure decisions, critique | Claude Sonnet 4.5 |
| `cw-brainstorm` | subagent | Free-form ideation, no file writes | Claude Sonnet 4.5 |
| `cw-explore` | subagent | Read-only vault navigation | Claude Haiku 4 |

Switch between primary agents with **Tab**. Invoke subagents with `@cw-brainstorm` or `@cw-explore`.

---

## Model Recommendations for Creative Writing

Based on 2025-2026 benchmarks (Mazur Writing Score + LM Arena human preference):

| Model | Strengths | Best For |
|-------|-----------|----------|
| **Claude Opus 4.6** | #1 Mazur Writing Score (8.561), 128K output tokens, superior character consistency | `/beat` prose writing — best quality |
| **Claude Sonnet 4.5** | Strong prose (8.169 Mazur), much cheaper than Opus | Planning, outlining, brainstorming |
| **Gemini 3 Pro** | #1 LM Arena creative writing (human preference), most natural voice | Alternative primary if you want less "AI feel" |
| **Claude Haiku 4** | Fast and cheap | Exploration, search, read-only tasks |
| **GPT-5.2** | Best for marketing copy | Not recommended for fiction — blander voice |

**Recommended setup:**
- `cw-write` → Claude Opus 4.6 (quality matters most here)
- `cw-plan` + `cw-brainstorm` → Claude Sonnet 4.5 (good prose, lower cost)
- `cw-explore` → Claude Haiku 4 (fast reads, minimal cost)

Update the `model:` field in each `.md` file to match your available provider/model IDs.

---

## How Agents Work Together

```
User → @cw-write (primary)
           ├─ delegates to @cw-explore: "find Codex entry for this character"
           ├─ delegates to @cw-explore: "read last 500 words of previous scene"
           └─ writes the beat

User → @cw-plan (primary)
           ├─ delegates to @cw-explore: "read current outline"
           └─ provides structural critique or outline

User: "@cw-brainstorm what if the antagonist..."
           └─ @cw-brainstorm explores ideas, no files touched
              └─ User takes what works → @cw-plan → @cw-write
```

---

## Installation

These are **project-level agents** — they override global agents of the same name when you're working in this vault.

For **global use** (available across all your novel projects), copy the `.md` files to:
```
~/.config/opencode/agents/
```

For **per-project use**, the `.opencode/agents/` folder in the vault root is already the right place.

---

## Customizing Models

Edit the `model:` field in each agent file. Use the format `provider/model-id`:

```yaml
model: anthropic/claude-opus-4-5        # Claude Opus 4.5
model: anthropic/claude-sonnet-4-5      # Claude Sonnet 4.5
model: anthropic/claude-haiku-4-20250514 # Claude Haiku 4
model: google/gemini-3-pro              # Gemini 3 Pro (alternative)
model: openai/gpt-5.2                   # GPT-5.2 (not recommended for fiction)
```

Run `opencode models` to see all available models for your configured providers.
