# Vault Templates for /novel-init

This file contains all templates that `/novel-init` uses to scaffold a new novel project. Each template is production-ready with proper frontmatter and structure.

---

## Project Root: `Meta/project.md`

```yaml
---
title: ""
genre: ""
premise: ""
structure-template: ""
status: drafting
created: ""
version: "1.0"
tags: [meta, project]
---

# 

## Project Notes

_Add project-level notes here._

## Workflow Status

- [ ] Pitch & Logline (`/pitch`)
- [ ] Codex populated (`/codex`)
- [ ] Act structure outlined (`/outline`)
- [ ] Style guide created (`/style`)
- [ ] Writing in progress (`/beat`)
```

---

## Story/Pitch/logline.md

```yaml
---
type: pitch
subtype: logline
status: draft
version: 1
tags: [pitch, story]
---

# Logline

_Write one to three sentences that capture the essential conflict, protagonist, and stakes of your story._

_Use this format as a guide:_
_When [inciting incident], [protagonist] must [central conflict] or [stakes if they fail]._
```

---

## Style/master.md

```yaml
---
type: style-guide
subtype: master
status: needs-sample
tags: [style, meta]
---

# Style Guide

_This guide is empty until you provide sample writing. Run `/style` with 1,000+ words of your prose to generate personalized writing directives._

---

## How to Create Your Style Guide

1. **Write a sample scene** (1,000+ words) in your intended voice—action scene, dialogue-heavy scene, or the type of scene you find hardest
2. **Run `/style`** and paste your sample when prompted
3. **The style skill will analyze** your sentence structure, word choices, dialogue patterns, and narrative voice
4. **Review the generated directives** and edit as needed
5. **Save to this file**—it becomes your prose writing standard

---

## Why This File Exists

The style guide contains **directives** (imperative instructions), not descriptions. When `/beat` writes prose, it reads these directives and applies them.

_Good directive_: "Use short, punchy sentences during action sequences."

_Not a directive_: "This project uses short sentences during action."

---

## Your Directives

_After running `/style`, directives will appear here in this format:_

### Sentence Structure
- _Directive_
- _Directive_

### Word Choice
- _Directive_
- _Directive_

### Dialogue
- _Directive_
- _Directive_

### Narrative Voice
- _Directive_
- _Directive_

### POV & Interiority
- _Directive_
- _Directive_

### Pacing & Rhythm
- _Directive_
- _Directive_

---

## Voice Notes

_Personal notes on maintaining your narrative voice:_
- _Note_
- _Note_
```

---

## Codex/Characters/_README.md

```yaml
---
type: reference
folder: characters
tags: [codex, reference]
---

# Codex: Characters

This folder contains character entries for your story. Each entry is a markdown file with YAML frontmatter.

---

## Entry Schema

```yaml
---
type: character
name: ""
role: ""              # protagonist | antagonist | supporting | minor
status: ""            # alive | dead | unknown
gender: ""            # (optional)
age: ""                # (optional)
faction: []            # array of faction names
home-location: null    # [[LocationName]]
appearance: ""         # 2-3 sentences
personality: ""        # key traits
backstory: ""          # few sentences
motivation: ""         # what they want most
relationships: ""      # important connections
arc: ""                # how they change
appears-in: []         # [[Act1/Chapter3/Scene2]] - fill as you write
related: []            # [[CharacterName]], [[LocationName]]
aliases: []            # alternative names
tags: [character]
---

# Character Name

_Author notes, secrets, hidden information (use >[!hidden] callout)_
```

---

## Creating Character Entries

**Option 1**: Run `/codex` and select "Character"

**Option 2**: Copy `character-template.md` from this folder, rename it, and fill in the fields.

---

## Wiki Links

Use `[[CharacterName]]` syntax to link to related entries in your prose and outlines. Obsidian will recognize these as internal links.

---

## Role Definitions

- **Protagonist**: Main character whose journey drives the story
- **Antagonist**: Opposes the protagonist (can be a person, force, or internal)
- **Supporting**: Significant characters who affect the protagonist's journey
- **Minor**: Appear in one or two scenes, not central to the plot
```

