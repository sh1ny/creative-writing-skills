---
name: cw-novel-init
description: Creative writing skill for initializing a new novel project. Use when the user wants to set up a new novel with a structured vault. Transforms the project directory into an Obsidian-compatible vault with Codex, Story, Style, Notes, and Meta folders. Use once at project start.
---

# Novel Project Initialization

Initialize a new novel project as an Obsidian-compatible vault with structured folders and starter files.

## When to Use This Skill

Use `/novel-init` when:
- User wants to start a new novel project
- User wants to organize existing notes into a structured vault
- User says "new novel", "start a project", "set up my writing vault"

**This skill should be used once at project start.** After initialization, use other skills for ongoing work.

## Project Vault Structure

The vault follows this structure:

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
│   │   └── logline.md
│   ├── Synopsis/
│   │   └── short-synopsis.md
│   ├── Outline/
│   │   └── act-structure.md
│   └── Chapters/
│       └── Act1/
│           └── Chapter01/
│               └── Scene01.md
├── Style/
│   └── master.md
├── Notes/
└── Meta/
    └── project.md
```

All files use Obsidian-compatible markdown with YAML frontmatter. Relationships use wiki links: `[[FileName]]`.

## Step-by-Step Process

### Step 1: Confirm Project Root

Ask the user where they want to create the vault:

```
Where would you like to create your novel vault? 

Option 1: Here (current directory) — I'll create a new folder for your novel
Option 2: Specify a path — Tell me the full path where you want it created

Note: The vault should be in its own folder, separate from other projects.
```

If current directory, ask for the novel title to name the folder. If path provided, use that.

### Step 2: Gather Project Information

Ask these questions one at a time or in logical groups:

**Question 1: Novel Title**
```
What is your novel called? (Working title is fine)
```

**Question 2: Genre**
```
What genre is your novel? (e.g., fantasy, sci-fi, literary fiction, thriller, romance, horror)
```

**Question 3: Premise**
```
In 2-3 sentences, what is your novel about? 

What's the main story? Who is it about, what do they want, and what stands in their way?
```

**Question 4: Structure Template**
```
Do you already have a structure template you want to use?

- If yes: Paste it or describe it, and I'll incorporate it
- If no: I can offer you a curated menu of proven story structures
```

**If user says "no" or "show me options":**

Present this menu:

```
I'd recommend one of these proven story structures:

1. **Save the Cat** (Blake Snyder) — 15 beats, popular for commercial fiction
2. **Story Grid** (Shawn Coyne) — 5 commandments per scene, systematic approach  
3. **Hero's Journey** (Campbell) — 12 stages, mythic structure
4. **Three-Act Structure** — Classic dramatic structure
5. **Four-Act Structure** — Expanded three-act with midpoint division
6. **Seven-Point Story Structure** (Dan Wells) — 7 key plot points
7. **Freytag's Pyramid** — 5-part dramatic structure

Which appeals to you, or would you like more detail on any?
```

After user selects, briefly explain the key beats/stages and confirm it matches their vision.

### Step 3: Create the Vault Scaffold

Create all folders and starter files. Work efficiently — create multiple files in parallel when possible.

#### Create Folder Structure

Create these directories:
```
Codex/Characters/
Codex/Locations/
Codex/Items/
Codex/Events/
Codex/Factions/
Codex/Concepts/
Story/Pitch/
Story/Synopsis/
Story/Outline/
Story/Chapters/Act1/Chapter01/
Style/
Notes/
Meta/
```

#### Create Meta/project.md

File: `Meta/project.md`

```yaml
---
title: "[Novel Title]"
genre: "[Genre]"
premise: "[2-3 sentence premise]"
structure-template: "[Template Name]"
status: drafting
created: [YYYY-MM-DD]
version: "1.0"
tags: [meta, project]
---

# [Novel Title]

## Quick Info

| Field | Value |
|-------|-------|
| Title | [Novel Title] |
| Genre | [Genre] |
| Structure | [Template Name] |
| Status | Drafting |
| Created | [Date] |

## Premise

[Premise text here]

## Current Phase

