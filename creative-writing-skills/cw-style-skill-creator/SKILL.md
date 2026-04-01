---
name: cw-style-skill-creator
description: Create a master style guide for your novel that teaches AI to write in your voice. The style guide is loaded automatically by /beat when writing prose. Audience is AI (Claude), format is directive and example-based.
---

# Style Skill Creator

Create a master style guide that captures your novel's unique voice, rhythm, and conventions. When complete, `/beat` will automatically load this guide when writing your prose.

## Critical: Audience is AI

This creates **AI instructions** (for Claude to read), NOT **human documentation** (for authors to read).

| AI Instructions | Human Documentation |
|-----------------|---------------------|
| "When writing X, do Y" | "The story uses X because Y" |
| Directive commands | Explanatory descriptions |
| Pattern + examples | Analysis + reasoning |

**Example:**

```
✅ "Use short sentences during action sequences."
✅ "Show emotion through physical action, not emotional labels."
✅ "When a character lies, their dialogue is longer than their thoughts."

❌ "The author tends to use short sentences during action." (analysis, not instruction)
❌ "She felt nervous (shown through trembling hands)." (explanation, not directive)
```

---

## Step 1: Check for Existing Style Guide

Before creating anything new, check if a style guide already exists:

1. Look for `Style/master.md` in the vault root
2. If it exists:
   > "I found an existing style guide at `Style/master.md`. Would you like me to:
   > - **Extend it** — Add new patterns you've developed
   > - **Update it** — Refine existing patterns based on new writing
   > - **Start fresh** — Replace it with a new analysis"

3. If no guide exists, proceed to Step 2

---

## Step 2: Gather Sample Writing

Ask the user to provide sample prose:

> "To create your style guide, I'll analyze your writing patterns. Please paste 1-3 chapters or scenes of your best prose—whatever represents the voice you want to capture. You can also paste writing from authors you admire if you're still developing your style."

**What to look for in the samples:**

- **Sentence length** — Short/impactful or long/flowing? Variation patterns?
- **Dialogue style** — Tags used, action beats, subtext habits
- **POV handling** — Deep interiority or more surface-level? How often do you head-hop?
- **Description density** — Sparse and functional or lush and detailed?
- **Pacing** — Action-heavy vs. reflective? Scene structure habits?
- **Emotion expression** — Internal states named directly, shown through action, or both?
- **Tense** — Past or present? Any tense shifts?
- **Formatting quirks** — Em dash usage, ellipsis patterns, scene break markers, thought formatting

---

## Step 3: Analyze and Generate Style Guide

Analyze the samples and extract concrete patterns. Use the user's own prose as examples wherever possible.

### Format Requirements

Save to: `Style/master.md`

```yaml
---
type: style-guide
subtype: master
novel: ""              # from Meta/project.md title, or "Untitled Novel"
created: YYYY-MM-DD
last-updated: YYYY-MM-DD
tags: [style, meta]
---
```

### Required Sections

The style guide MUST include these eight sections:

---

#### ## Voice & Tone

Overall narrative register and emotional temperature.

```
**General register:**
- [Directive: formality level, e.g., "Prefer plain, unadorned language"]
- Example from their prose: [quote]

**Emotional temperature:**
- [Directive: how emotion is conveyed, e.g., "Understated—let action speak"]
- Example from their prose: [quote]

**Narrative distance:**
- [Directive: close/third/first person intimacy level]
- Example from their prose: [quote]
```

---

#### ## Sentence Structure

Length variation, rhythm patterns, complexity preferences.

```
**Sentence length:**
- [Directive: typical length, variation approach, e.g., "Use 10-15 word sentences as default"]
- Example from their prose: [quote showing the pattern]

**Rhythm:**
- [Directive: how sentences flow, e.g., "Vary sentence opening structures"]
- Example from their prose: [quote]

**Complex sentences:**
- [Directive: when to use subordinate clauses, e.g., "Reserve long sentences for reflection"]
- Example from their prose: [quote]
```

---

#### ## POV & Interiority

How deep into the character's head the narration goes.

