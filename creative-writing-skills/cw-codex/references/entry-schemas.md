# Codex Entry Schemas

Reference documentation for all Codex entry types. Each entry uses YAML frontmatter followed by a markdown body.

## Common Fields

All entry types share these frontmatter fields:

| Field | Type | Description |
|-------|------|-------------|
| `type` | string | Entry type: `character`, `location`, `item`, `event`, `faction`, `concept` |
| `name` | string | The canonical name of the entry |
| `aliases` | array | Alternative names or nicknames |
| `appears-in` | array | Wiki-links to story locations (e.g., `[[Act1/Chapter3/Scene2]]`). Leave empty to populate as you write. |
| `related` | array | Wiki-links to related Codex entries |
| `tags` | array | Obsidian tags; must include the type tag (e.g., `[character]`) |

---

## Character

```yaml
---
type: character
name: ""
aliases: []
role: protagonist       # protagonist | antagonist | supporting | minor
status: alive           # alive | dead | unknown | other
age: null
gender: ""
faction: []             # [[FactionName]]
home-location: null     # [[LocationName]]
appears-in: []          # [[Act1/Chapter1/Scene1]]
related: []             # [[OtherEntry]]
tags: [character]
---
```

### Body Sections

**Overview**
Brief introduction to who this character is.

**Physical Description**
2-3 sentences on their appearance. Be specific enough for visual consistency.

**Personality**
Key traits, quirks, demeanor.

**Backstory**
How they came to be—relevant history that shapes who they are now.

**Motivations**
What they want and why they want it.

**Arc Notes**
How they change across the story. Leave blank if not yet determined.

**Relationships**
Connections to other characters, with brief notes on the nature of each relationship.

**Hidden**
Author-only secrets, twists, or information characters don't know. Use `> [!hidden]` callout:

```markdown
> [!hidden]
> This character is actually the lost heir to the throne.
```

---

## Location

```yaml
---
type: location
name: ""
aliases: []
parent-location: null   # [[ParentLocation]] e.g. city within a country
location-type: ""       # city | building | region | world | room | other
status: active          # active | ruins | destroyed | unknown
inhabitants: []         # [[CharacterName]] or faction names
appears-in: []
related: []
tags: [location]
---
```

### Body Sections

**Overview**
What this place is and its significance.

**Physical Description**
What it looks like—architecture, geography, key features.

**Atmosphere**
The mood or feeling of the place. Sensory details.

**History**
How it came to be or notable past events.

**Notable Features**
Landmarks, points of interest, special properties.

**Connections**
Links to other locations, factions, or characters associated with this place.

---

## Item

```yaml
---
type: item
name: ""
aliases: []
item-type: ""           # weapon | artifact | document | clothing | other
rarity: ""              # common | uncommon | rare | unique
owner: null             # [[CharacterName]]
location: null          # [[LocationName]]
appears-in: []
related: []
tags: [item]
---
```

### Body Sections

**Overview**
What this item is and its general description.

**Physical Description**
Appearance, materials, craftsmanship, distinctive features.

**History/Origin**
Where it came from, who made it, how it entered the story.

**Significance**
Why it matters to the plot, characters, or world.

**Current Status**
Where it is and what state it's in at the story's present.

---

## Event

```yaml
---
type: event
name: ""
event-type: ""          # historical | scene | turning-point | offscreen
date-in-story: ""       # e.g. "Day 3", "Year 412", "Before the story"
participants: []         # [[CharacterName]]
location: null           # [[LocationName]]
causes: []               # [[EventName]]
consequences: []         # [[EventName]]
appears-in: []
related: []
tags: [event]
---
```

### Body Sections

**Summary**
What happened. 2-4 sentences.

**Context**
The circumstances and why it matters.

**Impact**
Effects on characters, plot, or world.

**Hidden**
Author-only details about the event. Use `> [!hidden]` callout:

```markdown
> [!hidden]
> The true cause of the battle was manipulated by the advisor.
```

---

## Faction

```yaml
---
type: faction
name: ""
aliases: []
faction-type: ""        # guild | government | religion | family | other
status: active          # active | disbanded | secret | other
leader: null            # [[CharacterName]]
members: []             # [[CharacterName]]
headquarters: null      # [[LocationName]]
allies: []               # [[FactionName]]
enemies: []              # [[FactionName]]
appears-in: []
related: []
tags: [faction]
---
```

### Body Sections

**Overview**
What this faction is and what it does.

**History**
Origins and major developments.

**Goals**
What the faction wants to achieve.

**Structure**
How it's organized—ranks, roles, hierarchy.

**Rituals/Culture**
Traditions, customs, meeting places, internal culture.

**Known Members**
Named characters who belong to or interact with this faction.

---

## Concept

```yaml
---
type: concept
name: ""
concept-type: ""        # magic-system | theme | lore-rule | technology | religion | other
appears-in: []
related: []
tags: [concept]
---
```

### Body Sections

**Overview**
What this concept is.

**Rules/Mechanics**
How it works—if it's a magic system, the mechanics; if it's a theme, how it manifests.

**Limitations**
Costs, restrictions, drawbacks.

**In-World Perception**
How characters and people view this concept.

**Notes**
Additional observations, unanswered questions, areas for development.

---

## Wiki Link Format

Use Obsidian wiki links for all internal references:

```markdown
[[Aria Voss]]           # Links to a character
[[Thornwall Prison]]    # Links to a location
[[Solaris Dagger]]      # Links to an item
[[The Betrayal]]        # Links to an event
[[Iron Guild]]          # Links to a faction
[[Soul Bonding]]        # Links to a concept
```

For links with display text:

```markdown
[[Aria Voss|daughter of Marcus]]
```

---

## Obsidian Callouts

Use callout blocks for special content:

```markdown
> [!hidden]
> Author-only content goes here. This callout is collapsed by default in Obsidian.
```

Other useful callout types:

```markdown
> [!note]
> Additional context

> [!warning]
> Important consideration

> [!example]
> In-world example of this concept
```