---

## Codex/Locations/_README.md

```yaml
---
type: reference
folder: locations
tags: [codex, reference]
---

# Codex: Locations

This folder contains location entries for your story. Each entry is a markdown file with YAML frontmatter.

---

## Entry Schema

```yaml
---
type: location
name: ""
location-type: ""      # city | building | region | room | world | other
status: ""             # active | ruins | destroyed | unknown
inhabitants: []        # who lives here
parent-location: ""    # (optional) larger containing location
description: ""        # 2-3 sentences
atmosphere: ""         # mood of the place
history: ""            # how it came to be
notable-features: []   # landmarks, rooms, regions
connected-to: []       # related Codex entries
appears-in: []         # [[Act1/Chapter3/Scene2]] - fill as you write
related: []
aliases: []
tags: [location]
---

# Location Name

_Additional notes, secrets, hidden details (use >[!hidden] callout)_
```

---

## Creating Location Entries

**Option 1**: Run `/codex` and select "Location"

**Option 2**: Copy `location-template.md` from this folder, rename it, and fill in the fields.

---

## Location Hierarchy

Use `parent-location` to create nested locations:
- **The Silver City** (parent)
  - **The Merchant Quarter** (child)
  - **The Noble District** (child)
  - **The Whispering Tavern** (child, parent is Merchant Quarter)

---

## Wiki Links

Use `[[LocationName]]` syntax to link locations in your prose, Codex entries, and outlines.
```

---

## Codex/Items/_README.md

```yaml
---
type: reference
folder: items
tags: [codex, reference]
---

# Codex: Items

This folder contains item entries for your story. Each entry is a markdown file with YAML frontmatter.

---

## Entry Schema

```yaml
---
type: item
name: ""
item-type: ""          # weapon | artifact | document | clothing | other
rarity: ""             # common | uncommon | rare | unique
owner: ""              # who currently has it
location: ""           # where it is
description: ""        # 2-3 sentences
history: ""            # origin and past
significance: ""       # why it matters to the story
current-status: ""     # where the story finds it
appears-in: []         # [[Act1/Chapter3/Scene2]] - fill as you write
related: []
aliases: []
tags: [item]
---

# Item Name

_Additional notes, secrets, hidden details (use >[!hidden] callout)_
```

---

## Creating Item Entries

**Option 1**: Run `/codex` and select "Item"

**Option 2**: Copy `item-template.md` from this folder, rename it, and fill in the fields.

---

## Types of Items

- **Weapons**: Swords, daggers, firearms, magical weapons
- **Artifacts**: Magical objects, ancient relics, cursed items
- **Documents**: Letters, journals, maps, contracts
- **Clothing**: Armor, heirlooms, disguises
- **Other**: Anything that doesn't fit above categories
```

---

## Codex/Events/_README.md

```yaml
---
type: reference
folder: events
tags: [codex, reference]
---

# Codex: Events

This folder contains event entries for your story. Each entry is a markdown file with YAML frontmatter.

---

## Entry Schema

```yaml
---
type: event
name: ""
event-type: ""         # historical | scene | turning-point | offscreen
timeline: ""           # when it occurs (Day 3, Year 412, Before the story)
characters: []         # who participates
location: ""           # where it takes place
summary: ""            # what happens
causes: []             # events that led to this
consequences: []        # what happens afterward
impact: ""             # effect on the story
appears-in: []         # [[Act1/Chapter3/Scene2]] - fill as you write
related: []
aliases: []
tags: [event]
hidden: ""              # author-only secrets (use >[!hidden] callout)
---

# Event Name

