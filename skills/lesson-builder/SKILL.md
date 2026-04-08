---
name: eu-lesson-builder
description: "Author and produce lesson content for ElevenLabs Academy — instructional design, VO scripts, Remotion specs, Arcade recording specs, and WorkRamp text companions. Use this skill whenever Jake asks to: write a lesson, draft a lesson, author a lesson, create lesson content, build out a lesson, write a VO script, create a text companion, write an Arcade spec, flesh out a skeleton, turn a skeleton into a script, produce a lesson, or any variation of creating/updating deliverables for a specific lesson. Also trigger on: 'let's build L1.2', 'draft M3 lesson 4', 'write the text for lesson 2.3', 'create the Arcade plan for L4.1', 'let's do M3-L2', 'spec out the lesson', 'what do we need for L5.2', or 'let's knock out the next lesson'. This is the primary skill for all lesson production — from instructional design through final deliverables."
---

# ElevenLabs Academy — Lesson Builder

This skill is the complete lesson production engine for the ElevenLabs University Agent Builder Certification. It combines instructional design methodology with multi-deliverable production to take any lesson from skeleton entry to finished outputs.

Every lesson produces up to three deliverables:
1. **Lesson script + clean VO** — narrative, production cues, and extracted voiceover
2. **Visual spec** — Remotion video spec and/or Arcade recording spec
3. **Text companion** — WorkRamp-ready content document

---

## Before You Start — Always Do These

1. **Invoke `/elevenlabs-academy:elevenlabs-brand`** — Load brand guidelines. All copy must match ElevenLabs tone: confident, warm, not hype-y, not robotic.
2. **Read the Production Guide** — `01 - Certification Program/Planning & Reference/Lesson_Production_Guide.md` — Confirm the lesson's content type (Video, Arcade, or Both), what's been drafted, and production notes.
3. **Read the Module Structure** — `01 - Certification Program/Academy_Module_Structure_Draft.md` — Context on where this lesson sits in the curriculum.
4. **Check for existing drafts** — Look in `01 - Certification Program/Experiments/v3-compact/` and `01 - Certification Program/Lessons/` for any existing scripts or VO files.

---

## A. Input Requirements

### Required
1. **Lesson identifier** — M#-L# format (e.g., M3-L1, M5-L2)
2. **Skeleton entry** — Read from `01 - Certification Program/Planning & Reference/Lesson_Skeleton_Draft.md`. Extract: title, type, duration, what-it-covers, practice, comprehension check.

### Auto-derived (don't ask — look these up)
3. **Module position** — Which module, what came before, what comes after.
4. **Prior knowledge** — What the learner has already built and learned. Derive from previous lesson entries.
5. **Scaffolding level** — Determined by module number (see Section C).

### Optional (ask if unclear)
6. **Version number** — Default to v1 unless iterating.
7. **Specific focus areas** — Jake may want to emphasize certain aspects.

---

## B. Instructional Design Framework

Every lesson must satisfy these frameworks. Weave them NATURALLY into the content — never labeled as "STEP 1: GAIN ATTENTION." The learner experiences them without seeing the scaffolding.

### Gagne's Nine Events

Verify each is present before delivering the lesson script:

1. **Hook** — Open with a callback to something the learner built, a real-world problem, or a "what if" scenario. Never open with "In this lesson you'll learn..."
2. **Objectives** — State what the learner will be able to DO. Use observable action verbs: configure, build, test, compare, deploy, design, evaluate, create. Never: understand, learn, know.
3. **Prior recall** — Explicitly reference something from a previous lesson. "Remember when you configured your agent's system prompt? Now we're going to..."
4. **Content presentation** — Core instruction. Chunk into discrete sections, each covering ONE concept or skill. Explain what → how → when/why.
5. **Guided learning** — Worked examples, walkthroughs, demonstrations. Every concept needs visible proof.
6. **Practice** — The learner DOES something. Not watching, not reading — doing.
7. **Feedback** — Show consequences of choices, not just correct/incorrect.
8. **Assessment** — Comprehension check questions for heavier concept lessons. MC (A/B/C/D), 1-2 max.
9. **Bridge** — Connect to the next lesson and to real-world application.

### Merrill's First Principles

For each lesson, answer:

- **Problem-centered:** What real-world task does this help accomplish?
- **Activation:** What does the learner already know that connects?
- **Demonstration:** Where is the concept shown, not just explained?
- **Application:** Where does the learner practice IN CONTEXT?
- **Integration:** How does the learner adapt this to THEIR use case?

### Action Mapping Filter

| If the content is... | Then... |
|---|---|
| **Must-know** — directly supports a learning objective | Include in the main flow |
| **Should-know** — helpful but not blocking | Put in an accordion or "Good to Know" callout |
| **Nice-to-know** — interesting but not actionable | Cut it or link to docs |