Initialization complete. Next steps:
- [[Story/Pitch/logline|Develop logline]]
- [[Codex/Characters/_README|Add characters]]
- [[Style/master|Create style guide]]

## Notes

[Empty for user notes]
```

#### Create Story/Pitch/logline.md

File: `Story/Pitch/logline.md`

```yaml
---
type: pitch
subtype: logline
status: draft
tags: [pitch, story]
---

# Logline

## One-Sentence Pitch

[WORKING - 25 words or less capturing: Who is the protagonist? What do they want? What opposes them?]

## Expanded Pitch (2-3 sentences)

[WHO is the story about?]
[WHAT do they want?]
[WHAT STANDS IN THEIR WAY?]
[WHAT CHOICE must they make?]

## Origin

[How did this story emerge? Personal experience? Dream? Image? Existing story you want to tell in new form?]

## Notes

[Open questions, possibilities to explore]
```

**After creating, fill in the logline from user's premise:**

Convert the user's premise into a working logline. Show them what you wrote and ask for feedback:

```
I've drafted a working logline from your premise:

"[Your draft logline]"

Does this capture the essence? Want to refine it?
```

#### Create Story/Synopsis/short-synopsis.md

File: `Story/Synopsis/short-synopsis.md`

```yaml
---
type: synopsis
subtype: short
status: placeholder
tags: [synopsis, story]
---

# Short Synopsis

## Summary (1-2 paragraphs)

[One to two paragraph summary of the complete story arc — setup, major events, resolution. This is a placeholder to fill in later as the story develops.]

## Core Conflict

[What is the central dramatic question?]

## Key Thematic Statement

[What is this story really about? What idea or experience are you exploring?]

## Notes

[Questions to answer, things to nail down, possibilities to explore]
```

#### Create Story/Outline/act-structure.md

File: `Story/Outline/act-structure.md`

```yaml
---
type: outline
subtype: act-structure
status: skeleton
tags: [outline, structure]
---

# [Template Name] Structure

## Overview

[Brief description of the chosen structure]

## Key Beats/Stages

[The skeleton outline based on chosen template — fill in during outline phase]

## Acts/Major Divisions

[How the story divides into major sections]

## Notes

[Questions, uncertainties, things to explore]
```

#### Create Codex/_README.md and Codex Subfolder READMEs

File: `Codex/_README.md`

```yaml
---
type: reference
status: placeholder
tags: [codex, index]
---

# Codex — Story World Reference

The Codex stores all factual information about your story world.

## Subfolders

- [[Codex/Characters]] — Character profiles, backstories, motivations
- [[Codex/Locations]] — Places, settings, geography
- [[Codex/Items]] — Objects, artifacts, weapons, significant items
- [[Codex/Events]] — Historical events, plot events, timelines
- [[Codex/Factions]] — Organizations, groups, governments, guilds
- [[Codex/Concepts]] — Magic systems, technologies, rules, lore

## How to Use

- Create new entries as you develop your story
- Link entries using `[[Entry Name]]` wiki links
- Update entries as your story evolves
- Use this for canonical facts (what is true in your world)

## Entry Naming

Use consistent naming: `Character First Last.md`, `Location Name.md`
```

File: `Codex/Characters/_README.md`

```yaml
---
type: reference
status: placeholder
tags: [codex, characters]
---

# Characters Codex

Store character profiles here.

## What Goes Here

- Full character profiles (use `/wiki` to create)
- Character relationship maps
- Character arc tracking

## Recommended Fields

- Name and basic info
- Role in story
- Motivation (what they want)
- Conflict (what stands in their way)
- Backstory
- Character traits
- Relationships with other characters

## Entry Format

```yaml
---
name: [Character Name]
role: [Protagonist | Antagonist | Supporting | Minor]
status: [alive | dead | unknown]
tags: [character]
---

# [Character Name]

## Quick Info

| Field | Value |
|-------|-------|
| Role | [Story role] |
| Status | [Alive/Dead/Unknown] |

## Motivation

[What do they want?]

## Conflict

[What prevents them from getting it?]

## Notes

[Additional details, arc progress]
```
```

File: `Codex/Locations/_README.md`

```yaml
---
type: reference
status: placeholder
tags: [codex, locations]
---

