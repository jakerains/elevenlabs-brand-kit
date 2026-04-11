---
name: branded-web
description: "Build ElevenLabs-branded web experiences -- landing pages, marketing sites, web apps, dashboards, and interactive content. Use when building any web UI that should look like ElevenLabs: HTML pages, React components, Next.js apps, Tailwind projects, or shadcn/ui interfaces. Trigger on 'build a branded page', 'make it look like ElevenLabs', 'ElevenLabs landing page', 'branded website', 'vibe code', 'web project', or any web development task that needs brand compliance."
---

# ElevenLabs Brand Kit -- Branded Web

Build web experiences that look and feel like ElevenLabs. This skill translates the ElevenLabs brand system into web-native CSS, HTML, React, Tailwind, and shadcn/ui patterns.

**Before you start:** Make sure brand assets are installed. Check for `public/brand-assets/` in the project. If missing, run `/elevenlabs-brand-kit:asset-setup` first.

---

## Two Visual Modes

Every ElevenLabs-branded page uses one of two visual modes. Most pages mix both.

### Hero Mode (dark, atmospheric)

Full-bleed gradient background image with white text and glassmorphism cards. Use for: landing hero sections, feature announcements, dramatic emphasis, opening/closing sections.

```css
.hero-section {
  position: relative;
  overflow: hidden;
  color: #ffffff;
}

.hero-section .bg {
  position: absolute;
  inset: 0;
  background-image: url('/brand-assets/backgrounds/gradient/Background0.jpg');
  background-size: cover;
  background-position: center;
  filter: blur(25px);
  transform: scale(1.1); /* prevent blur edge bleed */
}

.hero-section .bg::after {
  content: "";
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.12); /* dark tint */
}
```

### Content Mode (light, clean)

Light background with dark text and solid cream cards. Use for: instructional content, feature breakdowns, documentation sections, most page body content.

```css
.content-section {
  background-color: #fafafa; /* OFF_WHITE */
  color: #1e1916; /* GRAPHITE */
}

.content-card {
  background-color: #f5f3f1; /* CREAM */
  border: 1px solid #e0dedc; /* LIGHT_GRAY */
  border-radius: 1rem;
  padding: 2rem;
}
```

---

## Brand Color Tokens

Set these as CSS custom properties on `:root`. Load the rule file `rules/css-tokens.md` for the full token reference including shadcn semantic mappings.

```css
:root {
  --graphite: #1e1916;    /* Primary text, headings */
  --off-white: #fafafa;   /* Page backgrounds (Content mode) */
  --cream: #f5f3f1;       /* Card backgrounds, accent areas */
  --light-gray: #e0dedc;  /* Borders, dividers */
  --mid-gray: #999999;    /* Secondary text, labels */
  --dark-gray: #555555;   /* Body text */
  --near-black: #151515;  /* Hover states, dark fills */
}
```

**Key rules:**
- GRAPHITE is for **text only** -- never use it as a background fill
- Color comes from **imagery**, not from applied UI palettes
- Gray shades should NOT be mixed with color accents

---

## Font Loading

Load the rule file `rules/typography-web.md` for the full typographic scale.

```css
@font-face {
  font-family: 'KMR Waldenburg';
  src: url('/brand-assets/fonts/KMR-Waldenburg-Buch.otf') format('opentype');
  font-weight: 300;
  font-display: swap;
}

@font-face {
  font-family: 'KMR Waldenburg';
  src: url('/brand-assets/fonts/KMR-Waldenburg-Normal.otf') format('opentype');
  font-weight: 400;
  font-display: swap;
}

@font-face {
  font-family: 'KMR Waldenburg';
  src: url('/brand-assets/fonts/KMR-Waldenburg-Halbfett.otf') format('opentype');
  font-weight: 600;
  font-display: swap;
}

@font-face {
  font-family: 'KMR Waldenburg';
  src: url('/brand-assets/fonts/KMR-Waldenburg-Fett.otf') format('opentype');
  font-weight: 700;
  font-display: swap;
}
```

**Font stack:** `'KMR Waldenburg', 'Inter', 'Helvetica Neue', system-ui, sans-serif`

**Two weights matter most:** Book (300) for large headlines and body, Normal (400) for emphasis. The brand uses only these two in its official hierarchy.

---

## Noise Texture Overlay

**Required on all branded content.** Apply a subtle noise overlay to every section.

```css
.noise-overlay {
  position: relative;
}

.noise-overlay::after {
  content: "";
  position: absolute;
  inset: 0;
  background-image: url("/brand-assets/backgrounds/noise-texture.jpg");
  background-size: 200px;
  opacity: 0.03;
  mix-blend-mode: overlay;
  pointer-events: none;
  z-index: 1;
}
```

**Alternative -- layered background shorthand:**

```css
/* Light card with noise */
.branded-card-light {
  background:
    url("/brand-assets/backgrounds/noise-texture.jpg") repeat 0 0 / 200px,
    linear-gradient(180deg, #ffffff 0%, #fafafa 100%);
  background-blend-mode: overlay, normal;
}

/* Dark card with noise */
.branded-card-dark {
  background:
    url("/brand-assets/backgrounds/noise-texture.jpg") repeat 0 0 / 200px,
    linear-gradient(180deg, #1e1916 0%, #151515 100%);
  background-blend-mode: overlay, normal;
}
```

---

## BrandedCard Variants

Load the rule file `rules/card-variants.md` for all 8 variants with full CSS.

The most common variants:

**`darkflat` (default for Hero mode):**
```css
.card-darkflat {
  background: rgba(0, 0, 0, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 14px;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.12);
  color: #ffffff;
}
```