### Scaffolding Progression (4C/ID)

| Modules | Level | What it looks like |
|---|---|---|
| **M1-M2** | Maximum | Every click shown. Detailed annotations. "Click the Configure tab..." |
| **M3-M4** | Medium | Key steps shown, routine navigation assumed. |
| **M5-M6** | Goal-oriented | Steps outlined but not hand-held. |
| **M7-M8** | Minimal | Complex scenario, light guidance. Near-certified. |

Module position OVERRIDES lesson type. A Concept lesson in M1 gets max scaffolding. Same type in M8 gets minimal.

---

## C. Lesson Type Patterns

### Concept Lesson
1. Hook → 2. Objectives (2-3) → 3. Core concept (architecture diagram) → 4. How it works → 5. When/why (decision framework) → 6. Recap + reference card → 7. Comprehension check → 8. Bridge

**Production:** Heavy Remotion (concept diagrams, comparison cards). Fewer screen recordings.
**VO tone:** Reflective, explanatory. "Here's what's happening under the hood..."

### Walkthrough Lesson
1. Hook → 2. Objectives (2-4) → 3-N. Walkthrough segments (context + recording + steps + annotations) → Recap → Practice → Bridge

**Production:** Heavy screen recordings with overlays. Remotion for intro/section breaks/outro only.
**VO tone:** Direct, guiding. "Now click here..." "Watch what happens..."

### Hands-On Lesson
1. Hook → 2. Objectives → 3. Worked example (watch instructor build) → 4. Guided practice (learner builds with guidance) → 5. Independent practice (goal only) → 6. Debrief → 7. Bridge

**Production:** Screen recording for worked example, text companion carries practice.
**VO tone:** Encouraging, coach-like. "Your turn..." "Try this..."

### Hybrid Lessons (most common)
Follow the first type's pattern, insert a clear transition ("Now let's put this into practice"), then follow the second type's pattern.

---

## D. The Three Deliverables

### 1. Lesson Script + Clean VO

**Lesson script:** VO narrative + production directions (Remotion callouts, screen recording cues) + text companion content in one document.

**Clean VO:** Extracted narration only — no headers, no formatting, no stage directions. Just spoken words paragraph by paragraph with word count and duration estimate (words / 145 = minutes).

**VO writing rules:**
- ~145 words/min conversational pace
- 3 min video ≈ 435 words, 4 min ≈ 580 words
- Active voice, second person ("you'll configure," "your agent")
- Contractions always ("you'll," "it's," "don't")
- No jargon without context — define terms on first use
- Voice-first but omnichannel — lead with voice, acknowledge chat/messaging

**File naming:**
- Script: `M{X}-L{Y}_v{Z}_Title.md`
- VO: `M{X}-L{Y}_v{Z}_VO.md`

### 2. Visual Spec (depends on content type)

#### Remotion Spec (Video lessons)

Scene-by-scene blueprint for the Remotion build agent. **Invoke `/elevenlabs-academy:remotion-spec-builder`** for the detailed spec drafting guidance, layout library, and two-mode scene system.

Key rules:
- Every scene gets a layout, component, duration, VO beat, and Screengrab flag
- Mark `Screengrab: Yes` for architecture diagrams, feature grids, step flows, checklists
- Mark `Screengrab: No` for title cards, outros, atmospheric/transitional scenes
- Title card always uses `WaveformScene`, outro always uses `OutroScene`

**Output:** `10 - Remotion/specs/M{XX}L{YY}v{Z}-spec.md`

#### Arcade Recording Spec (Arcade lessons)

Detailed screen recording plan for the Arcade Mac app. Read `references/arcade-spec-guide.md` for the full format. Key elements per segment:
- Segment name, starting screen (URL/UI state)
- Click path (step-by-step), hotspot placements
- Callout text, spotlight areas
- Chapter steps, end state, estimated step count

**Output:** `01 - Certification Program/Specs/Arcade/M{XX}L{YY}_arcade-spec.md`

### 3. Text Companion (every lesson)

WorkRamp-ready content document. Read `references/workramp-text-companion-guide.md` for the full block mapping. The text companion mirrors the video section structure exactly — same sections, same order, same headings.

**Building blocks:**

