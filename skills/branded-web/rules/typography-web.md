# Typography for Web

ElevenLabs typography system implemented with CSS.

## @font-face Declarations

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

## Font Stack

```css
font-family: 'KMR Waldenburg', 'Inter', 'Helvetica Neue', system-ui, sans-serif;
```

When KMR Waldenburg is unavailable, Inter is the best fallback -- it shares low stroke contrast and a geometric-humanist feel.

## Typographic Scale

From the official brand guidelines:

| Use | Weight | Size | Line-Height | Tracking | CSS |
|-----|--------|------|-------------|----------|-----|
| Hero headline | Book (300) | 80px | 100% | 0% | `font-weight: 300; font-size: 5rem; line-height: 1; letter-spacing: 0;` |
| Large headline | Normal (400) | 58px | 100% | -2% | `font-weight: 400; font-size: 3.625rem; line-height: 1; letter-spacing: -0.02em;` |
| Body / subhead | Book (300) | 27px | 150% | 0% | `font-weight: 300; font-size: 1.6875rem; line-height: 1.5; letter-spacing: 0;` |
| Body small | Book (300) | 18px | 140% | 0% | `font-weight: 300; font-size: 1.125rem; line-height: 1.4; letter-spacing: 0;` |
| Labels / caps | 600 | 16px | 100% | 0.1em | `font-weight: 600; font-size: 1rem; text-transform: uppercase; letter-spacing: 0.1em;` |

## Weight Usage

Only two weights matter in the brand hierarchy:

- **Book (300)** -- the lighter weight. Used for large headlines (refined, elegant look) and body text.
- **Normal (400)** -- the heavier weight. Used for secondary headlines and emphasis.

The key principle is **typographic balance**: lighter weight for large text gives refinement; heavier weight for smaller emphasis text adds confidence.

## Responsive Typography

```css
.hero-headline {
  font-family: 'KMR Waldenburg', 'Inter', system-ui, sans-serif;
  font-weight: 300;
  line-height: 1;
  letter-spacing: 0;
  font-size: clamp(2.5rem, 5vw, 5rem); /* 40px to 80px */
}

.section-headline {
  font-family: 'KMR Waldenburg', 'Inter', system-ui, sans-serif;
  font-weight: 400;
  line-height: 1;
  letter-spacing: -0.02em;
  font-size: clamp(2rem, 4vw, 3.625rem); /* 32px to 58px */
}

.body-text {
  font-family: 'KMR Waldenburg', 'Inter', system-ui, sans-serif;
  font-weight: 300;
  line-height: 1.5;
  font-size: clamp(1rem, 1.5vw, 1.6875rem); /* 16px to 27px */
}

.label-text {
  font-family: 'KMR Waldenburg', 'Inter', system-ui, sans-serif;
  font-weight: 600;
  font-size: 1rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}
```