**`glass` (frosted glass for Hero mode):**
```css
.card-glass {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(40px);
  -webkit-backdrop-filter: blur(40px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 14px;
  color: #ffffff;
}
```

**Content mode card (solid cream):**
```css
.card-content {
  background-color: #f5f3f1; /* CREAM */
  border: 1px solid #e0dedc; /* LIGHT_GRAY */
  border-radius: 1rem;
}
```

**Important:** Use `darkflat` (no `backdrop-filter`) for dense grids of 4+ cards to avoid blur rendering artifacts.

---

## Background Treatment

Load the rule file `rules/backgrounds.md` for advanced techniques (complex blur, Chladni masks).

**Hero background with blur:**
```html
<section class="hero-section noise-overlay">
  <div class="hero-bg"></div>
  <div class="hero-content">
    <!-- White text content here -->
  </div>
</section>
```

**Background image selection:**
- `backgrounds/gradient/` -- 16 atmospheric gradients (Background0-15.jpg). Best for general Hero sections.
- `backgrounds/agents/` -- 9 green/teal/blue variants. Use for agent-related content.
- `backgrounds/chladni-closeup/` -- 15 nature photography bases. Need blur treatment.
- `backgrounds/general/` -- 7 blue/cyan gradients + Chladni patterns.

Browse all backgrounds at `public/brand-assets/backgrounds/catalog.html`.

---

## Icons

Three color variants -- choose based on background:

| Background | Use variant | Path |
|-----------|-------------|------|
| Dark / gradient (Hero mode) | `white/` | `/brand-assets/icons/white/` |
| Light (Content mode) | `black/` | `/brand-assets/icons/black/` |
| On cream cards | `cream/` | `/brand-assets/icons/cream/` |

**Product icons on dark backgrounds** need a CSS filter:
```css
.product-icon-on-dark {
  filter: brightness(0) invert(1);
}
```

Browse all 130 icons at `public/brand-assets/icons/catalog.html`.

---

## Voice Orb Compositing

Voice orbs ship on black backgrounds. Use CSS blend mode to knock out the black:

```css
.voice-orb {
  mix-blend-mode: screen;
}
```

```html
<div style="position: relative; background: #1e1916;">
  <img
    src="/brand-assets/voice-orbs/orb-teal-on-black.jpg"
    alt=""
    style="mix-blend-mode: screen; width: 200px;"
  />
</div>
```

8 colors available: teal, purple-blue, pink, coral, green, gold, hotpink, lavender.

Load the rule file `rules/voice-orbs-web.md` for Three.js/R3F usage patterns.

---

## Tailwind CSS Integration

Load the rule file `rules/tailwind-setup.md` for the complete `@theme` configuration.

Quick setup -- add to your `globals.css`:

```css
@theme inline {
  --color-graphite: var(--graphite);
  --color-off-white: var(--off-white);
  --color-cream: var(--cream);
  --color-light-gray: var(--light-gray);
  --color-mid-gray: var(--mid-gray);
  --color-dark-gray: var(--dark-gray);
  --color-near-black: var(--near-black);
}
```

This enables: `bg-cream`, `text-graphite`, `border-light-gray`, etc.

---

## shadcn/ui Integration

Load the rule file `rules/shadcn-theming.md` for the full semantic token mapping.

Map shadcn tokens to ElevenLabs brand:

```css
:root {
  --background: #fafafa;     /* OFF_WHITE */
  --foreground: #1e1916;     /* GRAPHITE */
  --card: #ffffff;
  --card-foreground: #1e1916;
  --primary: #1e1916;        /* GRAPHITE */
  --primary-foreground: #fafafa;
  --secondary: #f5f3f1;      /* CREAM */
  --secondary-foreground: #1e1916;
  --muted: #f5f3f1;          /* CREAM */
  --muted-foreground: #999999; /* MID_GRAY */
  --accent: #f5f3f1;         /* CREAM */
  --accent-foreground: #1e1916;
  --border: #e0dedc;         /* LIGHT_GRAY */
  --input: #e0dedc;
  --ring: #1e1916;
  --radius: 0.625rem;
}
```

---

## Layout Principles

**Standard layout formula:**
1. Logo/wordmark in top-left corner (small, with safespace = logo height on all sides)
2. Large headline text with generous whitespace
3. Imagery or graphic elements on the right or as background
4. The brand breathes -- generous `padding`, `max-w-7xl` containers, large `gap`

**Split compositions:**
Many ElevenLabs layouts use a clean half (text, logo, light background) paired with a visual half (blurred imagery, Chladni patterns, color). This creates strong contrast between clarity and atmosphere.

```html
<section style="display: grid; grid-template-columns: 1fr 1fr; min-height: 100vh;">
  <div class="content-section" style="padding: 4rem; display: flex; flex-direction: column; justify-content: center;">
    <!-- Clean text side -->
  </div>
  <div class="hero-section">
    <!-- Visual/gradient side -->
  </div>
</section>
```

**Dark and light both work.** Dark backgrounds use white text and white logo. Light backgrounds use GRAPHITE text and black logo.

---

## Locating Brand Assets

Brand assets may be stored centrally or in the project. Always check in this order:

1. **Check config:** Read `~/.elevenlabs-kit/config.json`
2. **If `assetLocation` is `"central"`:** Assets are symlinked to `public/brand-assets/`
3. **If `"project-local"` or no config:** Assets are directly in `public/brand-assets/`
4. **If not found:** Run `/elevenlabs-brand-kit:asset-setup`

**Browse the catalog:** Open `public/brand-assets/index.html` in a browser to see every background, icon, voice orb, and color token with one-click copy buttons.