| Block | Use |
|---|---|
| **Hero Context** | Every lesson opener — title, meta badges, learning objectives |
| **Annotated Screenshots** | Major UI moments. Max 3-4 annotations per image. Amber (#F59E0B) highlights. |
| **Short GIFs** | 5-10s loops for multi-click flows where screenshots fail |
| **Step Sequences** | Numbered steps with connecting line. 1:1 translation of walkthroughs. |
| **Callout: Course Connection** | Links to other modules (Graphite border) |
| **Callout: Key Insight** | Important takeaways (Green border) |
| **Callout: Good to Know** | Optional helpful context (Blue border) |
| **Callout: Warning** | Pitfalls and gotchas (Amber border) |
| **Reference Cards** | Comparison tables, decision frameworks, cheat sheets |
| **Accordions** | Expandable deeper detail — keeps main flow clean |
| **Diagrams** | Static versions of Remotion motion graphics |
| **Practice Section** | Numbered action checklist. Progressive: direct task → adapt for own use case. |
| **Next Lesson Card** | Dark footer pointing to next lesson with teaser |

**Progressive disclosure:**
- Must-know → visible in main flow
- Should-know → in accordions
- Could-know → in "Good to Know" callouts or linked to docs

---

## E. Lesson Script Output Format

```markdown
# Module X, Lesson Y: [Title] (v[version])

**Module:** X — [Module Landing Page Title]
**Lesson:** X.Y — [Lesson Title]
**Type:** [Concept | Walkthrough | Hands-On | hybrid]
**Duration:** ~X min video, ~Y min text read
**Format:** ElevenLabs AI voiceover + Remotion motion graphics [+ screen recordings], assembled in Premiere Pro

---

## Learning Objectives

By the end of this lesson, learners will be able to:
1. [Action verb] + [observable outcome]
2. [Action verb] + [observable outcome]

---

## Production Notes

- **Voiceover:** ElevenLabs AI voice — [tone notes]
- **Pacing:** [pacing guidance]
- **Music:** [music direction]

---

## VIDEO SCRIPT

### [SECTION NAME] [timestamp range]

> **[REMOTION: `CompositionID` — Description. Layout, content, animation notes.]**

OR

> **[SCREEN RECORDING: What to show. Duration. Overlay specs.]**

**VO:**

[Narration text in plain conversational prose.]

---

## Composition Summary

| Composition ID | Duration | Type | Key Visual |
|---|---|---|---|
| `M0XL0Y-Name` | X sec | Remotion / Screen Rec | Description |

## Screen Recording List

| Recording | What to Show | Est. Duration | Overlays Needed |
|---|---|---|---|

---

## TEXT COMPANION

[Mirrors video section structure using building blocks from Section D.3]

### Practice

[Numbered checklist]

### Up Next

> **Lesson X.Y — [Next Lesson Title]**
> [One sentence teaser]
```

---

## F. Writing Style — Jake's Voice

All lesson content should sound like a warm, knowledgeable person talking to another person. Not a textbook. Not a corporate training deck.

**Talk to a person, not a student:**
- "Every interaction with a person" — NOT "Every interaction your business has with a customer"
- "There are eight modules" — NOT "Eight modules." (too structural)
- "It's where you build..." — contractions are natural, use them always

**Natural sentence flow:**
- Vary energy and pacing. Some lines are punchy. Some flow longer.
- Conversational connectors: "And then there's..." / "From there, you go deeper..."
- Let exclamation marks land when there's genuine energy

**Avoid:**
- Corporate speak: no "leverage," "utilize," "comprehensive," "robust," "seamless"
- Cold structural openers: no "Module 1 covers..." or "In this lesson, you will learn..."
- AI-isms: no "Let's dive in," "Here's the thing," "It's worth noting that"
- Hedging: no "essentially," "basically," "it's important to understand that"

**Mechanics:**
- Contractions always. Em dashes for pauses — not semicolons. Short paragraphs. Active voice. Second person.

---

## G. Content Quality Rules

### Writing
- **Headings:** Descriptive actions, not clever labels. "Configure the Backup LLM Chain" not "Safety Net."
- **Paragraphs:** One idea per paragraph. 2-4 sentences max.
- **Bold:** Key terms bold on first use only. Never for emphasis — use callouts.
- **Lists:** 3+ items. Bullets for unordered, numbers for sequential.
- **Inverted pyramid:** Most important info first in every section.

### Accuracy & Naming
- **Product names:** ElevenAgents, ElevenCreative, ElevenAPI (one word each)
- **Credential:** "ElevenLabs Certified ElevenAgent Builder" — exact, every time
- **Company:** ElevenLabs (one word, capital E, capital L)
- **Origin story:** Founded as a research company to solve dubbing. NOT "to solve the conversation volume problem."
- **Voice-first-plus:** Lead with voice, acknowledge chat/messaging channels
- **Module references:** Use landing page titles (see below)

### What to Avoid
- No marketing copy, no superlatives, no hype, no unsubstantiated claims
- No jargon without context — define on first use
- No "understand" objectives — use observable verbs only

---

## H. Comprehension Checks & Module Quizzes

### In-Lesson Checks
- Heavier concept lessons only. Not every lesson.
- Always MC — A, B, C, D. No free-text.
- 1-2 questions max per lesson.
- Application/identification/comparison types. Plausible distractors.

### Module Quizzes
- 5-10 questions covering all lessons in the module.
- M3+: include 1-2 questions from PREVIOUS modules (spaced retrieval).
- Brief rationales for correct answers.

---

## I. Quality Checklist

Run through before delivering:

1. [ ] Learning objectives use observable action verbs
2. [ ] All nine Gagne events present
3. [ ] VO connects to what learner has already done (prior recall)
4. [ ] Every concept has visible proof (diagram, screenshot, recording)
5. [ ] Text companion mirrors video section structure exactly
6. [ ] Callout types used correctly
7. [ ] Module/lesson references use 8-module numbering and landing page titles
8. [ ] Product names correct (ElevenAgents, ElevenCreative, ElevenAPI)
9. [ ] Credential name exact
10. [ ] Voice-first-plus framing
11. [ ] Scaffolding matches module position
12. [ ] No marketing language in instructional content
13. [ ] MC questions are A/B/C/D if present
14. [ ] Practice section exists if skeleton includes one
15. [ ] Next lesson card points to correct next lesson
16. [ ] File naming follows convention
17. [ ] Action Mapping filter applied: no "nice to know" in main flow

---

## J. Production Flow

Follow this order for any lesson:

1. **Identify content type** — Check the Production Guide (Video, Arcade, or Both)
2. **Gather context** — Read skeleton, module structure, prior lessons, determine scaffolding
3. **Author the lesson script** — Apply instructional design framework, lesson type pattern, writing style
4. **Extract the clean VO** — Strip production directions, output VO-only file with word count
5. **Write the Remotion spec** (if video) — Invoke `/elevenlabs-academy:remotion-spec-builder`
6. **Write the Arcade recording spec** (if Arcade) — Use `references/arcade-spec-guide.md`
7. **Write the text companion** — Structured for WorkRamp copy-paste
8. **Run quality checklist** — Verify all 17 items
9. **Present to Jake** — Jake makes all decisions

---

## K. Module Titles (Landing Page Names — Use These)

1. The Platform & Your First Agent
2. Voice & AI Foundations
3. Prompt Engineering
4. Knowledge & Tools
5. Advanced Architecture
6. Deployment
7. Testing & Evaluation
8. Production Operations
- Certification Exam — Prove It (separate, paid)

**Credential:** "ElevenLabs Certified ElevenAgent Builder"

---

## L. Content Model — Not Every Lesson Gets a Video

- **Text companion:** Every lesson (baseline)
- **Video (Remotion + screen recordings):** When the lesson needs audio examples, motion graphics, or a "wow moment"
- **Arcade interactive demo:** When the lesson is primarily UI navigation — clickable walkthroughs
- **Some lessons get both video AND Arcade**

Check the Production Guide to determine which visual medium each lesson uses.

---

## M. Key Brand/PMM Rules

- **Three pillars:** Research-backed, Configurable, Trusted
- **"We are the source"** — competitors license ElevenLabs models
- **Voice-first but omnichannel** — lead with voice, acknowledge chat/messaging
- **No "one linear path" language** — use "core agents certification path"
- **Tone:** Confident, warm, instructional. Not hype-y. Not robotic. Not salesy.

---

## N. Reference Files

| File | When to Read |
|------|-------------|
| `references/workramp-text-companion-guide.md` | When writing any text companion |
| `references/arcade-spec-guide.md` | When writing an Arcade recording spec |
| `references/remotion-spec-guide.md` | When writing a Remotion video spec |

### Exemplar scripts
- `01 - Certification Program/Experiments/v3-compact/M1-L1_v4_Welcome_to_ElevenLabs.md` — concept lesson
- `01 - Certification Program/Experiments/v3-compact/M1-L2_v1_The_Agents_Platform.md` — walkthrough lesson
- `01 - Certification Program/Experiments/v3-compact/M1-L1_v4_VO.md` — clean VO script

### Related skills
- `/elevenlabs-academy:remotion-spec-builder` — Detailed Remotion spec drafting (layout library, two-mode system)
- `/elevenlabs-academy:eu-remotion-builder` — Build Remotion code from specs
- `/elevenlabs-academy:elevenlabs-brand` — Brand guidelines enforcement
- `/elevenlabs-academy:eu-project-context` — Naming conventions, curriculum structure

### Technical reference
- `06 - Content Library/Docs & Guides/LLMS-Full ElevenLabsDevDocs.txt` — Platform capabilities, API details
- `06 - Content Library/Docs & Guides/Arcade llms-full.txt` — Arcade platform docs
