# Creative Writing — Slash Commands (opencode)

Eight commands covering the full novel-writing workflow. In opencode, invoke with `/project:<command>`.

## Recommended Workflow

```
/project:novel-init → /project:pitch → /project:codex → /project:outline → /project:style → /project:beat → /project:critique → /project:bs → /project:beat
```

---

## Commands

| Command | Purpose |
|---------|---------|
| `/project:novel-init` | Initialize a new novel vault (scaffold + first logline) |
| `/project:pitch` | Develop logline, elevator pitch, premise, and synopses |
| `/project:codex` | Create/update Codex entries (characters, locations, items, events, factions, concepts) |
| `/project:outline` | Build outline top-down (act → chapter → scene → beats) |
| `/project:beat <Act#/Chapter#/Scene#> [beat #]` | Write beat prose — the atomic unit of novel writing |
| `/project:style` | Create or update `Style/master.md` from sample writing |
| `/project:critique <beat\|scene\|chapter\|outline>` | Get structured feedback at any scope |
| `/project:bs` | Brainstorm and capture exploratory ideas |

---

## Usage Examples

```
/project:novel-init
/project:pitch I have a logline: A retired hitman...
/project:codex Create a character entry for Elena Vasquez
/project:outline Build act structure for a three-act thriller
/project:beat Act1/Chapter01/Scene02 beat 3
/project:style
/project:critique scene
/project:bs What if the antagonist is actually the protagonist's father?
```

---

## Vault Structure

All commands write to an **Obsidian-compatible vault**:

```
MyNovel/
├── Codex/
│   ├── Characters/
│   ├── Locations/
│   ├── Items/
│   ├── Events/
│   ├── Factions/
│   └── Concepts/
├── Story/
│   ├── Pitch/
│   ├── Synopsis/
│   ├── Outline/
│   └── Chapters/Act1/Chapter01/Scene01.md
├── Style/
│   └── master.md
├── Notes/
└── Meta/
    └── project.md
```

All files use YAML frontmatter. `[[WikiLinks]]` connect related Codex entries.

---

## Key Design Decisions

- **`/project:beat` loads minimal context** — only what's needed to write the current beat. Context stays lean and cost-manageable.
- **Top-down outline discipline** — act structure must exist before chapter outlines; chapter outlines before scene breakdowns.
- **One style guide** — `Style/master.md` only. `/project:beat` loads it automatically.
- **Codex is canonical** — all world-building lives in `Codex/`. `/project:beat` and `/project:outline` reference it.
