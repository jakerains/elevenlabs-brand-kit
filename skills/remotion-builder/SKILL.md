---
name: eu-remotion-builder
description: "Build Remotion video compositions from spec files for ElevenLabs University. This skill takes structured spec markdown files (from the elevenlabs-remotion spec-drafting skill) and generates the actual React/TypeScript code: scene components, Zod schemas, combined compositions, and Root.tsx registrations. Use this skill whenever you need to: implement a spec, build a composition from a spec, code a lesson video, generate scene components, create new layout components, update existing compositions to match an updated spec, register new scenes in Root.tsx, or fix/debug Remotion rendering issues. Also trigger when Jake says things like 'build this spec', 'implement M03L02', 'code up the scenes', 'render this lesson', 'add this scene to the composition', or any task involving writing Remotion React code for the ElevenLabs University video project. Even casual mentions like 'make the video' or 'build the Remotion for this' should use this skill."
---

# ElevenLabs Remotion Builder Skill

This skill takes spec files and builds actual Remotion compositions for ElevenLabs University lesson videos. It's the implementation counterpart to the `elevenlabs-remotion` spec-drafting skill.

## Your Role

You are the code agent. You receive a completed spec file (a markdown document describing every scene in a lesson video) and you produce:

1. **Scene components** — React/TSX files in `src/components/`
2. **Zod schemas** — added to `src/schemas.ts`
3. **Combined composition** — a `src/M{XX}L{YY}v{Z}.tsx` file stitching all scenes with TransitionSeries
4. **Root.tsx registrations** — individual Composition entries for each scene + the combined preview

## Project Setup

This is an existing Remotion 4.0 project. Key facts:

- **Remotion version:** 4.0.438
- **React:** 19
- **Zod:** 4.3.6
- **FPS:** 30
- **Resolution:** 1920×1080
- **Package:** `elevenlabs-university-video`

### File Structure

```
remotion/
├── public/
│   ├── fonts/          — KMR Waldenburg OTFs (300, 400, 600, 700)
│   ├── logos/          — Logo-black.png, ElevenLabs_Icon_Black.svg
│   ├── covers/         — Cover0.jpg, Cover1.jpg (Chladni patterns)
│   └── icons/          — Product icons (tts.png, convai.png, etc.)
├── src/
│   ├── brand.ts        — Colors, typography, font loading (BRAND constants)
│   ├── schemas.ts      — All Zod schemas (one file, all components)
│   ├── Root.tsx         — Composition registry
│   ├── M01L01v3.tsx     — Combined composition example (13 scenes)
│   ├── components/
│   │   ├── ChladniPattern.tsx  — SVG patterns + NoiseOverlay + AccentLine
│   │   ├── IILogo.tsx          — Programmatic II bars
│   │   ├── IIWatermark.tsx     — Persistent bottom-right mark
│   │   ├── WaveformScene.tsx   — Split title card (opener)
│   │   ├── OutroScene.tsx      — Split title card (closer)
│   │   ├── [other scene components...]
│   │   ├── v2/                     — V2 Hero mode components
│   │   │   ├── GradientBackground.tsx   — Full-bleed bg with blur+noise+tint
│   │   │   ├── BrandedCard.tsx          — Card with variant system (darkflat default). Exports: BrandedCard, getCardColors(), CardVariant type
│   │   │   ├── WaveformSceneV2.tsx      — Full gradient title card
│   │   │   ├── TextRevealSceneV2.tsx    — Gradient + frosted 3-card reveal
│   │   │   ├── OriginStoryV2.tsx        — Full gradient origin narrative
│   │   │   ├── PlatformEvolutionV2.tsx  — Gradient + frosted step flow
│   │   │   ├── ChannelStripV2.tsx       — Gradient + frosted channel panels
│   │   │   ├── WelcomeCardV2.tsx        — Gradient centered hero
│   │   │   ├── ThreePillarsSceneV2.tsx  — Gradient + frosted platform cards
│   │   │   ├── PillarDetailSceneV2.tsx  — White/gradient split + 2x2 grid
│   │   │   ├── FoundationDiagramV2.tsx  — Gradient + frosted connected rows
│   │   │   ├── AgentExperienceSceneV2.tsx — Gradient + frosted 3-card showcase
│   │   │   ├── TimelineV4V2.tsx         — White/gradient split + module grid
│   │   │   └── OutroSceneV2.tsx         — Full gradient outro
│   │   └── layouts/
│   │       ├── TwoColumnCards.tsx
│   │       ├── FourGridCards.tsx
│   │       ├── SingleFeatureCard.tsx
│   │       ├── QuoteCard.tsx
│   │       ├── SideBySideComparison.tsx
│   │       ├── StatNumber.tsx
│   │       ├── StatRow.tsx
│   │       ├── NumberedSteps.tsx
│   │       ├── Checklist.tsx
│   │       ├── IconRow.tsx
│   │       ├── CodeDisplay.tsx
│   │       ├── FullBleedPlaceholder.tsx
│   │       └── SplitQuote.tsx
│   └── overlays/
│       ├── LowerThird.tsx
│       ├── CalloutLabel.tsx
│       ├── SectionBumper.tsx
│       └── HighlightBox.tsx
└── package.json
```