_Additional narrative details, author notes (use >[!hidden] callout for secrets)_
```

---

## Event Type Definitions

- **Historical**: Events that happened before the story begins
- **Scene**: Events that occur within a specific scene
- **Turning-Point**: Major story moments that change the direction
- **Offscreen**: Events referenced but not dramatized

---

## Creating Event Entries

**Option 1**: Run `/codex` and select "Event"

**Option 2**: Copy `event-template.md` from this folder, rename it, and fill in the fields.
```

---

## Codex/Factions/_README.md

```yaml
---
type: reference
folder: factions
tags: [codex, reference]
---

# Codex: Factions

This folder contains faction entries for your story. Each entry is a markdown file with YAML frontmatter.

---

## Entry Schema

```yaml
---
type: faction
name: ""
faction-type: ""       # guild | government | religion | family | other
status: ""             # active | disbanded | secret | other
leader: ""             # who leads
members: []            # known members
headquarters: ""       # base of operations
description: ""        # 2-3 sentences
history: ""            # how it came to be
goals: ""              # what they want
structure: ""          # how organized
culture: ""            # rituals, traditions, beliefs
allies: []             # friendly factions
enemies: []            # opposing factions
appears-in: []         # [[Act1/Chapter3/Scene2]] - fill as you write
related: []
aliases: []
tags: [faction]
---

# Faction Name

_Additional notes, secrets, hidden details (use >[!hidden] callout)_
```

---

## Creating Faction Entries

**Option 1**: Run `/codex` and select "Faction"

**Option 2**: Copy `faction-template.md` from this folder, rename it, and fill in the fields.
```

---

## Codex/Concepts/_README.md

```yaml
---
type: reference
folder: concepts
tags: [codex, reference]
---

# Codex: Concepts

This folder contains concept entries for your story. Each entry is a markdown file with YAML frontmatter.

---

## Entry Schema

```yaml
---
type: concept
name: ""
concept-type: ""       # magic-system | theme | lore-rule | technology | religion | other
description: ""        # 2-3 sentences explaining what it is
rules: ""               # how it works
limitations: ""         # costs, restrictions
perception: ""          # how people in the world view it
notes: ""               # additional author notes
appears-in: []         # [[Act1/Chapter3/Scene2]] - fill as you write
related: []
aliases: []
tags: [concept]
---

# Concept Name

_Additional explanation, edge cases, or hidden lore (use >[!hidden] callout)_
```

---

## Concept Type Definitions

- **Magic System**: Rules governing magical abilities
- **Theme**: Central ideas explored in the story
- **Lore Rule**: World-specific rules (gravity, physics variants)
- **Technology**: Notable tech in your world
- **Religion**: Beliefs, gods, worship practices
- **Other**: Anything that doesn't fit above

---

## Creating Concept Entries

**Option 1**: Run `/codex` and select "Concept"

**Option 2**: Copy `concept-template.md` from this folder, rename it, and fill in the fields.
```

---

## Notes/_README.md

```yaml
---
type: reference
folder: notes
tags: [notes, scratchpad]
---

# Notes

This folder is your scratchpad for ideas, fragments, and exploration that doesn't fit elsewhere yet.

---

## Purpose

- Dump ideas that aren't ready for Codex or outlines
- Explore "what if" scenarios
- Collect fragments, images, dialogue snippets
- Brainstorm without committing

---

## Workflow

**Use `/bs`** (brainstorming) to fill this folder with exploratory notes.

Brainstorming produces exploratory, multiple-option notes with `[TBD]` markers. Once an idea is finalized, move it to the appropriate Codex folder or outline.

---

## File Naming

- Use descriptive names: `tavern-idea.md`, `aria-backstory-exploration.md`
- Prefix with status if helpful: `[draft]-merchant-guild.md`, `[maybe]-time-travel.md`

---

## Don't Organize Too Early

The notes folder is messy by design. It's a thinking tool, not a reference library. Let ideas accumulate, then organize when patterns emerge.
```
