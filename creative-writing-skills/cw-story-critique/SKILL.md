---
name: cw-story-critique
description: Multi-level story critique skill for novel writing. Use when the user requests feedback on beats, scenes, chapters, acts, or full outlines. Provides constructive, calibrated feedback with composability suggestions.
---

# Story Critique

Analyze story content at multiple levels and provide constructive feedback calibrated to the user's needs. This skill is designed for a novel-writing workflow and integrates with other skills in the plugin.

## Core Philosophy

**Don't force rigid templates.** Each story—and each portion of a story—needs different things. Focus on what actually matters to this story at this stage. Trust your analysis of what affects the narrative, even if it's not in any reference guide.

**Ask context first.** The right critique depends entirely on what the user needs right now.

## Critique Scopes

This skill operates at multiple levels. **Always confirm the scope before critiquing:**

| Scope | What It Means | Focus Areas |
|-------|----------------|-------------|
| `beat` | Single moment, one paragraph to one page | Dramatization, sensory grounding, POV consistency, emotional truth |
| `scene` | Single scene, one to several pages | Goal/conflict/outcome, emotional shift, pacing within scene |
| `chapter` | Full chapter | Scene sequence, chapter-level arc, pacing, chapter hook |
| `act` | Multiple chapters | Structural integrity, turning points, act-level arc |
| `outline` | Full outline (before prose) | Scene-level structure, chapter progression, act turning points |
| `full` | Entire written manuscript | Everything, prioritized by what matters most |

## Process

### 1. Confirm Context

Always ask (or infer from available information):

```
Before I critique this, help me understand:

1. Scope: Is this a beat, scene, chapter, act, or full manuscript?
2. Target audience? (YA, adult, genre)
3. What feedback are you looking for? (big picture, line-level, specific concerns)
4. Draft stage? (early = structural issues, later = prose/details OK)
```

If the user doesn't provide context, **ask targeted follow-ups**. If you can't ask, infer from content and note your assumptions.

### 2. Determine Critique Mode

**Balanced** (default): Strengths + areas for improvement + prioritized recommendations

**Harsh** (if requested): Focus on problems, minimize or skip strengths section

**Flexible**: Whatever structure serves this content best

### 3. Read Relevant Context Files

**For prose critique (scene/chapter/act/full):**
- Read `Meta/project.md` for project settings
- Read `Story/Pitch/*.md` for story premise
- Read existing chapter context if available
- Optionally read `Codex/Characters/*.md` for character consistency checks

