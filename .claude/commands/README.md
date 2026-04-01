# Creative Writing — Slash Commands

Eight commands covering the full novel-writing workflow. Commands are composable and designed to work top-down, but you can enter at any level.

## Recommended Workflow

```
/novel-init → /pitch → /codex → /outline → /style → /beat → /critique → /bs → /beat
```

---

## Commands

| Command | Purpose |
|---------|---------|
| `/novel-init` | Initialize a new novel vault (scaffold + first logline) |
| `/pitch` | Develop logline, elevator pitch, premise, and synopses |
| `/codex` | Create/update Codex entries (characters, locations, items, events, factions, concepts) |
| `/outline` | Build outline top-down (act → chapter → scene → beats) |
| `/beat <Act#/Chapter#/Scene#> [beat #]` | Write beat prose — the atomic unit of novel writing |
| `/style` | Create or update `Style/master.md` from sample writing |
| `/critique <beat\|scene\|chapter\|outline>` | Get structured feedback at any scope |
| `/bs` | Brainstorm and capture exploratory ideas |

---

## Usage Examples

```
/novel-init
/pitch I have a logline: A retired hitman...
/codex Create a character entry for Elena Vasquez
/outline Build act structure for a three-act thriller
/beat Act1/Chapter01/Scene02 beat 3
/style
/critique scene
/bs What if the antagonist is actually the protagonist's father?
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

- **`/beat` loads minimal context** — only what's needed to write the current beat. Context stays lean and cost-manageable.
- **Top-down outline discipline** — act structure must exist before chapter outlines; chapter outlines before scene breakdowns.
- **One style guide** — `Style/master.md` only. `/beat` loads it automatically.
- **Codex is canonical** — all world-building lives in `Codex/`. `/beat` and `/outline` reference it.
