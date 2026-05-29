---
name: novelseed
description: AI novel-writing agent. Given a one-sentence idea, NovelSeed generates a complete novel: genre detection, world-building, character design, outline, chapter-by-chapter writing with quality checks, and AI-style removal. Supports all genres (fantasy, urban, romance, suspense, sci-fi, historical). Trigger when user wants to write a novel, create a story, develop characters, or asks for fiction writing help.
license: AGPL-3.0
platforms: [linux]
---

# NovelSeed — Open-Source Novel Writing Agent

NovelSeed takes a single premise and grows it into a complete novel through structured, multi-phase generation.

## When to Use

Apply when the user wants to:
- Write a novel but only has a vague idea
- Generate a complete story from a premise
- Develop characters, world-building, or plot outlines
- Get quality-checked chapters with AI-style removal

## Agent Workflow

```
User Input: "我想写一个都市悬疑小说，主角是个退役刑警"
    ↓
Phase 1: Genre Detection → Load genre template
    ↓
Phase 2: Three-Layer Questionnaire → Lock in core settings
    ↓
Phase 3: World-Building → 72-point setting checklist
    ↓
Phase 4: Character Generation → Protagonist + antagonist + supporting cast
    ↓
Phase 5: Outline → Snowflake Method 12-step
    ↓
Phase 6: Chapter Writing → Write → Quality Check → De-AI → Repeat
```

## Phase 1: Genre Detection

Detect the genre from the user's premise. Load the corresponding template from `references/genres/`.

| Genre | Template | Key Elements |
|-------|----------|-------------|
| Urban (都市) | `urban.md` | Real-world setting, relationships, career |
| Fantasy/Immortal (修仙) | `fantasy.md` | Power systems, realm progression, magical rules |
| Suspense/Mystery (悬疑) | `suspense.md` | Clue pacing, red herrings, reveal timing |
| Romance (言情) | `romance.md` ✏️ | Relationship arcs, misunderstandings, resolution |
| Sci-Fi (科幻) | `scifi.md` ✏️ | Technology rules, world logic, future society |
| Historical (历史) | `historical.md` ✏️ | Period accuracy, power structures, language |

✏️ = template coming soon (PRs welcome!)

Multiple genres can blend (e.g., urban + suspense). Pick one primary, others as secondary.

## Phase 2: Three-Layer Questionnaire

### Layer 1: Core Position (Required)

```
Q1: Genre and premise?
  Urban / Fantasy / Suspense / Romance / Sci-Fi / Historical
  (Can blend: pick primary + secondary)

Q2: Protagonist?
  Male lead / Female lead / Dual leads / Ensemble cast

Q3: Core conflict?
  Life-or-death / Uncover truth / Revenge / Growth
  Forbidden love / Power struggle / Protection
```

### Layer 2: Deep Customization (Recommended)

```
Q4: World scale?
  Single city / Single nation / Multi-continent / Multi-world

Q5: Narrative POV?
  First person / Third person limited / Third person omniscient

Q6: Core theme?
  Growth / Redemption / Resistance / Love / Truth / Survival

Q7: Reader demographic?
  Male-oriented / Female-oriented / All ages

Q8: Chapter count?
  30 (short) / 100 (medium) / 300+ (long) / 600+ (epic)
```

### Layer 3: Style (Optional)

```
Q9: Narrative tone?
  Hot-blooded / Cold / Light / Serious / Dark humor

Q10: Prose style?
  Concise / Flowery / Plain / Web-novel style
```

## Phase 3: World-Building

Fill in the 72-point setting checklist (see `references/long-novel-infrastructure.md`). Key categories:

- **Power/Magic System**: Rules, limitations, progression path
- **Social Structure**: Factions, hierarchies, economy
- **Geography**: Key locations, travel methods, climate
- **History**: Backstory events, myths, conflicts
- **Technology**: Level, rules, limitations

Each genre template in `references/genres/` provides defaults for its category.

## Phase 4: Character Generation

### Protagonist
- Name, age, appearance, background
- Core motivation (what they want)
- Flaw (what holds them back)
- Growth arc (how they change)
- Special ability or trait
- Speech patterns, habits

### Antagonist
- Motivation (why they oppose — must be rational from their view)
- Resources and power
- Connection to protagonist
- Their own "code" or philosophy

### Supporting Cast
- 3-5 key characters
- Each: relationship to protagonist, function in plot, distinct voice

**Character label system** (prevent inconsistency):
1. Give each character 3 core labels
2. Rank labels by importance
3. Every action must align with top-ranked label

Example (generic):
```
Hot-headed > Calculating
Loyal > Self-preserving
Impulsive > Patient
```

## Phase 5: Outline (Snowflake Method)

Use the 12-step Snowflake Method:

```
Step 1:  One-sentence summary
Step 2:  Five-sentence outline (setup, conflict, development, climax, resolution)
Step 3:  Character cards (motivation, goal, conflict, epiphany per character)
Step 4:  One-page outline (expand each sentence to paragraph)
Step 5:  Character backgrounds (full story per major character)
Step 6:  Four-page outline (expand each paragraph to page)
Step 7:  Character bible (appearance, habits, catchphrases, history)
Step 8:  Scene list (all scenes)
Step 9:  Scene planning (detailed per scene)
Step 10: Draft writing (write by scene)
Step 11: De-AI polish (remove AI patterns)
Step 12: Export to format
```

