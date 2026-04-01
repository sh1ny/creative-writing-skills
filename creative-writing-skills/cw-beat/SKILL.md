---
name: cw-beat
description: Write individual beats of novel prose from beat descriptions in scene outlines. Loads minimal context (beat description, scene outline, chapter summary, relevant Codex entries, style guide, last 500 words of previous scene). Composables with /outline for beat descriptions, /critique for reviewing completed scenes, and /bs to rethink scene direction.
---

# Beat Writer

Writes individual beats of novel prose, appending them to scene files and marking beats as complete in the scene outline.

## Workflow

### Step 1: Determine Which Scene and Beat to Write

Ask the user which scene they want to work on, or parse the argument if provided:

> `/beat Act1/Chapter01/Scene01 beat 3`

If no argument provided, ask:
> "Which scene would you like to work on? (e.g., Act1/Chapter01/Scene01)"

Then determine which beat to write:
- If beat number provided, use that
- Otherwise, scan the scene outline for the next unmarked beat (no ✓ or `status: written`)

### Step 2: Load the Minimal Context Bundle

Read and load ONLY the following files in this order:

1. **Scene outline** — `Story/Outline/[act]/[chapter].md`
   - Shows all beats listed with scene metadata (location, characters, POV, goal, conflict, outcome, emotional shift)
   - Each beat is a 1-sentence description like "Aria spots Marcus in the corner, approaches carefully."

2. **Scene file** — `Story/Chapters/[act]/[chapter]/[scene].md`
   - If it exists, show current state (existing prose and word count)
   - This tells you where to append

3. **Chapter outline** — `Story/Outline/[act]/[chapter].md`
   - Read the scene list and their 2-3 sentence summaries only — do NOT load beat lists or scene notes beyond what's needed for context
   - This gives chapter-level orientation without loading unnecessary detail

4. **Codex entries** for characters present in the scene
   - Load from `Codex/Characters/[character-name-kebab].md`
   - Load from `Codex/Locations/[location-name-kebab].md` for the scene location

5. **Style guide** — `Style/master.md`
   - Contains prose writing directives

6. **Last ~500 words of the previous scene's prose** (if it exists)
   - From `Story/Chapters/[act]/[chapter]/[previous-scene].md`
   - For continuity of voice, not plot recap

**DO NOT load**: full chapter prose, other acts, full Codex, all outline files.

### Step 3: Suggest Additional Codex Entries

Before writing, read the beat description carefully. Flag any proper nouns (character names, location names, items, factions) mentioned in the beat that are NOT already listed in the scene outline's `characters` or `location` fields.

Ask the user if they want to load or create these entries:
> "This beat mentions '[Name]' but I don't see them in the scene's character list. Want me to load their Codex entry, or create one?"

### Step 4: Write the Beat

Write the beat as prose following these guidelines:

- **One moment per beat** — A single action, reaction, dialogue exchange, or emotional shift
- **No time jumps within a beat** — The beat takes place in continuous real-time
- **Sensory grounding** — Anchor the moment in concrete detail
- **POV interiority** — Stay in the POV character's perspective and感受
- **Flow into next beat** — End with a hook or transition that leads naturally to the following beat's description
- **Follow style guide** — Apply all directives from `Style/master.md`
- **No beat headers in prose** — Beats are structural planning units; the prose reads as continuous narrative

Write the prose and append it to the scene file (after existing prose, with a blank line between paragraphs).

Update the scene file's `word-count` in frontmatter.

### Step 5: Mark Beat as Written

In the scene outline file, mark the beat as written by adding ✓ or updating `status: written`:

```
- [x] "Aria spots Marcus in the corner, approaches carefully."
```
or
```
- "Aria spots Marcus in the corner, approaches carefully." ✓
```

Update the outline beat's status to `status: written`.

### Step 6: Offer Next Actions

After completing a beat, ask:
> "Beat written. What would you like to do next?
> - **Write next beat** — Continue to the following beat
> - **Regenerate this beat** — Rewrite this beat fresh
> - **Done for now** — Stop and resume later"

---

## Regeneration

User can ask to regenerate any single beat by specifying the beat number or referring to the current beat.

**Process:**
1. Remove the previous beat's prose from the scene file
2. Subtract the beat's word count from the scene's `word-count`
3. Rewrite the beat fresh using the same context bundle
4. Append the new prose to the scene file
5. Update `word-count` again

**Does NOT regenerate**: other beats, the whole scene, or adjacent scenes.

---

## Scene File Format

Scene files use this frontmatter:

```yaml
---
type: scene
act: 1
chapter: 1
scene: 1
title: ""
pov: ""                  # [[CharacterName]]
location: ""             # [[LocationName]]
characters: []           # [[CharacterName]], [[CharacterName]]
status: in-progress      # not-started | in-progress | complete
word-count: 0
tags: [scene, prose]
---
```

Prose follows the frontmatter as flowing paragraphs with no beat headers.

---

## Composability

- **/outline** — Create or modify beat descriptions before writing
- **/critique** — Review completed scenes for pacing, voice, or structural issues
- **/bs** — Rethink a scene direction or explore alternative approaches
- **/codex** — Create or update character/location entries referenced in beats

## Example Session

**User**: `/beat Act1/Chapter01/Scene01`

**You**: "Working on Act1/Chapter01/Scene01. Let me load the context... I see this scene has 4 beats, and beat 3 ('Aria spots Marcus in the corner, approaches carefully') is next. This beat mentions '[Orin]' who isn't in the scene's character list—want me to check if there's a Codex entry for them?"

**User**: "Yes, load Orin."

**You**: *Loads Codex/Characters/orin.md*, then writes beat 3 prose and appends it to the scene file, marks it complete in the outline.

**You**: "Beat 3 done (247 words). Next is beat 4: 'Marcus recognizes Orin and tensions spike.' Ready to write it, or would you like to regenerate beat 3?"