## How to Use This Skill

### Step 1: Read the Spec

The spec file tells you everything: what scenes to build, what layout each uses, what content goes where, and how long each scene lasts. Read it carefully — it's your blueprint.

Spec files live in `10 - Remotion/` and follow the naming pattern `M{XX}L{YY}v{Z}-spec.md`.

### Step 2: Check What Already Exists

Before writing any code, check what components already exist. Most specs reuse existing layouts with different content — you shouldn't create a new component unless the spec explicitly calls for a new layout type.

Load `references/existing-components.md` for the full inventory of scene components, layout components, and shared elements.

### Step 3: Build

For each scene in the spec:

1. **If the component exists** — use it with props from the spec's Content section
2. **If a layout exists but no scene component** — wrap the layout in a scene shell (header + background + watermark)
3. **If nothing fits** — create a new component following the established patterns

Then:
4. Add any new schemas to `src/schemas.ts`
5. Create the combined composition file (`src/M{XX}L{YY}v{Z}.tsx`)
6. Register everything in `src/Root.tsx`

### Step 4: Verify

After building, run `npx remotion studio` to verify. Check that:
- All scenes render without errors
- Transitions are smooth (fade, 20 frames)
- Typography and colors match the brand
- II watermark appears on all scenes except the title card
- Duration matches the spec

## Core Rules

Load `rules/` files for detailed patterns. Here's the essential summary:

### Brand System (always enforced)

Load `rules/brand-system.md` for the complete reference. Key constants:

```typescript
import { BRAND } from "../brand";

// Colors — monochrome only
BRAND.GRAPHITE    // #1E1916 — text/elements, NEVER backgrounds
BRAND.OFF_WHITE   // #FAFAFA — every scene background
BRAND.CREAM       // #F5F3F1 — card backgrounds
BRAND.LIGHT_GRAY  // #E0DEDC — dividers, borders
BRAND.MID_GRAY    // #999999 — labels, secondary text
BRAND.DARK_GRAY   // #555555 — body text

// Typography
BRAND.FONT_FAMILY // KMR Waldenburg with fallbacks
BRAND.LABEL_SIZE  // 14px — labels (weight 600, uppercase, tracking 0.1em)
```

### Animation System

Load `rules/animation-patterns.md` for the full reference. Summary:

- **Every animation** uses `spring({ frame, fps, config: { damping: 200 } })`
- **Cards** enter from below: `translateY(40px → 0)`, staggered 15 frames apart
- **Headers** enter from below: `translateY(12px → 0)`
- **List items** enter from the side: `translateX(15px → 0)`, staggered 4 frames apart
- **Badges** scale in: `scale(0 → 1)`, delay 60 frames
- **Transitions** between scenes: fade only, 20 frames, linear timing
- **Never use CSS transitions or animations** — only `useCurrentFrame()` + `spring()`/`interpolate()`

### Component Patterns

Load `rules/component-patterns.md` for the full reference. Summary:

Every scene component follows this structure:

```tsx
import { AbsoluteFill, useCurrentFrame, useVideoConfig, spring, interpolate, staticFile } from "remotion";
import { z } from "zod";
import { BRAND } from "../brand";
import { ChladniPattern, NoiseOverlay } from "./ChladniPattern";
import { IIWatermark } from "./IIWatermark";
import { SomeSchema } from "../schemas";

export const SomeScene: React.FC<z.infer<typeof SomeSchema>> = ({
  prop1 = "default",
  prop2 = "default",
}) => {
  const frame = useCurrentFrame();
  const { fps } = useVideoConfig();

  // Spring animations with damping: 200
  const headerProgress = spring({ frame, fps, config: { damping: 200 } });

  return (
    <AbsoluteFill style={{ backgroundColor: BRAND.OFF_WHITE }}>
      <ChladniPattern opacity={0.03} variant="geometric" position="right" color={BRAND.LIGHT_GRAY} />
      <NoiseOverlay opacity={0.04} />

      <div style={{ /* content */ fontFamily: BRAND.FONT_FAMILY }}>
        {/* Scene content here */}
      </div>

      <IIWatermark />  {/* On every scene except title card */}
    </AbsoluteFill>
  );
};
```