**For outline critique:**
- Read `Meta/project.md` to identify the structure template (Save the Cat, Three-Act, Hero's Journey, etc.)
- Read `Story/Outline/act-structure.md` for act breakdown
- Read chapter outline files being critiqued
- Read `Story/Pitch/*.md` for story premise and core conflict

**For beat-level critique:**
- Read the surrounding scene/chapter for context
- Focus on the beat in isolation, then zoom out to confirm it fits

### 4. Perform the Critique

Use `references/critique-areas.md` as a reference guide—not a checklist. Examine what matters for this specific content.

**For each scope, apply the appropriate focus:**

#### Beat-Level Critique
- Is the moment dramatized (showing) or summarized (telling)?
- Are there sensory details that ground the reader?
- Is POV consistent and close enough?
- Does the emotional truth ring true?
- Does it advance the scene's goal, or is it filler?

#### Scene-Level Critique
- Does the scene have a clear **goal** for the POV character?
- Is there genuine **conflict** that opposes that goal?
- Is there a clear **outcome** (success, failure, or partial)?
- Does the scene have an **emotional shift** (not flat throughout)?
- Does the scene move the story forward?

#### Chapter-Level Critique
- Does each scene serve the chapter's purpose?
- Is there a chapter-level arc (something changes by the end)?
- Does the chapter hook work (end on tension, question, or shift)?
- Is pacing appropriate (not too fast/slow for the content)?
- Does the chapter sequence build momentum?

#### Act-Level Critique
- Do major turning points land where the structure template specifies?
- Does each chapter contribute to the act's overall arc?
- Are there dead chapters (neither advance plot nor develop character)?
- Does the act have a clear emotional progression?
- Are setup and payoff balanced?

#### Outline Critique Mode

When the user passes an outline (not prose), focus critique on:

**Scene-Level (within outlines):**
- Goal/conflict/outcome present for each scene?
- Emotional shift clear?
- Beats are 1 sentence, action-focused?

**Chapter-Level:**
- Does each chapter move the story forward?
- Any dead chapters that could be cut?
- Scene sequence logical and building?

**Act-Level:**
- Do turning points match the structure template?
- Act purposes clear and fulfilled?
- Setup in Act 1 pays off in Act 3?

### 5. Codex Consistency Check (Optional)

When critiquing prose, you can optionally check character behavior against Codex entries:

```
To check consistency, I would need:
- Run `/codex` to list existing character entries
- Compare behavior in the critiqued passage against established character traits
```

If the user asks you to check consistency, read the relevant `Codex/Characters/*.md` entries and note any discrepancies—but only if the user explicitly requests this.

### 6. Deliver Critique

Structure your critique based on mode:

**Balanced Mode:**
```
## What Works
[Strengths that should be preserved]

## Areas for Improvement
[Issues, prioritized by impact]

## Specific Recommendations
[Concrete suggestions for fixing issues]

## Composability Suggestions
[How other skills can help address issues]
```

**Harsh Mode:**
Focus on problems and concrete fixes. Minimize or skip strengths.

**Flexible Mode:**
Adapt structure to what this content needs. Some critiques need extensive character analysis; others need pacing work; others are strong but need line editing.

## Composability

After critique, suggest how other skills can help:

| Issue Identified | Suggest |
|------------------|---------|
| Scene conflict is weak | "Use `/bs` to brainstorm alternatives" |
| Character motivation unclear | "Check their `/codex` entry, or create one if it doesn't exist" |
| Act structure seems off | "Compare against your `/outline` structure template" |
| Need to develop character backstory | "Use `/codex` to create or expand their entry" |
| Want to explore alternative directions | "Use `/bs` to explore possibilities before revising" |
| Need to write new prose for a beat | "Use `/beat` to draft the revision" |
| Outline needs work before prose | "Use `/outline` to restructure" |

## Saving Critiques

When the user asks you to save critique to `Notes/`:

1. Create the file with proper frontmatter:

```yaml
---
type: critique
scope: scene            # beat | scene | chapter | act | outline | full
target: ""              # [[Story/Chapters/Act1/Chapter01/Scene01]]
date: YYYY-MM-DD
tags: [critique, notes]
---
```

2. Write the critique content below the frontmatter

3. Save to `Notes/Critiques/` with an appropriate filename (e.g., `scene-01-critique-2026-04-01.md`)

## File Locations

This skill reads from and saves to:

```
Story/
├── Chapters/           # Written chapters (prose)
├── Outline/            # Act and chapter outlines
└── Pitch/             # Story premise and core conflict

Meta/
└── project.md          # Structure template and project settings

Codex/
└── Characters/         # Character profile entries

Notes/
└── Critiques/          # Saved critique documents
```

## Skills Are Composable

This skill works with the full novel-writing workflow:

| Skill | When to Use |
|-------|-------------|
| `/pitch` | Establish story premise before outlining or writing |
| `/outline` | Build or revise structure before/during writing |
| `/codex` | Create or check character/location entries |
| `/beat` | Write or revise specific prose beats |
| `/bs` | Brainstorm alternatives when critique reveals problems |
| `/critique` | (This skill) Analyze and provide feedback |

**Typical workflow:** Write → Critique → Brainstorm fixes → Revise → Critique again

## Quality Principles

Regardless of scope or mode, good critique:

1. **Names specific problems** — not just "pacing issues" but "the chapter slows in the middle because two scenes backload reflection without conflict"
2. **Explains why it matters** — not just "unclear motivation" but "without clear motivation, the reader can't root for or understand her decision"
3. **Offers paths forward** — critique without suggestion is just complaint
4. **Respects the author's vision** — flag when your preference differs from a valid stylistic choice
5. **Calibrates to stage** — early draft = structural; later draft = line-level
