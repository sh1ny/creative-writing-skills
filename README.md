# Novel Writing Skills for Claude Code

A complete novel-writing workflow plugin for Claude Code and opencode. From first pitch to final prose — structured, composable, and Obsidian-compatible.

---

## What This Is

A set of eight composable AI skills that guide you through the entire novel-writing process:

- **Plan** your story with pitch documents, synopses, and structured outlines
- **Build a Codex** of characters, locations, items, events, factions, and concepts — all interlinked
- **Write prose** beat by beat, with lean context loading to keep costs manageable
- **Brainstorm** freely without over-committing, **critique** at any scope, **refine** your voice

Every file the plugin creates is **Obsidian-compatible** — proper YAML frontmatter, `[[WikiLinks]]` between entries, folder structure that maps directly to Obsidian's graph view. Write in Claude Code, organize and read in Obsidian.

---

## The Eight Skills

| Command | What it does |
|---------|-------------|
| `/novel-init` | Initializes your novel vault — folders, starter files, first logline, structure template |
| `/codex` | Creates/updates world-building entries with rich frontmatter and wiki links |
| `/pitch` | Develops logline, elevator pitch, premise, short and long synopsis |
| `/outline` | Builds the outline top-down: act structure → chapter outlines → scene breakdowns with beats |
| `/beat` | Writes beat prose one moment at a time, with minimal context loading |
| `/bs` | Brainstorming — captures ideas without over-elaborating, saves to `Notes/` |
| `/critique` | Feedback at any scope: beat, scene, chapter, act, or full outline |
| `/style` | Creates/updates `Style/master.md` — an AI-directive style guide from your own prose |

---

## The Vault Structure

Running `/novel-init` creates this structure in your project directory:

```
MyNovel/
├── Codex/
│   ├── Characters/       ← aria-voss.md, marcus-dune.md ...
│   ├── Locations/        ← thornwood-inn.md, the-capital.md ...
│   ├── Items/
│   ├── Events/
│   ├── Factions/
│   └── Concepts/         ← magic systems, themes, lore rules
├── Story/
│   ├── Pitch/            ← logline.md, elevator-pitch.md, story-premise.md
│   ├── Synopsis/         ← short-synopsis.md, long-synopsis.md
│   ├── Outline/          ← act-structure.md, Act1/chapter-01.md ...
│   └── Chapters/         ← Act1/Chapter01/Scene01.md (actual prose)
├── Style/
│   └── master.md         ← AI-directive style guide, loaded by /beat
├── Notes/                ← brainstorming dumps, critique outputs
└── Meta/
    └── project.md        ← title, genre, premise, structure template, status
```

All files use standard YAML frontmatter. Relationships between entries use `[[WikiLinks]]` — Obsidian renders these as a graph automatically.

---

## The Workflow

### Standard path, from zero:

```
/novel-init   →  Set up vault, pick structure template
/pitch        →  Develop logline, premise, synopsis
/codex        →  Create characters, locations, factions
/outline      →  Act structure → chapters → scenes with beat lists
/style        →  Build style guide from your sample prose
/beat         →  Write prose, one beat at a time
/critique     →  Get feedback at any scope
/bs           →  Brainstorm when stuck, rethink directions
```

**You don't have to start at the top.** If you already have a story concept, skip straight to `/codex` or `/outline`. If you have existing writing, run `/style` first.

### The writing loop (once outlining is done):

```
/beat → /beat → /beat → /critique → /bs → revise outline → /beat
```

Each `/beat` call writes one moment — one action, reaction, or emotional shift — and appends it to the scene file. Beats are the atomic unit: you can regenerate any single beat without touching the rest.

---

## Structure Templates

When you run `/novel-init`, you can bring your own template or pick from the curated menu:

- **Save the Cat** (Blake Snyder) — 15 beats
- **Story Grid** (Shawn Coyne) — 5 commandments per scene
- **Hero's Journey** (Campbell) — 12 stages
- **Three-Act Structure** — classic turning points
- **Four-Act Structure** — pinch points, midpoint reversal
- **Seven-Point Story Structure** (Dan Wells) — hook to resolution
- **Freytag's Pyramid** — 5-part classical arc

The outline skill maps whichever template you choose to your act and chapter breakdown.

---

## The Codex

