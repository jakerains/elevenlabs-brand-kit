# BrandedCard CSS Variants

All 8 card variants from the ElevenLabs design system, translated to pure CSS.

## Hero Mode Cards (on gradient/dark backgrounds)

### `darkflat` (DEFAULT for Hero)

No blur -- safe for dense grids of 4+ cards.

```css
.card-darkflat {
  background: rgba(0, 0, 0, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 14px;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.12);
  padding: 2rem;
  /* Text colors */
  color: #ffffff;
}
.card-darkflat .card-title { color: #ffffff; }
.card-darkflat .card-description { color: rgba(255, 255, 255, 0.65); }
```

### `darkglass`

Same as darkflat + backdrop blur. Use for 1-3 cards only.

```css
.card-darkglass {
  background: rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  border-radius: 14px;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.12);
  padding: 2rem;
  color: #ffffff;
}
.card-darkglass .card-title { color: #ffffff; }
.card-darkglass .card-description { color: rgba(255, 255, 255, 0.65); }
```

### `glass`

Frosted glass -- more transparent, higher blur.

```css
.card-glass {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(40px);
  -webkit-backdrop-filter: blur(40px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 14px;
  padding: 2rem;
  color: #ffffff;
}
.card-glass .card-title { color: #ffffff; }
.card-glass .card-description { color: rgba(255, 255, 255, 0.7); }
```

### `baseline`

Frosted cream -- light text background on dark. Good for readability.

```css
.card-baseline {
  background: rgba(245, 243, 241, 0.88);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  border: 1px solid rgba(224, 222, 220, 0.5);
  border-radius: 14px;
  padding: 2rem;
  color: #1e1916;
}
.card-baseline .card-title { color: #1e1916; }
.card-baseline .card-description { color: #555555; }
```

### `outline`

Transparent with border only. Minimal, elegant.

```css
.card-outline {
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.25);
  border-radius: 14px;
  padding: 2rem;
  color: #ffffff;
}
.card-outline .card-title { color: #ffffff; }
.card-outline .card-description { color: rgba(255, 255, 255, 0.65); }
```

### `pill`

Rounded, subtle blur. Good for tags or compact items.

```css
.card-pill {
  background: rgba(255, 255, 255, 0.12);
  backdrop-filter: blur(30px);
  -webkit-backdrop-filter: blur(30px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 24px;
  padding: 1rem 1.5rem;
  color: #ffffff;
}
.card-pill .card-title { color: #ffffff; }
.card-pill .card-description { color: rgba(255, 255, 255, 0.7); }
```

### `acrylic`

Semi-transparent cream overlay with light blur.

```css
.card-acrylic {
  background: rgba(245, 243, 241, 0.45);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(224, 222, 220, 0.4);
  border-radius: 14px;
  padding: 2rem;
  color: #1e1916;
}
.card-acrylic .card-title { color: #1e1916; }
.card-acrylic .card-description { color: #555555; }
```

### `gradientborder`

Gradient stroke with dark fill.

```css
.card-gradientborder {
  background: rgba(0, 0, 0, 0.15);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-radius: 14px;
  padding: 2rem;
  position: relative;
  color: #ffffff;
}
/* Gradient border via pseudo-element */
.card-gradientborder::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 14px;
  padding: 1px;
  background: linear-gradient(135deg, rgba(255,255,255,0.3), rgba(255,255,255,0.05));
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
.card-gradientborder .card-title { color: #ffffff; }
.card-gradientborder .card-description { color: rgba(255, 255, 255, 0.65); }
```

## Content Mode Card (on light backgrounds)

```css
.card-content {
  background-color: #f5f3f1; /* CREAM */
  border: 1px solid #e0dedc; /* LIGHT_GRAY */
  border-radius: 1rem;
  padding: 2rem;
  color: #1e1916;
}
.card-content .card-title { color: #1e1916; }
.card-content .card-description { color: #555555; }
```

## Variant Selection Guide

| Scenario | Variant |
|----------|---------|
| Grid of 4+ cards on Hero bg | `darkflat` (no blur artifacts) |
| 1-3 featured cards on Hero bg | `darkglass` or `glass` |
| Readable text overlay on Hero bg | `baseline` |
| Minimal border-only treatment | `outline` |
| Tags, pills, compact items | `pill` |
| Semi-transparent on Hero bg | `acrylic` |
| Premium/featured single card | `gradientborder` |
| Cards on light Content bg | `card-content` |
