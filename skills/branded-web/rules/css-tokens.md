# CSS Token Reference

Complete CSS custom property definitions for ElevenLabs brand theming.

## Brand Tokens

```css
:root {
  /* ─── ElevenLabs Brand Tokens ─── */
  --graphite: #1e1916;    /* Primary text, headings, active elements */
  --off-white: #fafafa;   /* Page backgrounds (Content mode) */
  --cream: #f5f3f1;       /* Card backgrounds, accent areas, warm light bg */
  --light-gray: #e0dedc;  /* Borders, dividers, subtle separators */
  --mid-gray: #999999;    /* Secondary text, labels, disabled states, hints */
  --dark-gray: #555555;   /* Body text (secondary importance) */
  --near-black: #151515;  /* Hover states, dark fills, icon fill on cream */
  --white: #ffffff;       /* Cards, overlays, Hero mode text */
  --black: #000000;       /* Pure black (rare) */
}
```

## shadcn/ui Semantic Tokens

Map shadcn's semantic token system to ElevenLabs brand values:

```css
:root {
  /* shadcn semantic tokens -> ElevenLabs monochrome */
  --background: #fafafa;          /* OFF_WHITE */
  --foreground: #1e1916;          /* GRAPHITE */
  --card: #ffffff;
  --card-foreground: #1e1916;
  --popover: #ffffff;
  --popover-foreground: #1e1916;
  --primary: #1e1916;             /* GRAPHITE */
  --primary-foreground: #fafafa;
  --secondary: #f5f3f1;           /* CREAM */
  --secondary-foreground: #1e1916;
  --muted: #f5f3f1;               /* CREAM */
  --muted-foreground: #999999;    /* MID_GRAY */
  --accent: #f5f3f1;              /* CREAM */
  --accent-foreground: #1e1916;
  --destructive: #dc2626;
  --destructive-foreground: #fafafa;
  --border: #e0dedc;              /* LIGHT_GRAY */
  --input: #e0dedc;               /* LIGHT_GRAY */
  --ring: #1e1916;                /* GRAPHITE */
  --radius: 0.625rem;             /* 10px default radius */
}
```

## Usage Rules

- **GRAPHITE (#1e1916)** -- text and elements ONLY, never as a background fill
- **OFF_WHITE (#fafafa)** -- Content mode page backgrounds
- **CREAM (#f5f3f1)** -- card fills, accent areas, secondary backgrounds
- **Color comes from imagery** -- the brand palette is monochrome; color enters through background images, voice orbs, and atmospheric photography
- **No gray + color mixing** -- gray shades should not appear alongside color accents in the same composition