Every world-building entry is a markdown file with typed frontmatter:

**Characters** — name, aliases, role, status, age, faction, home location, scenes they appear in, related entries, hidden author notes

**Locations** — type, parent location (for nesting: room → building → city → region), inhabitants, atmosphere

**Events** — date in story, participants, location, causes, consequences

**Factions** — leader, members, headquarters, allies, enemies, goals

**Items** — type, rarity, owner, location, history

**Concepts** — magic systems, themes, lore rules, technology

All entries link to each other with `[[WikiLinks]]`. A character's file links to their home location, their faction, the scenes they appear in. Obsidian's graph view makes these relationships visual.

---

## Beat Writing & Context

The `/beat` skill is designed to be lean by default. When writing a beat it loads **only**:

- The beat description (from your scene outline)
- The scene outline (all beats listed, scene metadata)
- The chapter outline (scene summaries only — no prose)
- Relevant Codex entries (characters in the scene + the location)
- `Style/master.md`
- The last ~500 words of the previous scene

It does **not** load your full manuscript, all Codex entries, or the complete outline. This keeps context windows small and costs manageable — no matter how long your novel gets.

**Regeneration is beat-level only.** Ask to redo a single beat; the rest of the scene stays untouched.

---

## Brainstorming

The `/bs` skill uses a three-tag capture system to keep ideas clean:

- **Untagged** — you said it; it's yours
- **`<AI>...</AI>`** — AI suggestion (kept to 2–3 brief options, always marked)
- **`<hidden>...</hidden>`** — author-only secrets: twists, planned reveals, hidden motivations

Notes save to `Notes/brainstorm-[topic].md` with frontmatter linking to related Codex entries and outline sections. When an idea crystallizes, `/bs` suggests whether to formalize it via `/codex` or `/outline`.

---

## Style Guide

`/style` analyzes sample prose you paste — your own writing or prose you admire — and produces `Style/master.md` as **AI instructions**, not human documentation.

Every directive is imperative and example-backed:

> **Emotion:**
> Show emotion through physical action and sensory detail, not labels.
> ✅ "Her hands wouldn't stop moving." — not ❌ "She felt anxious."

The guide covers: Voice & Tone, Sentence Structure, POV & Interiority, Dialogue, Description, Pacing, Emotion, Formatting, and an explicit Avoid list. The `/beat` skill loads it automatically every time it writes.

Run `/style` again after a revision session to keep the guide current as your voice evolves.

---

## Installation

### Claude Code

```bash
# Install from GitHub marketplace
claude plugin marketplace add sh1ny/creative-writing-skills
claude plugin install creative-writing-skills@creative-writing-skills

# Or install from a local clone
git clone https://github.com/sh1ny/creative-writing-skills.git
claude plugin marketplace add ./creative-writing-skills
claude plugin install creative-writing-skills
```

Slash commands (`/novel-init`, `/codex`, `/pitch`, etc.) are included automatically.

### opencode

Clone the repository and point opencode at it. Slash commands live in `.opencode/commands/` and are invoked as `/project:novel-init`, `/project:codex`, `/project:beat`, etc.

The skill SKILL.md files are tool-agnostic and work in opencode without changes.

### Claude.ai

Download `.skill` files from the [Releases page](https://github.com/sh1ny/creative-writing-skills/releases) and upload them to Claude.ai via Settings → Capabilities → Skills.

---

## Obsidian Setup (Optional)

Open your novel's project directory as an **Obsidian vault**. You get:

- **Graph view** — see all Codex relationships visually
- **Backlinks** — every `[[WikiLink]]` is navigable
- **Dataview queries** — filter characters by role, scenes by status, etc.
- **Local search** — full-text search across your entire manuscript and Codex

No MCP server required. Claude Code writes the files; Obsidian reads them.

---

## Development

### Rebuild skill packages
```bash
python scripts/create_skill_zips.py
```

### Modify a skill
1. Edit `creative-writing-skills/cw-[name]/SKILL.md`
2. Update `references/` if needed
3. Rebuild: `python scripts/create_skill_zips.py`
4. Test in a novel project directory

### Version
Defined in `.claude-plugin/marketplace.json` → `metadata.version`. Current: `1.0.0`

---

## License

Apache License 2.0 — see [LICENSE](LICENSE).