```
**Interiority depth:**
- [Directive: e.g., "Stay in the POV character's direct experience"]
- Example from their prose: [quote]

**Thought representation:**
- [Directive: how thoughts appear, e.g., "Italics for direct thought, no quotes"]
- Example from their prose: [quote]

**Head-hopping policy:**
- [Directive: e.g., "Never leave POV character's perspective within a scene"]
- Example from their prose: [quote]
```

---

#### ## Dialogue

Tag usage, action beats, subtext, interruptions, character distinctiveness.

```
**Dialogue tags:**
- [Directive: e.g., "Prefer action beats over dialogue tags"]
- Example from their prose: [quote]

**Action beats:**
- [Directive: how to integrate action with speech]
- Example from their prose: [quote]

**Subtext:**
- [Directive: e.g., "Characters avoid saying what they mean"]
- Example from their prose: [quote]

**Interruptions and pauses:**
- [Directive: em dash vs. ellipsis usage]
- Example from their prose: [quote]

**Character voice:**
- [Directive: how characters are distinguished through speech]
- Example from their prose: [quote showing distinct voice]
```

---

#### ## Description

Sensory balance, density, metaphor style.

```
**Sensory focus:**
- [Directive: which senses dominate, e.g., "Prioritize sight and sound"]
- Example from their prose: [quote]

**Description density:**
- [Directive: sparse vs. lush, e.g., "One strong image per scene"]
- Example from their prose: [quote]

**Metaphor and simile:**
- [Directive: frequency and style, e.g., "Avoid metaphor—prefer direct observation"]
- Example from their prose: [quote]

**Environmental grounding:**
- [Directive: how settings are established]
- Example from their prose: [quote]
```

---

#### ## Pacing

Scene pacing signals, action vs. reflection balance.

```
**Action pacing:**
- [Directive: sentence-level pacing during action]
- Example from their prose: [quote]

**Reflection pacing:**
- [Directive: how reflection/pause is handled]
- Example from their prose: [quote]

**Scene transitions:**
- [Directive: how scenes end and begin]
- Example from their prose: [quote]

**Chapter rhythm:**
- [Directive: overall chapter structure patterns]
- Example from their prose: [quote]
```

---

#### ## Emotion

How emotion is shown and expressed.

```
**Showing emotion:**
- [Directive: e.g., "Show through physicality, not named emotions"]
- Example from their prose: [quote]

**Emotion intensity:**
- [Directive: peak emotional moments vs. sustained emotion]
- Example from their prose: [quote]

**Emotional range:**
- [Directive: how different intensities are handled]
- Example from their prose: [quote]

**Suppressed vs. expressed:**
- [Directive: when characters hide vs. reveal feelings]
- Example from their prose: [quote]
```

---

#### ## Formatting

Em dashes, ellipsis, scene breaks, thought formatting, special conventions.

```
**Em dashes:**
- [Directive: usage patterns, e.g., "Use em dash for interruptions and clarifications"]
- Example from their prose: [quote]

**Ellipsis:**
- [Directive: usage patterns, e.g., "Use ellipsis for trailing thoughts, not unfinished speech"]
- Example from their prose: [quote]

**Scene breaks:**
- [Directive: how to mark breaks, e.g., "Use *** centered on its own line"]
- Example from their prose: [quote]

**Thought formatting:**
- [Directive: how internal thoughts appear]
- Example from their prose: [quote]

**Other conventions:**
- [Directive: any unique formatting choices]
- Example from their prose: [quote]
```

---

#### ## Avoid

Explicit list of patterns that break this author's style.

```
**Never do:**
- [Directive: specific patterns to avoid]
- Example of what NOT to write: [counter-example]

**Tone violations:**
- [Directive: things that feel out of character]
- Example of what NOT to write: [counter-example]

**Structural taboos:**
- [Directive: structural patterns that don't fit]
- Example of what NOT to write: [counter-example]
```

---

## Step 4: Save and Confirm

1. Save the completed style guide to `Style/master.md`
2. Confirm with the user:
   > "Your style guide is saved at `Style/master.md`. When you run `/beat`, this guide will load automatically and inform how your prose is written.
   >
   > **Tip:** After major revision sessions, re-run `/style` to update the guide with new patterns you've developed."

---

## Iterative Updates

The style guide is a living document. Offer to update it when:

