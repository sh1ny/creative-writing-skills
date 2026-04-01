---
name: cw-pitch
description: Develops loglines, elevator pitches, story premises, and synopses for your novel. Use when you need to crystallize your story concept, create a compelling pitch for agents/editors, or generate a summary document. Composable with /bs for idea exploration and /outline when your pitch is solid. Can be entered cold — if no project context exists, ask for a rough premise and extract the pitch from it.
---

# cw-pitch: Story Pitch Development Skill

This skill helps you develop and refine the core pitch documents for your novel—from a single logline to a full synopsis. It works collaboratively, generating drafts and iterating based on your feedback until you have polished, professional-quality pitch materials.

**Composes well with:**
- `/bs` — Explore and develop story ideas before pitching
- `/outline` — Create detailed scene outlines once your pitch feels solid

---

## Project Context

Before generating any content, this skill reads your existing project files to understand what's already established:

### Files to Read

1. **`Meta/project.md`** — Your project foundation containing:
   - Title and genre
   - Premise summary
   - Structure template chosen during initialization

2. **`Story/Pitch/`** — Existing pitch documents (if any):
   - `logline.md` — One-sentence story summary
   - `elevator-pitch.md` — 2-3 paragraph pitch
   - `story-premise.md` — Full premise document

3. **`Story/Synopsis/`** — Existing synopsis documents (if any):
   - `short-synopsis.md` — 1-page summary
   - `long-synopsis.md` — Detailed beat-by-beat summary

All files use YAML frontmatter. The skill respects any existing content and builds upon it rather than replacing it without cause.

---

## What You Can Work On

### 1. Logline

A single sentence (25-35 words) that captures the essence of your story.

**Formula:**
```
When [inciting incident], [protagonist] must [goal] before [stakes/deadline], but [obstacle stands in the way].
```

Or:
```
[Protagonist] is a [description] who [wants/needs something], but [obstacle], so [conflict].
```

**Requirements:**
- Specific protagonist (name or vivid descriptor)
- Active voice
- Clear external goal
- Visible stakes
- Ironic tension or compelling conflict
- No vague phrases ("must find himself," "discovers the true meaning of")

### 2. Elevator Pitch

2-3 paragraphs that sell your story to an agent, editor, or reader.

**Structure:**
1. **Hook** — One punchy line that grabs attention
2. **Genre + Tone** — What kind of story is this?
3. **Protagonist** — Who is your main character and what do they want/need?
4. **Central Conflict** — What opposition do they face?
5. **Stakes** — What happens if they fail?
6. **Comparable Titles** (optional) — "For fans of X meets Y"

### 3. Story Premise

A full document that establishes your story's foundation.

**Includes:**
- **Premise** — 1-2 paragraph story summary
- **Themes** — Central ideas and what the story explores
- **Tone** — Emotional register and stylistic approach
- **Target Audience** — Who this story is for
- **Comparable Titles** — Similar published works

### 4. Short Synopsis

A 1-page summary of your complete story arc.

**Covers:**
- Opening setup (protagonist, status quo)
- Inciting incident
- Major turning points (3-act structure)
- Climax
- Resolution
- Only essential characters and plot threads

### 5. Long Synopsis

A detailed 5-10 page beat-by-beat summary of your entire story.

**Includes:**
- All major plot events in sequence
- Key character arcs (transformation/development)
- All subplots and how they resolve
- The complete ending (no cliffhangers)
- Scene-level specificity for pivotal moments

---

## Process

### Step 1: Assess the Project

Read the following files (if they exist):
1. `Meta/project.md` — Project foundation
2. `Story/Pitch/*` — Any existing pitch documents
3. `Story/Synopsis/*` — Any existing synopsis documents

Note the status of any existing documents. If content is already marked "final," treat it as constraint rather than starting point.

**If no project context exists (cold entry):**

The user may be entering the workflow here without having run `/novel-init` first. That's fine. Don't demand structured input — ask them to describe their story in their own words, even rough. "Just tell me what the story is about."

Extract from their response: protagonist, central conflict, genre, tone. Generate a rough logline first — this forces clarity on both sides. Iterate on that before expanding to anything longer. See `references/pitch-craft.md` for guidance on extracting a pitch from a raw concept.

### Step 2: Ask What to Work On

Present the five options and ask the user which they'd like to develop or revise:

1. Logline
2. Elevator pitch
3. Story premise
4. Short synopsis
5. Long synopsis

If the user is unsure, suggest starting with the logline as it forces clarity about core story elements.

