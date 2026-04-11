# Tailwind CSS v4 Setup for ElevenLabs Brand

Complete Tailwind configuration for ElevenLabs-branded projects.

## Full globals.css Setup

```css
@import "tailwindcss";

/* ─── ElevenLabs Brand Tokens ─── */
:root {
  --graphite: #1e1916;
  --off-white: #fafafa;
  --cream: #f5f3f1;
  --light-gray: #e0dedc;
  --mid-gray: #999999;
  --dark-gray: #555555;
  --near-black: #151515;

  /* shadcn semantic tokens -> ElevenLabs monochrome */
  --background: #fafafa;
  --foreground: #1e1916;
  --card: #ffffff;
  --card-foreground: #1e1916;
  --popover: #ffffff;
  --popover-foreground: #1e1916;
  --primary: #1e1916;
  --primary-foreground: #fafafa;
  --secondary: #f5f3f1;
  --secondary-foreground: #1e1916;
  --muted: #f5f3f1;
  --muted-foreground: #999999;
  --accent: #f5f3f1;
  --accent-foreground: #1e1916;
  --destructive: #dc2626;
  --destructive-foreground: #fafafa;
  --border: #e0dedc;
  --input: #e0dedc;
  --ring: #1e1916;
  --radius: 0.625rem;
}

@theme inline {
  --color-graphite: var(--graphite);
  --color-off-white: var(--off-white);
  --color-cream: var(--cream);
  --color-light-gray: var(--light-gray);
  --color-mid-gray: var(--mid-gray);
  --color-dark-gray: var(--dark-gray);
  --color-near-black: var(--near-black);

  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-popover: var(--popover);
  --color-popover-foreground: var(--popover-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-destructive: var(--destructive);
  --color-destructive-foreground: var(--destructive-foreground);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);

  --font-sans: 'KMR Waldenburg', 'Inter', 'Helvetica Neue', system-ui, sans-serif;
  --radius-sm: calc(var(--radius) - 4px);
  --radius-md: calc(var(--radius) - 2px);
  --radius-lg: var(--radius);
  --radius-xl: calc(var(--radius) + 4px);
}

body {
  background: var(--off-white);
  color: var(--graphite);
  font-family: var(--font-sans);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

## Resulting Utility Classes

After configuration, these utilities work automatically:

| Class | Value | Use |
|-------|-------|-----|
| `bg-off-white` | `#fafafa` | Content mode page background |
| `bg-cream` | `#f5f3f1` | Card backgrounds |
| `bg-near-black` | `#151515` | Dark backgrounds |
| `text-graphite` | `#1e1916` | Primary text |
| `text-mid-gray` | `#999999` | Labels, secondary text |
| `text-dark-gray` | `#555555` | Body text |
| `border-light-gray` | `#e0dedc` | Dividers, card borders |
| `bg-primary` | `#1e1916` | Buttons, CTAs |
| `text-primary-foreground` | `#fafafa` | Button text |
| `bg-secondary` | `#f5f3f1` | Secondary buttons |
| `bg-muted` | `#f5f3f1` | Muted backgrounds |
| `text-muted-foreground` | `#999999` | Muted text |

## Noise Overlay Utility

Add this to your CSS for a reusable noise overlay class:

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