# Locations Codex

Store location profiles and setting details here.

## What Goes Here

- Geographic locations (cities, countries, continents)
- Buildings and structures
- Natural features
- Historical sites
- Any place that matters to your story

## Entry Format

```yaml
---
type: location
name: [Location Name]
status: [active | abandoned | destroyed | historical]
tags: [location]
---

# [Location Name]

## Quick Info

| Field | Value |
|-------|-------|
| Type | [City/Building/Natural/Other] |
| Status | [Current status] |

## Description

[Physical description of the location]

## Significance

[Why does this location matter to the story?]

## Notes

[History, connections, details to add]
```
```

File: `Codex/Items/_README.md`

```yaml
---
type: reference
status: placeholder
tags: [codex, items]
---

# Items Codex

Store significant objects, artifacts, weapons, and items here.

## What Goes Here

- Magical artifacts
- Important weapons
- Sentimental objects
- Keys and MacGuffins
- Historical relics
- Any item that affects the plot

## Entry Format

```yaml
---
type: item
name: [Item Name]
status: [active | lost | destroyed | stolen]
tags: [item]
---

# [Item Name]

## Description

[Physical description]

## Significance

[Why does this item matter?]

## History

[Brief history if relevant]

## Notes

[Plot relevance, connections]
```
```

File: `Codex/Events/_README.md`

```yaml
---
type: reference
status: placeholder
tags: [codex, events]
---

# Events Codex

Store historical events and plot events here.

## What Goes Here

- Historical events (backstory)
- Plot events (things that happen in the story)
- Timeline entries
- Wars, treaties, discoveries
- Personal milestones for characters

## Entry Format

```yaml
---
type: event
name: [Event Name]
date: [Timeline date if known]
status: [historical | current | future | unknown]
tags: [event]
---

# [Event Name]

## Date

[When did/will this happen?]

## Description

[What happened]

## Significance

[Why does this matter?]

## Notes

[Impact on story, connections]
```
```

File: `Codex/Factions/_README.md`

```yaml
---
type: reference
status: placeholder
tags: [codex, factions]
---

# Factions Codex

Store organizations, groups, governments, and other factions here.

## What Goes Here

- Governments and political entities
- Guilds and organizations
- Religions and cults
- Rebel groups
- Corporations
- Any group that acts as an entity in your story

## Entry Format

```yaml
---
type: faction
name: [Faction Name]
alignment: [Alignment or goals]
status: [active | disbanded | dissolved]
tags: [faction]
---

# [Faction Name]

## Quick Info

| Field | Value |
|-------|-------|
| Alignment | [Goals/ideals] |
| Status | [Current status] |

## Description

[What is this faction?]

## Leadership

[Who leads them?]

## Goals

[What do they want?]

## Conflicts

[Who opposes them? Why?]

## Notes

[Details, relationships, history]
```
```

File: `Codex/Concepts/_README.md`

```yaml
---
type: reference
status: placeholder
tags: [codex, concepts]
---

# Concepts Codex

Store abstract systems, magic rules, technologies, and lore here.

## What Goes Here

- Magic systems and rules
- Technologies
- Religions and belief systems
- Cultural customs
- Languages
- Economics
- Any abstract system that governs your world

## Entry Format

```yaml
---
type: concept
name: [Concept Name]
status: [established | developing | theoretical]
tags: [concept]
---

# [Concept Name]

## Overview

[What is this concept?]

## Rules

[How does it work?]

## Limitations

[What can't it do?]

## Significance

[Why does it matter to the story?]

## Notes

[Questions, possibilities, development needed]
```
```

#### Create Style/master.md

File: `Style/master.md`

```yaml
---
type: style-guide
subtype: master
status: placeholder
tags: [style, writing]
---

# Master Style Guide

This is your project's writing style reference. Run `/style` to create detailed style guides for prose, dialogue, characters, and more.

## Purpose

A style guide ensures consistent writing across your novel. It captures:
- Prose rhythm and sentence structure preferences
- Dialogue formatting conventions
- POV handling
- Tense usage
- Character voice patterns
- Genre-specific conventions

## How to Build

1. Run `/style` to create this master guide
2. Answer questions about your preferences
3. Add examples from your own writing
4. Update as you discover what works

