# shadcn/ui Theming for ElevenLabs

How to configure shadcn/ui components with ElevenLabs brand tokens.

## Token Mapping

shadcn uses semantic CSS variables that map to its component library. Here's how they map to ElevenLabs:

| shadcn Token | ElevenLabs Value | Brand Token |
|-------------|-----------------|-------------|
| `--background` | `#fafafa` | OFF_WHITE |
| `--foreground` | `#1e1916` | GRAPHITE |
| `--card` | `#ffffff` | WHITE |
| `--card-foreground` | `#1e1916` | GRAPHITE |
| `--popover` | `#ffffff` | WHITE |
| `--popover-foreground` | `#1e1916` | GRAPHITE |
| `--primary` | `#1e1916` | GRAPHITE |
| `--primary-foreground` | `#fafafa` | OFF_WHITE |
| `--secondary` | `#f5f3f1` | CREAM |
| `--secondary-foreground` | `#1e1916` | GRAPHITE |
| `--muted` | `#f5f3f1` | CREAM |
| `--muted-foreground` | `#999999` | MID_GRAY |
| `--accent` | `#f5f3f1` | CREAM |
| `--accent-foreground` | `#1e1916` | GRAPHITE |
| `--destructive` | `#dc2626` | (standard red) |
| `--destructive-foreground` | `#fafafa` | OFF_WHITE |
| `--border` | `#e0dedc` | LIGHT_GRAY |
| `--input` | `#e0dedc` | LIGHT_GRAY |
| `--ring` | `#1e1916` | GRAPHITE |
| `--radius` | `0.625rem` | 10px |

## Radius Scale

```css
:root {
  --radius: 0.625rem;  /* 10px base */
}

@theme inline {
  --radius-sm: calc(var(--radius) - 4px);   /* 6px */
  --radius-md: calc(var(--radius) - 2px);   /* 8px */
  --radius-lg: var(--radius);               /* 10px */
  --radius-xl: calc(var(--radius) + 4px);   /* 14px */
}
```

## Component Style Notes

- **Buttons:** Primary buttons are GRAPHITE background with OFF_WHITE text. Secondary buttons are CREAM with GRAPHITE text.
- **Cards:** White background with LIGHT_GRAY border. Or CREAM for muted/secondary cards.
- **Inputs:** LIGHT_GRAY borders, GRAPHITE text, MID_GRAY placeholder.
- **Focus rings:** GRAPHITE ring color matches brand identity.
- **Destructive:** Standard red (#dc2626) -- the only non-monochrome UI color.

## cn() Utility

Use the standard `clsx` + `tailwind-merge` pattern:

```typescript
import { clsx, type ClassValue } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}
```