### Schema Patterns

All schemas go in `src/schemas.ts`. Every field is `.optional()` so defaults work:

```typescript
export const SomeSchema = z.object({
  sectionLabel: z.string().optional(),
  headline: z.string().optional(),
  // ... all fields optional
});
```

### Combined Composition Pattern — MUST BE EDITABLE

Load `rules/composition-patterns.md` for the full reference. Summary:

Combined compositions MUST accept a flat Zod schema with prefixed props for every scene, so all text is editable from the Remotion Studio sidebar. Props use `{sceneName}_{propName}` naming to group by scene.

```tsx
import { TransitionSeries, linearTiming } from "@remotion/transitions";
import { fade } from "@remotion/transitions/fade";
import { z } from "zod";
import { M02L01v1Schema } from "../schemas";

const TRANSITION_FRAMES = 20;

export const M02L01v1: React.FC<z.infer<typeof M02L01v1Schema>> = ({
  titleCard_title = "Default Title",
  titleCard_subtitle = "Default Subtitle",
  someScene_headline = "Default Headline",
  outro_lessonNumber = "Lesson 2.2",
  outro_lessonTitle = "Next Lesson Title",
}) => {
  const { fps } = useVideoConfig();
  const sec = (s: number) => s * fps;

  return (
    <AbsoluteFill>
      <TransitionSeries>
        <TransitionSeries.Sequence durationInFrames={sec(8)}>
          <WaveformScene title={titleCard_title} subtitle={titleCard_subtitle} />
        </TransitionSeries.Sequence>
        <TransitionSeries.Transition
          presentation={fade()}
          timing={linearTiming({ durationInFrames: TRANSITION_FRAMES })}
        />
        {/* ... more scenes, each receiving props from the combined schema ... */}
        <TransitionSeries.Sequence durationInFrames={sec(10)}>
          <OutroScene lessonNumber={outro_lessonNumber} lessonTitle={outro_lessonTitle} />
        </TransitionSeries.Sequence>
      </TransitionSeries>
    </AbsoluteFill>
  );
};
```

The combined schema in `src/schemas.ts`:
```typescript
export const M02L01v1Schema = z.object({
  titleCard_title: z.string().optional(),
  titleCard_subtitle: z.string().optional(),
  someScene_headline: z.string().optional(),
  // ... all scene text props, all optional
  outro_lessonNumber: z.string().optional(),
  outro_lessonTitle: z.string().optional(),
});
```

Only include text props in the combined schema. Structural props (feature arrays, isFocus booleans) stay hardcoded in the composition file.

### Root.tsx Registration

Each scene gets its own Composition (for individual editing) plus the combined one. The combined composition MUST have `schema` and `defaultProps`:

```tsx
const FPS = 30;
const W = 1920;
const H = 1080;
const sec = (s: number) => s * FPS;

// Combined — editable with all scene props
<Composition
  id="M02L01v1"
  component={M02L01v1}
  schema={M02L01v1Schema}
  durationInFrames={sec(totalDuration)}
  fps={FPS} width={W} height={H}
  defaultProps={{
    titleCard_title: 'Default Title',
    titleCard_subtitle: 'Default Subtitle',
    // ... all scene text props
    outro_lessonNumber: 'Lesson 2.2',
    outro_lessonTitle: 'Next Lesson Title',
  }}
/>

// Individual scenes — also editable
<Composition
  id="v1-SomeScene"
  component={SomeScene}
  schema={SomeSchema}
  durationInFrames={sec(sceneDuration)}
  fps={FPS} width={W} height={H}
  defaultProps={{ /* from spec */ }}
/>
```

## Remotion 4.0 Specifics

This project uses Remotion 4.0.438. Key things to know:

- **Audio/Video imports:** Use `@remotion/media` for `<Audio>` and `<Video>` (not the older `remotion` package exports)
- **Font loading:** Use `@remotion/fonts` with `loadFont()` — fonts must specify `format: "opentype"` for .otf files
- **Premounting:** Always use `premountFor` prop on `<Sequence>` components
- **Static files:** Always use `staticFile()` for anything in `public/`
- **Time in seconds:** Write `s * fps`, not raw frame numbers
- **Type safety:** Use `type` not `interface` for component props; use `z.infer<typeof Schema>`
- **No CSS animations:** All motion via `useCurrentFrame()` + `spring()`/`interpolate()`

Load `rules/remotion-api.md` for the complete Remotion 4.0 API reference.

## Rules Directory