- User has completed significant new writing
- User notices patterns in their recent work that aren't captured
- User's style has evolved through the writing process
- User wants to add patterns from a different genre or author they admire

### Update Process:

1. Load existing `Style/master.md`
2. Ask what new patterns to add or what existing patterns to refine
3. Optionally analyze recent chapters for new patterns
4. Update the `last-updated` date in frontmatter
5. Preserve existing patterns unless explicitly requested to change

---

## Composability

- **/beat** — Loads `Style/master.md` automatically when writing prose
- **/critique** — After writing, use critique to identify what patterns emerged that should be added to the style guide
- **/bs** — Brainstorm new narrative approaches; update style guide if the approach establishes new patterns

## Example Style Guide (Complete)

```yaml
---
type: style-guide
subtype: master
novel: The Last Horizon
created: 2026-03-15
last-updated: 2026-03-15
tags: [style, meta]
---

# The Last Horizon — Style Guide

## Voice & Tone

**General register:**
- Use plain, unadorned language. No flowery prose or elevated diction.
- Short paragraphs. White space is your friend.
- Example: "The bar was empty. She sat in the corner booth."

**Emotional temperature:**
- Understated. Let physical action convey emotion rather than naming it.
- Characters don't announce their feelings—they show them.
- Example: "His jaw tightened. He didn't look at her."

**Narrative distance:**
- Close third person. Narrator knows only what the POV character knows.
- No editorial omniscience. Stay in the moment.
- Example: "She couldn't tell if he was lying."

---

## Sentence Structure

**Sentence length:**
- Default to 10-15 words. Use short sentences (under 10 words) for impact.
- Reserve long sentences for reflection or building tension before a reveal.
- Example (short): "The door opened. Rain spilled in."
- Example (long): "She stood there, trying to remember why she'd come back to this town, what she'd hoped to find that she hadn't already lost."

**Rhythm:**
- Vary sentence openings. Mix subject-verb-object with inversions and fragments.
- Read sentences aloud—if they all sound the same, vary them.
- Example: "Hard rain. Cold beer. Neither touched the ache in her chest."

**Complex sentences:**
- Use subordinate clauses sparingly. One clause maximum per sentence.
- Complex ideas need multiple short sentences, not one long one.
- Example: "The road curved. She followed it."

---

## POV & Interiority

**Interiority depth:**
- POV character's direct experience only. No outside commentary.
- Thoughts and feelings surface when they surface—don't summarize inner states.
- Example: "She locked the door. Turned the deadbolt. The click echoed."

**Thought representation:**
- Italics for direct thought. No quotation marks for thoughts.
- Present thought briefly—don't internal monologue for paragraphs.
- Example: *What does he want?* She didn't ask.

**Head-hopping policy:**
- Never leave the POV character's perspective within a scene.
- If another character's internal state matters, show it through the POV character's observation.
- Example: "He looked worried. She wondered why."

---

## Dialogue

**Dialogue tags:**
- Minimize dialogue tags. Use action beats instead.
- When tags are necessary, use "said" only. Never "exclaimed," "replied," etc.
- Example: "Fine." She turned away.

**Action beats:**
- Attach action to dialogue. The action should inform the line's emotional tone.
- Place beats before or after dialogue, not in the middle of a character's speech.
- Example: "I'm leaving." She grabbed her coat.

**Subtext:**
- Characters rarely say what they mean directly. Let tension live in the subtext.
- A flat "Okay" can carry more weight than an emotional outburst.
- Example: "That's nice." Her voice didn't change.

**Interruptions and pauses:**
- Em dash for interruptions: "Wait—I didn't mean—"
- Ellipsis for trailing thoughts or hesitation: "I thought you'd..."
- Pause indicated by em dash, not ellipsis, when the character cuts themselves off.
- Example: "You don't have to—" "Leave? I'm already gone."

**Character voice:**
- Distinguish speakers through word choice and rhythm, not dialect markers.
- A nervous character speaks in shorter fragments. A confident one finishes sentences.
- Example: "Yeah. Sure. Whatever." He shrugged.

---

## Description

**Sensory focus:**
- Prioritize sight and sound. Touch and smell are accents, not foundations.
- One strong sensory image per scene. Don't overwhelm with detail.
- Example: "Rain streaked the windows. Somewhere, a dog barked."

**Description density:**
- Sparse. Describe only what matters to the moment.
- If it doesn't affect the scene, leave it out.
- Example: "The kitchen was clean. That was unusual."

**Metaphor and simile:**
- Avoid metaphor. Prefer direct observation.
- If a metaphor occurs naturally, keep it. Don't force them.
- Example: "Her laughter faded." (Not "Her laughter fell like autumn leaves.")

**Environmental grounding:**
- Set the scene in two or three details, then move. Don't paint backgrounds.
- Let characters interact with the environment rather than observing it.
- Example: "She set her mug on the counter. The linoleum was cracked."

---

## Pacing

**Action pacing:**
- Short sentences. No subordinate clauses. Verbs carry momentum.
- Skip the blow-by-blow during rapid action. Imply movement.
- Example: "He ran. The door. The lock. Behind him, footsteps."

**Reflection pacing:**
- Use short sentences to punctuate reflection.
- Reflection shouldn't last more than a paragraph before returning to external action.
- Example: "She thought about leaving. She stayed."

**Scene transitions:**
- Use *** centered on its own line for scene breaks.
- Mark time jumps with a brief transitional line if the gap matters.
- Example: ***
- Or: "Three days later, the letter arrived."

**Chapter rhythm:**
- Alternate tension and release. Build to a cliff or revelation, then pause.
- Chapters end mid-thought when possible—a question unanswered keeps readers going.
- Example: "She opened the envelope. Inside was—"

---

## Emotion

**Showing emotion:**
- Show through physicality. Trembling hands, set jaws, averted eyes.
- Never write "She felt X" or "He was feeling X." Show it.
- Example: "Her hands shook. She hid them in her pockets."

**Emotion intensity:**
- Build to peak moments gradually. Don't rush to tears or rage.
- Sustained emotion is shown through repeated physical signs, not repeated declarations.
- Example: "First the tears came. Then the shaking. Then the grief."

**Emotional range:**
- Most emotion stays below the surface. Characters endure.
- When they break, it's earned—quiet, not theatrical.
- Example: "She didn't cry. Not then. Later, alone, she did."

**Suppressed vs. expressed:**
- Characters in conflict suppress. Characters at peace express.
- Watch for when a character would hide their true reaction—and show that.
- Example: "I'm fine." He smiled. It didn't reach his eyes.

---

## Formatting

**Em dashes:**
- Use for interruptions in speech or thought: "Wait—I need to—"
- Use for clarifications that follow: "She knew him—knew what he was capable of."
- Never use em dashes to emphasize. Plain sentence structure instead.

**Ellipsis:**
- Use for trailing thoughts: "I thought I'd never see you again..."
- Use for unfinished words when the ending is obvious: "The letter was from..."
- Not for interruptions—use em dash for that.

**Scene breaks:**
- Mark with *** centered on its own line
- Follow with a blank line before new prose
- Example:
  ```
  ***

  Morning came too soon.
  ```

**Thought formatting:**
- Italics for direct thought. No quotes.
- Keep thoughts brief—one to three sentences max.
- Example: *What was she doing here?*

**Other conventions:**
- No section headers within prose
- No footnote-style annotations
- Numbers: spell out one through nine, use numerals for 10+
- Example: "Three people. Ten dollars. Twenty miles to go."

---

## Avoid

**Never do:**
- Name emotions directly: "She felt sad" / "He was angry" / "She was scared"
- Use dialogue tags other than "said" (or no tag)
- Head-hop out of POV character's perspective
- Use flowery or elevated language: "mercurial," "cacophony," "vestiges"
- Write paragraphs longer than 150 words

**Tone violations:**
- Purple prose or melodrama
- Over-explaining a character's motivation
- Breaking the POV contract by revealing what the character doesn't know
- Sarcasm or ironic distance in the narration itself

**Structural taboos:**
- Scene breaks marked with anything other than ***
- Headers or sub-headers within prose chapters
- Backstory delivered as exposition rather than through action or dialogue
- Time jumps without transition markers

---

*This guide is loaded automatically by /beat when writing prose.*
```

(End of file - total 532 lines)