### Step 3: Generate Initial Draft

Based on the selected document type and existing project context, generate a draft following the appropriate formula or structure outlined above.

**Principles:**
- Ground everything in established project details
- Use specific, vivid language — see `references/pitch-craft.md` for logline diagnostics, elevator pitch anatomy, and the want/need split
- Ensure stakes are clear, personal, and specific (not "save the world" — what specifically is lost?)
- Check for irony: is the protagonist uniquely wrong-footed for this situation?
- Maintain consistent tone with the project's genre

### Step 4: Collaborative Iteration

Present the draft and ask for feedback:

- What works well?
- What needs adjustment?
- Any character, plot, or thematic elements missing?
- Does the tone match your vision?

After receiving feedback, revise and present again. Repeat until the user confirms the document meets their needs.

### Step 5: Save the Document

When the user approves, save to the appropriate file with correct frontmatter:

**For Logline (`Story/Pitch/logline.md`):**
```yaml
---
type: pitch
subtype: logline
status: draft           # draft | revised | final
version: 1
tags: [pitch, story]
---
```

**For Elevator Pitch (`Story/Pitch/elevator-pitch.md`):**
```yaml
---
type: pitch
subtype: elevator-pitch
status: draft
version: 1
tags: [pitch, story]
---
```

**For Story Premise (`Story/Pitch/story-premise.md`):**
```yaml
---
type: pitch
subtype: premise
status: draft
version: 1
comparable-titles: []
themes: []
tone: ""
target-audience: ""
tags: [pitch, story]
---
```

**For Short Synopsis (`Story/Synopsis/short-synopsis.md`):**
```yaml
---
type: synopsis
subtype: short
status: draft
version: 1
tags: [synopsis, story]
---
```

**For Long Synopsis (`Story/Synopsis/long-synopsis.md`):**
```yaml
---
type: synopsis
subtype: long
status: draft
version: 1
tags: [synopsis, story]
---
```

Set `status: final` only when the user explicitly approves the document as complete.

---

## Craft Guidance

### Logline Pitfalls to Avoid

- **Passive protagonist** — "A woman who must..." is weak; "Mara, a surgeon, must..." is active
- **Vague stakes** — "save the world" is overused; "save her brother's chance at a normal life" is specific
- **No conflict** — The obstacle or opposition must be visible in the logline
- **Filler phrases** — Avoid "must learn," "discovers," "finds out" when possible
- **Multiple conflicts** — Stick to one central conflict per logline

### Synopsis Best Practices

- **Point of view** — Write in third person (present or past tense, your choice, stay consistent)
- **No chapter breaks** — Flow as continuous prose
- **Reveal the ending** — Synopses spoil the ending; that's expected
- **Character names** — Use full names on first reference, then first names
- **Subplot inclusion** — Short synopsis: omit or barely mention. Long synopsis: include all meaningful threads.

### Tension Maintenance

Every pitch document should maintain dramatic tension:
- What does the protagonist want desperately?
- What prevents them from getting it?
- What will happen if they fail?
- Why should we care?

If you can't answer all four questions clearly, the pitch needs more focus.

---

## Composability Notes

This skill is designed to work with other skills in the novel-writing plugin:

| Skill | How It Composes |
|-------|-----------------|
| `/bs` | Use before pitching to explore story ideas and develop your concept |
| `/outline` | Use after pitching to structure scenes and beats once your story concept is solid |
| `/beat` | Use after outlining to write prose for individual beats |
| `/critique` | Use on any written material to get feedback before revising pitch docs |

The typical workflow: **Brainstorm → Pitch → Outline → Write → Critique → Revise**

---

## File Locations

| Document | Path |
|----------|------|
| Logline | `Story/Pitch/logline.md` |
| Elevator Pitch | `Story/Pitch/elevator-pitch.md` |
| Story Premise | `Story/Pitch/story-premise.md` |
| Short Synopsis | `Story/Synopsis/short-synopsis.md` |
| Long Synopsis | `Story/Synopsis/long-synopsis.md` |
| Project Meta | `Meta/project.md` |

---

## Status Tracking

Documents move through these states:

1. **draft** — Initial generation, may need significant revision
2. **revised** — Feedback incorporated, closer to final
3. **final** — Approved by author, ready for submission or reference

Use the version field to track iterations. Increment (version: 2, version: 3, etc.) each time significant revisions are made.

---

This skill prioritizes your vision for the story. The formulas and structures above are guides, not rules—if a different approach better serves your specific story, use it. The goal is clarity and compelling communication of your story's essence.