Load relevant rule files based on what you're building:

- **`rules/brand-system.md`** — Complete color, typography, and spacing reference. Load when creating any visual element.
- **`rules/animation-patterns.md`** — Spring configs, entrance animations, delay patterns, stagger timing. Load when animating anything.
- **`rules/component-patterns.md`** — Full scene component template, layout wrapping pattern, shared elements usage. Load when creating new components.
- **`rules/composition-patterns.md`** — TransitionSeries setup, duration calculation, Root.tsx registration. Load when building combined compositions.
- **`rules/remotion-api.md`** — Remotion 4.0 API essentials: hooks, components, imports, rendering. Load when you need API details.
- **`rules/spec-reading.md`** — How to parse spec files, map layouts to components, extract content fields. Load when reading a new spec.

## References Directory

- **`references/existing-components.md`** — Complete inventory of all scene components, layout components, and shared elements with their props and when to use each.
- **`references/bundled-assets.md`** — Inventory of all brand assets in the project (logos, fonts, covers, icons).

## Common Mistakes to Avoid

1. **Creating components that already exist.** Check the inventory first. `ThreePillarsScene` with different content is still `ThreePillarsScene` — just pass different props.
2. **Making combined compositions non-editable.** Combined compositions MUST have a flat Zod schema with `{sceneName}_{propName}` prefixed props, registered with `schema` + `defaultProps` in Root.tsx. Never create a combined composition without this — it makes the full timeline uneditable in Studio.
3. **Using GRAPHITE for backgrounds.** GRAPHITE is for text and graphic elements only. All backgrounds are OFF_WHITE.
4. **Forgetting NoiseOverlay or IIWatermark.** Every scene needs `<NoiseOverlay opacity={0.04} />`. Every scene except the title card needs `<IIWatermark />`.
5. **Using CSS transitions.** All animation must use `useCurrentFrame()` with `spring()` or `interpolate()`. CSS transitions won't render correctly in Remotion.
6. **Hardcoding frame numbers.** Use `s * fps` for time calculations, never raw frame counts.
7. **Missing `fontFamily: BRAND.FONT_FAMILY`** on content containers.
8. **Using `interface` instead of `type`** for component props with Zod.
9. **Not making schema fields optional.** All fields should be `.optional()` with defaults in the component destructuring.
10. **V2 scenes must have ENTER_DELAY and exitOpacity.** Every v2 scene needs `const ENTER_DELAY = 35` and the `exitOpacity` interpolation. Without these, content overlaps during transitions.
11. **V2 transitions are 45 frames, not 20.** Using `TRANSITION_FRAMES = 20` with v2 scenes causes jarring cuts because the exit/entrance timing is designed for 45-frame crossfades.
12. **Don't dim the II icon on Hero scenes.** Never use `opacity: 0.4` or similar on the ElevenLabs icon in title/welcome/outro scenes. Full opacity always.
13. **No backdrop-filter on dense grids.** When 4+ BrandedCards are close together, use `variant="darkflat"` (no blur). Using `darkglass` or other blur variants in tight layouts causes rendering distortion artifacts.
14. **Cards should NOT stretch.** Never put `flex: 1` on BrandedCard styles — cards should hug their content. Use `alignItems: "center"` on the parent container to center cards vertically.
15. **All icons white on Hero scenes.** Use `brand-assets/icons/white/` variants. For product icons, apply `filter: "brightness(0) invert(1)"`. Inline SVGs should use `stroke="#FFFFFF"`, not `stroke="#1E1916"`.
16. **Don't hardcode card text colors.** Use `getCardColors(variant)` from BrandedCard to get the correct `title`, `description`, `label`, `divider`, and `decorativeNumber` colors. Never hardcode `#151515` or `#666666` on cards.

## Project Context

### ElevenLabs University
- 9 training modules + separate certification (NOT 10 modules)
- Credential: "ElevenLabs Certified ElevenAgent Builder"
- Voice-first but omnichannel
- "ElevenLabs" is one word, capital E and L

### Module Structure
1. The Platform — ElevenLabs & the AI Voice Landscape
2. Voice & AI Foundations — How the Technology Works
3. Your First Agent — Create, Configure & Test
4. Prompt Engineering — LLM Configuration & Conversation Design
5. Knowledge & Tools — Connect Your Agent to the World
6. Advanced Architecture — Workflows, API & Multi-Agent Systems
7. Deployment — Phone, Web, Mobile & Enterprise Channels
8. Testing & Evaluation — Scenarios, Experiments & CI/CD
9. Production Operations — Analytics, Cost, Privacy & Scale
- Certification — Build an agent end-to-end (separate, paywalled)
