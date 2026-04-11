# Background Treatments for Web

How to apply ElevenLabs background treatments in CSS.

## Simple Blur (Hero Mode Background)

The standard Hero mode treatment: blur the background image + add a dark tint.

```css
.hero-bg-container {
  position: relative;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  background-image: url('/brand-assets/backgrounds/gradient/Background0.jpg');
  background-size: cover;
  background-position: center;
  filter: blur(25px);
  transform: scale(1.1); /* prevent blur edge bleed */
}

.hero-bg::after {
  content: "";
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.12); /* dark tint */
}
```

**Alternative -- using backdrop-filter on content layer:**

```css
.hero-bg-raw {
  position: absolute;
  inset: 0;
  background-image: url('/brand-assets/backgrounds/gradient/Background0.jpg');
  background-size: cover;
}

.hero-content-layer {
  position: relative;
  backdrop-filter: blur(25px);
  -webkit-backdrop-filter: blur(25px);
  background: rgba(0, 0, 0, 0.12);
}
```

## Noise Overlay

**Required on ALL branded content.** Two approaches:

### Pseudo-element (most flexible)

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

### Layered background shorthand

```css
/* Light card with baked-in noise */
.card-with-noise-light {
  background:
    url("/brand-assets/backgrounds/noise-texture.jpg") repeat 0 0 / 200px,
    linear-gradient(180deg, #ffffff 0%, #fafafa 100%);
  background-blend-mode: overlay, normal;
}

/* Dark card with baked-in noise */
.card-with-noise-dark {
  background:
    url("/brand-assets/backgrounds/noise-texture.jpg") repeat 0 0 / 200px,
    linear-gradient(180deg, #1e1916 0%, #151515 100%);
  background-blend-mode: overlay, normal;
}
```

## Complex Blur (Signature Technique)

Two blur layers -- the base image stays unedited. One layer is heavily blurred, a second layer uses a Chladni shape mask to reveal parts of the image through the blur.

```css
.complex-blur-container {
  position: relative;
  overflow: hidden;
}

/* Base image -- unedited */
.complex-blur-base {
  position: absolute;
  inset: 0;
  background-image: url('/brand-assets/backgrounds/chladni-closeup/closeup-01-red-rock-blue-sky.jpg');
  background-size: cover;
}

/* Heavy blur layer */
.complex-blur-heavy {
  position: absolute;
  inset: 0;
  background: inherit;
  filter: blur(80px);
}

/* Reveal layer -- shape mask shows base through blur */
.complex-blur-reveal {
  position: absolute;
  inset: 0;
  background: inherit;
  opacity: 0.1;
  /* Apply Chladni shape as clip-path or mask */
  mask-image: url('/path/to/chladni-shape.svg');
  mask-size: 60%;
  mask-position: center;
  mask-repeat: no-repeat;
}
```

## Chladni Patterns as Background Decoration

Subtle Chladni grid patterns at very low opacity:

```css
.chladni-accent {
  position: relative;
}

.chladni-accent::before {
  content: "";
  position: absolute;
  inset: 0;
  background-image: url('/brand-assets/backgrounds/general/image38-chladni-pattern.jpg');
  background-size: 400px;
  background-repeat: repeat;
  opacity: 0.03;
  mix-blend-mode: multiply;
  pointer-events: none;
}
```

## Background Selection Guide

| Directory | Count | Palette | Best for |
|-----------|-------|---------|----------|
| `gradient/` | 16 | Atmospheric gradients | General Hero sections, landing pages |
| `agents/` | 9 | Green/teal/blue | Agent-related content |
| `chladni-closeup/` | 15 | Nature photography | Need blur treatment -- dramatic Hero sections |
| `general/` | 7 | Blue/cyan + Chladni patterns | Technical Hero sections |
| `creative/` | 1 | Coral-sunset | Warm/creative content |

## Blur Rules

- Avoid tight crops that turn images into formless color patches -- keep some structure
- Don't mix too many colors in one crop
- Don't over-blur to the point colors become muddy
- Background images always get blur + noise + tint