## Placeholder Sections

Once you run `/style`, these sections will be populated:
- [ ] Prose Style — sentence rhythm, paragraph structure, description
- [ ] Dialogue Style — tags, beats, formatting
- [ ] POV — perspective handling, head-hopping rules
- [ ] Tense — past/present, consistency
- [ ] Character Voices — individual speech patterns
- [ ] Genre Conventions — format-specific rules

## Quick Notes

[Your initial thoughts on style preferences]
```

#### Create First Scene Placeholder

File: `Story/Chapters/Act1/Chapter01/Scene01.md`

```yaml
---
type: scene
chapter: "01"
act: "1"
status: placeholder
tags: [chapter, scene]
---

# Chapter 01 — Scene 01

## Placeholder

This is a placeholder scene file. The first actual scene will be written using the `/beat` command.

## Scene Notes

[Initial thoughts on opening scene]

## Checkpoints

- [ ] Opening image/hook established
- [ ] Character introduced
- [ ] Ordinary world shown (or inciting incident)
- [ ] Tone and voice established

## Word Count Target

[Target word count for this scene]
```

#### Create Notes Placeholder

File: `Notes/.gitkeep` or `Notes/README.md`

```yaml
---
type: notes
status: placeholder
tags: [notes]
---

# Writing Notes

General notes folder. Use for:
- Brainstorming not yet organized
- Research links
- Ideas to explore later
- Writing reminders

This folder is intentionally unstructured. Organize as you see fit.
```

### Step 4: Report Completion

After all files are created, summarize what was done:

```
## Novel Vault Initialized

Your novel vault is ready at: `[path/to/vault]`

### Created Structure

```
[VaultName]/
├── Codex/
│   ├── Characters/
│   ├── Locations/
│   ├── Items/
│   ├── Events/
│   ├── Factions/
│   ├── Concepts/
│   └── _README.md (with entry templates)
├── Story/
│   ├── Pitch/logline.md
│   ├── Synopsis/short-synopsis.md
│   ├── Outline/act-structure.md
│   └── Chapters/Act1/Chapter01/Scene01.md
├── Style/master.md
├── Notes/
└── Meta/project.md
```

### Next Steps (Suggested Workflow)

1. **Refine your pitch** → Run `/pitch` to develop your logline, elevator pitch, and premise
2. **Build your codex** → Run `/codex` to add characters, locations, factions, and concepts
3. **Develop your outline** → Run `/outline` to build your act structure, chapter outlines, and scene breakdowns
4. **Create your style guide** → Run `/style` with sample prose to define your writing voice
5. **Start writing** → Run `/beat` to write prose one beat at a time

### Skills are Composable

This vault is designed to work with all your creative writing skills:
- `/pitch` — Develop your logline, elevator pitch, and synopses
- `/codex` — Create and update world-building entries
- `/outline` — Build your story structure top-down
- `/style` — Build your prose style guide
- `/beat` — Write prose beat by beat
- `/bs` — Brainstorm ideas and solve plot problems
- `/critique` — Get feedback on written chapters

Good luck with your novel!
```

## Composability

This skill sets up the foundation for your novel project. It works with all other creative writing skills:

- **Before initialization**: Just have an idea
- **After initialization**: Use `/pitch` for story development, `/codex` for world-building, `/outline` for structure, `/style` for voice, `/beat` for prose, `/bs` for brainstorming, `/critique` for feedback

The vault structure makes everything interlinked — wiki links connect your logline to characters to scenes to outlines.

## File Placement

Files are always created at the project root (wherever the user wants their vault). Ask if unclear.

## Edge Cases

**User has an existing project:**
```
I see you have existing files here. Would you like to:
1. Create the vault alongside these files (in a new subfolder)
2. Convert this into a vault (I'll reorganize)
3. Choose a different location
```

**User has partial structure:**
```
It looks like you already have some structure. I can:
1. Fill in missing folders/files only
2. Start fresh with the full vault
3. Adapt the vault to match what you have
```

**User doesn't know genre or template:**
That's fine. Use "Unknown" or "Undetermined" in project.md. They can always update it later.
