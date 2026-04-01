# Style Guide Patterns Reference

Reference material for the `cw-style-skill-creator` skill. Use when analyzing prose samples and generating `Style/master.md`.

---

## The AI-Directive Principle

Style guides created by this skill are **instructions to Claude**, not documentation for humans.

Every entry follows the pattern:
```
**[Category]:**
- [Imperative directive — what Claude must do]
- Example from prose: "[quote]"
```

| Do | Don't |
|----|-------|
| "Use short sentences during action" | "The author tends toward short sentences in action scenes" |
| "Show emotion through physical action" | "Emotion is conveyed physically rather than being stated" |
| "Never name emotions directly" | "Direct emotional labeling is avoided" |

---

## Eight Analysis Dimensions

When analyzing prose samples, extract patterns across these eight dimensions:

### 1. Voice & Tone
- **Register**: formal/plain/colloquial/elevated
- **Temperature**: understated/lyrical/sardonic/earnest
- **Distance**: close interiority / camera-lens distance / omniscient

**Key questions:**
- Would you describe this prose as warm or cold?
- Does the narrator editorialize, or just observe?
- Is the language elevated or plain?

### 2. Sentence Structure
- **Default length**: count average words per sentence in samples
- **Variation rhythm**: do short/long sentences alternate, or cluster?
- **Clause usage**: how many subordinate clauses per sentence on average?
- **Fragment use**: intentional fragments for rhythm or impact?

**Key questions:**
- What does a "normal" sentence look like?
- How does sentence length signal mood or pace?

### 3. POV & Interiority
- **Depth**: surface-observation vs. full interiority
- **Thought format**: italics / unmarked / quoted
- **Free indirect discourse**: does narration slide into character's voice?
- **POV strictness**: how rigidly single-character is the perspective?

**Key questions:**
- Can you tell when a sentence is the character's thought vs. narration?
- Does the narrator know things the POV character doesn't?

### 4. Dialogue
- **Tag preference**: action beats / "said" only / varied tags
- **Beat placement**: before / after / never mid-speech
- **Subtext density**: how often do characters say what they mean directly?
- **Interruption markers**: em dash / ellipsis / both / neither
- **Voice differentiation**: word choice / rhythm / length / register

**Key questions:**
- Can you tell who's speaking without tags?
- What does a typical dialogue exchange look like?

### 5. Description
- **Dominant senses**: sight, sound, smell, touch, taste — which lead?
- **Density**: one detail per scene / paragraph / sentence?
- **Metaphor frequency**: common / rare / never
- **Setting integration**: characters act in settings vs. settings described separately

**Key questions:**
- How much does the reader see vs. feel?
- Does the author let detail breathe, or compress it?

### 6. Pacing
- **Action mode**: sentence length, verb density, punctuation patterns
- **Reflection mode**: how long? how often? how does the narrator exit?
- **Transition style**: hard cuts / soft fades / chapter bridges
- **Chapter structure**: what does the author consistently do at chapter end?

**Key questions:**
- How is urgency signaled at the sentence level?
- Where does the prose slow down?

### 7. Emotion
- **Show vs. tell ratio**: physicality / named emotion / both
- **Peak moment handling**: theatrical or restrained?
- **Sustained vs. punctual**: does emotion build over paragraphs, or hit in one line?
- **Suppression patterns**: when do characters hide vs. reveal?

**Key questions:**
- Is this author's emotional style loud or quiet?
- What does peak emotion look like here?

### 8. Formatting
- **Em dash usage**: interruptions / clarifications / emphasis / none
- **Ellipsis usage**: trailing / hesitation / pregnant pause
- **Scene break marker**: ***, ---, blank line, other
- **Thought format**: italic / plain / quoted
- **Other conventions**: numbers, headers in prose, chapter titles

---

## Common Patterns to Watch For

### Voice Signals
| Pattern | What it signals |
|---------|----------------|
| Short declarative sentences dominate | Minimalist / hardboiled / direct |
| Long, clause-heavy sentences | Literary / introspective / lyrical |
| Frequent fragments | Urgent / poetic / interior |
| Subordinate clauses building to a conclusion | Measured / deliberate / formal |

### Dialogue Signals
| Pattern | What it signals |
|---------|----------------|
| Mostly action beats, few tags | Modern literary / commercial |
| Rich dialogue tags ("she snapped", "he murmured") | Genre fiction / older style |
| Minimal punctuation in dialogue | Spare / hardboiled |
| Nested dialogue-within-thought | Deep interiority |

### Pacing Signals
| Pattern | What it signals |
|---------|----------------|
| Chapters end mid-action | Thriller / commercial pacing |
| Chapters end in reflection | Literary / character-driven |
| Very short chapters (under 1500 words) | Fast-paced / cinematic |
| Long chapters with multiple scenes | Epic / immersive / world-focused |

---

## Anti-Patterns (Things Style Guides Should Flag)

Every style guide's **Avoid** section should capture what breaks *this author's* voice specifically. Common categories:

- **Emotion naming**: "felt sad," "was angry," "seemed nervous" (vs. physical show)
- **Over-tagging**: "she exclaimed," "he replied," "she retorted"
- **Head-hopping**: switching POV mid-scene without a break
- **Adverb stacking**: "quickly ran," "softly whispered," "angrily said"
- **Throat-clearing**: "He thought to himself," "She said out loud," "She felt her heart race"
- **Exposition dumps**: backstory inserted as information rather than dramatized
- **Purple prose markers**: overly ornate metaphors that don't fit the register
- **Rhetorical questions in narration**: "What was she thinking?" as a narrator device

---

## Sample Extraction Technique

When given prose samples:

1. **Paste in mentally as plain text** — strip formatting, read raw
2. **Count**: average sentence length (word count), average paragraph length (sentence count)
3. **Tag 5 representative sentences** from each section (action, dialogue, reflection, description, transition)
4. **Find the outliers**: longest sentence, shortest sentence — what are they doing?
5. **Look for repetition**: what words, constructions, or rhythms appear 3+ times?
6. **Note what's absent**: what techniques common in fiction don't appear at all?

The patterns in (5) and (6) become directives. The absences in (7) become the **Avoid** section.

---

## Minimal vs. Complete Style Guides

### Minimal (cold start, no sample writing)
When the user has no sample prose yet, create a **minimal aspirational guide** — 3-4 directives per section based on stated preferences, clearly marked as provisional:

```yaml
---
type: style-guide
subtype: master
status: provisional   # add this field for guides built without prose samples
---
```

Note in the guide footer:
> *This guide is provisional — built from stated preferences, not analyzed prose. Update it with `/style` after completing your first chapter.*

### Complete (built from samples)
All eight sections fully populated, every directive backed by a quote from the author's own prose.

---

*This reference is used by `cw-style-skill-creator` during style guide generation.*
