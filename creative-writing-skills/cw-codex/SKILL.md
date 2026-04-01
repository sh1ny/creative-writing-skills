---
name: cw-codex
description: Create and update world-building entries in your novel's Obsidian Codex vault. Supports Characters, Locations, Items, Events, Factions, and Concepts. Composables with /bs for brainstorming entries before creation and /outline for seeing where entries appear in your story structure.
---

# Codex Entry Creator

Creates and updates entries in your Obsidian-compatible Codex vault under `Codex/`. All entries use YAML frontmatter with markdown bodies, wiki links (`[[EntryName]]`) for connections, and Obsidian callouts for author-only content.

## Workflow

### Step 1: Determine Entry Type

Ask the user what type of entry they want to create or update:

> "What type of Codex entry would you like to create or update? **Character**, **Location**, **Item**, **Event**, **Faction**, or **Concept**?"

If the user is unsure, briefly describe each type:
- **Character** — People, creatures, or entities in your story
- **Location** — Places, buildings, regions, or worlds
- **Item** — Objects, artifacts, documents, or weapons
- **Event** — Historical occurrences, scene events, or turning points
- **Faction** — Organizations, governments, guilds, or families
- **Concept** — Magic systems, themes, lore rules, or technologies

### Step 2: Gather Entry Information

Ask for the **name** first, then ask type-specific questions (see below). Keep the conversation natural—don't dump all questions at once. Ask 2-4 questions per exchange, then let the user respond before continuing.

**File naming**: Use the entry name in kebab-case, e.g., `aria-voss.md`, `the-wandering-woods.md`, `solaris-dagger.md`.

### Step 3: Check for Related Existing Entries

Before creating the file, scan `Codex/` to find existing entries that could be linked. Mention these to the user and ask if they want to add those connections.

### Step 4: Create or Update the Entry

Write the file with correct frontmatter and markdown body following the schemas in `references/entry-schemas.md`.

**File location**:
- `Codex/Characters/[name-kebab].md`
- `Codex/Locations/[name-kebab].md`
- `Codex/Items/[name-kebab].md`
- `Codex/Events/[name-kebab].md`
- `Codex/Factions/[name-kebab].md`
- `Codex/Concepts/[name-kebab].md`

### Step 5: Suggest Next Steps

After creating an entry, suggest related actions:
- "You may want to create a Faction entry for the guild Marcus belongs to."
- "Run `/outline` to see which chapters feature this character."
- "Use `/bs` to brainstorm how this location fits into Act 2."
- "Consider creating an Item entry for the artifact users are seeking."

## Entry Type Questions

### Character

1. "What is this character's role in your story? Protagonist, antagonist, supporting, or minor?"
2. "Are they alive, dead, or is their status unknown?"
3. "What gender do they identify as?" (optional)
4. "How old are they?" (optional)
5. "Do they belong to any factions?" (collect as `faction` array)
6. "Where is their home location?"
7. "Give me 2-3 sentences describing their physical appearance."
8. "What are their key personality traits?"
9. "What is their backstory in a few sentences?"
10. "What do they want most—what are their motivations?"
11. "Do they have any important relationships with other characters?"
12. "What is their arc? How do they change by story's end?"
13. "Any hidden secrets only the author should know?" (use `> [!hidden]` callout)

**Infer** `appears-in` from context but leave empty for user to fill as they write.

### Location

1. "What type of place is this? City, building, region, world, room, or other?"
2. "Is it active, in ruins, destroyed, or is its status unknown?"
3. "Who or what lives here?" (collect inhabitants)
4. "Is this within a larger location?" (parent-location)
5. "Give me 2-3 sentences describing what it looks like physically."
6. "What is the atmosphere or mood of this place?"
7. "What is its history—how did it come to be?"
8. "What notable features or landmarks does it have?"
9. "What other Codex entries connect to this location?"

### Item

1. "What type of item is this? Weapon, artifact, document, clothing, or other?"
2. "How rare is it? Common, uncommon, rare, or unique?"
3. "Who currently possesses it?" (owner)
4. "Where is it located?"
5. "Give me 2-3 sentences describing what it looks like."
6. "What is its history or origin?"
7. "Why is it significant to the story?"
8. "What is its current status—where does the story find it?"

### Event

1. "What type of event is this? Historical, scene, turning-point, or offscreen?"
2. "When does it occur in your story's timeline? (e.g., 'Day 3', 'Year 412', 'Before the story starts')"
3. "Who participates in this event?" (characters involved)
4. "Where does it take place?"
5. "Give me a summary of what happens."
6. "What events or circumstances led to this?" (causes)
7. "What are the consequences—what happens afterward?" (consequences)
8. "What impact does this have on the story?"
9. "Any hidden details only the author should know?" (use `> [!hidden]` callout)

### Faction

1. "What type of faction is this? Guild, government, religion, family, or other?"
2. "Is it active, disbanded, secret, or something else?"
3. "Who leads this faction?"
4. "Who are the members?" (can include known members vs. general membership)
5. "Where is their headquarters or base of operations?"
6. "Give me 2-3 sentences describing what this faction is and does."
7. "What is their history?"
8. "What are their goals—what do they want to achieve?"
9. "How is the faction structured or organized?"
10. "What rituals, culture, or traditions do they have?"
11. "Do they have allies or enemies among other factions?"

### Concept

1. "What type of concept is this? Magic system, theme, lore rule, technology, religion, or other?"
2. "Give me 2-3 sentences explaining what this concept is."
3. "What are the rules or mechanics—how does it work?"
4. "What are its limitations or costs?"
5. "How do people in your world perceive this concept?"
6. "Any additional notes for your own reference?"

## Frontmatter Fields

All entries share these common fields:
- `type` — The entry type (character, location, item, event, faction, concept)
- `name` — The entry name
- `aliases` — Alternative names (array, can be empty)
- `appears-in` — Story locations where this entry appears (array, leave empty to fill later)
- `related` — Other related Codex entries (array)
- `tags` — Array including the entry type tag (e.g., `[character]`)

The `appears-in` field should be populated with wiki-links to specific scenes like `[[Act1/Chapter3/Scene2]]`. Infer potential values from context but leave the field empty or with a placeholder for the user to fill as they write.

## Obsidian Compatibility

- **Wiki links**: Use `[[EntryName]]` for all internal links
- **Frontmatter**: YAML block at the top of each file
- **Tags**: Include type tag (e.g., `#character`) in frontmatter `tags` array
- **Hidden content**: Use `> [!hidden]` callout blocks for author-only secrets
- **Aliases**: Obsidian's built-in aliases field works with the `aliases` frontmatter key

## Composability

- **Before creating**: Use `/bs` (brainstorming skill) to explore ideas before committing to a Codex entry
- **After creating**: Use `/outline` to see where a character or location appears in your story structure
- **Critique loop**: Create a character → use `/critique` on a chapter featuring them → update the entry based on feedback
- **Documentation**: After finalizing elements through brainstorming, use `/wiki` to create polished documentation

## Example Entry Creation

**User**: "I want to add a character named Aria Voss."

**You**: "Great! Aria Voss—what type of role does she play? Protagonist, antagonist, supporting, or minor?"

**User**: "She's the protagonist."

**You**: "Is she alive, dead, or unknown?"

**User**: "Alive, obviously."

...and so on, progressing through the questions naturally.

---

After creating the entry, check `Codex/` for related entries and suggest connections the user might want to make.