## Phase 6: Chapter Writing Loop

### Per-Chapter Workflow

```
1. Determine current phase (see Six-Phase Rhythm Control below)
2. Write chapter draft
3. Quality check (Five-Dimension Scoring)
4. De-AI polish (24-pattern detection)
5. Hook injection (13 hook types)
6. Deliver to user
```

### Six-Phase Rhythm Control

| Phase | Position | Outline Scope | Spoiler Filter | Focus |
|-------|----------|--------------|----------------|-------|
| **Opening** | ≤12% | This chapter only | Strict (filter all) | Build mystery slowly |
| **Early Development** | 12-35% | ±1 chapter | Medium (filter twists) | Steady progression |
| **Mid Development** | 35-60% | ±2 chapters | Minimal (filter ending only) | Push forward, don't rush |
| **Late Development** | 60-78% | ±2 chapters | Minimal (filter ending only) | Build momentum |
| **Climax** | 78-92% | ±2 chapters | None | Maximum tension, tie threads |
| **Resolution** | ≥92% | ±1 chapter | None | Focus on ending, callbacks |

### Five-Dimension Quality Score

After each chapter, self-check:

| Dimension | Weight | Pass | Excellent |
|-----------|--------|------|-----------|
| Conflict Intensity | 25 | ≥15 | ≥22 |
| Emotional Density | 20 | ≥12 | ≥18 |
| Anticipation | 20 | ≥12 | ≥18 |
| Rhythm Control | 20 | ≥12 | ≥17 |
| Hook Design | 15 | ≥10 | ≥14 |
| **Total** | **100** | **≥60** | **≥85** |

### Quick Self-Check Questions

1. **Conflict**: Is there opposing force? Is conflict escalating?
2. **Emotion**: Will readers feel emotional shifts? (None = fail)
3. **Anticipation**: Must reader turn the page? (No = hook too weak)
4. **Rhythm**: Is this chapter fast or slow? Different from previous?
5. **Hook**: What hook type is used? (See `references/hook-techniques.md`)

### Boring-Chapter Detection

Any of these → rewrite:
- 3+ consecutive paragraphs of pure event listing with no emotion
- 3+ "then"/"after that"/"next" connectors
- Long environment descriptions that don't advance plot
- Low information density (1 useful fact per paragraph)

Fix formula: `Event → Surprise/Conflict → Emotional Response → Suspense Hook`

## De-AI Polish

After writing, scan for 24 AI-detection patterns (see `references/ai-detection-patterns.md`). Key signals:

- Meaning inflation (overly dramatic words)
- Vague attribution ("somehow", "for some reason")
- Overuse of "because... therefore..."
- Three-rule abuse (always listing things in threes)
- Emotional labels instead of emotional scenes
- Template transitions ("Meanwhile...", "Just then...")

Fix: inject real voice — irregular sentences, personal opinions, sensory details, imperfect dialogue.

## Four Iron Rules

1. **Character > Plot** — Characters drive plot, not the reverse
2. **Asymmetric Conflict** — True tension requires information asymmetry
3. **Every Chapter Needs Uncertainty** — At least one unresolved question per chapter
4. **Dialogue is a Battlefield** — Every line attacks, defends, or probes

### Making Characters Feel Alive

Characters should have:
- Physical sensations (hunger, fatigue, pain)
- Irrational emotions (mood swings, gut feelings)
- Catchphrases and verbal tics
- Fixed behavioral patterns (nervous habits, rituals)

Characters should NOT:
- Always say the "right" thing
- Be perfectly rational
- Have emotions that are "just right" for the situation

## Golden Three Chapters (Opening Rules)

| Position | Requirement |
|----------|------------|
| First 300 words | Hook: first small stimulus |
| First 500 words | Establish protagonist's core trait |
| End of Chapter 1 | Cliffhanger |
| First 3 chapters | Establish main plot + protagonist + core conflict |

## Pleasure Point Density

Web-novel standard for long-form:
```
Every 3 chapters   → Small win (face-slap, skill unlock, small gain)
Every 10 chapters  → Medium win (identity reveal, combat breakthrough, romantic advance)
Every 30 chapters  → Big win (major antagonist defeated, major secret revealed)
Every 100 chapters → Epic win (world changes, protagonist transformation)
```

## References

- `references/genres/` — Genre-specific templates (world-building defaults, common tropes, reader expectations)
- `references/long-novel-infrastructure.md` — 72-point setting checklist for long serials
- `references/hook-techniques.md` — 13 types of chapter-end hooks with examples
- `references/ai-detection-patterns.md` — 24 AI writing patterns and how to fix them
- `references/quality-checklist.md` — Detailed quality scoring rubrics
- `references/anti-template-rules.md` — Four iron rules + making characters feel alive + multi-character scenes
