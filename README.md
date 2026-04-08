<p align="center">
  <img src="brand-assets/logos/Logo-black.png" alt="ElevenLabs" width="300" />
</p>

# ElevenLabs Academy Plugin for Claude Code

A Claude Code plugin that provides the complete toolkit for producing ElevenLabs Academy certification videos using Remotion.

## What's Included

| Skill | Command | What It Does |
|-------|---------|-------------|
| **Asset Setup** | `/elevenlabs-academy:asset-setup` | Download brand assets, bootstrap a Remotion project, configure central or project-local storage |
| **Lesson Builder** | `/elevenlabs-academy:lesson-builder` | Full lesson production — instructional design, VO scripts, Remotion specs, Arcade specs, text companions |
| **Remotion Spec Builder** | `/elevenlabs-academy:remotion-spec` | Draft scene-by-scene video blueprints with layouts, modes, backgrounds, and content |
| **Remotion Builder** | `/elevenlabs-academy:remotion-builder` | Generate React/TypeScript Remotion compositions from spec files |
| **Remotion Best Practices** | `/elevenlabs-academy:remotion-best-practices` | Remotion API reference — animations, transitions, audio, video, fonts, 3D |
| **Brand** | `/elevenlabs-academy:brand` | Enforce ElevenLabs brand guidelines on any content |
| **Project Context** | `/elevenlabs-academy:project-context` | Curriculum structure, module info, credential details |

### When to use which

- **"Build out lesson M3-L2"** → **Lesson Builder** — produces all deliverables (VO, specs, text companion) with full instructional design rigor
- **"Spec out the video for M3-L2"** → **Remotion Spec Builder** — just the video blueprint (scene layouts, modes, durations)
- **"Implement this spec"** → **Remotion Builder** — generates the actual React code from a spec file

## Installation

### From GitHub (recommended)

```bash
claude /plugin install https://github.com/jakerains/elevenlabs-academy-plugin
```

### Local development

```bash
git clone https://github.com/jakerains/elevenlabs-academy-plugin.git
claude --plugin-dir ./elevenlabs-academy-plugin
```

## Quick Start

1. Install the plugin
2. Run `/elevenlabs-academy:asset-setup` to bootstrap your Remotion project with brand assets
3. Draft a spec with `/elevenlabs-academy:remotion-spec`
4. Build it with `/elevenlabs-academy:remotion-builder`

## Brand Assets

Brand assets (backgrounds, icons, voice orbs, fonts, logos — ~278MB optimized) are distributed via [GitHub Releases](https://github.com/jakerains/elevenlabs-academy-plugin/releases). The `asset-setup` skill downloads them and supports both project-local and central (`~/.elevenlabs-academy/`) storage.

## V2 Design System

The plugin includes the full v2 visual system:

- **Hero mode** — Gradient backgrounds, frosted BrandedCards, white text
- **Content mode** — OFF_WHITE backgrounds, CREAM cards, GRAPHITE text
- **Hybrid mode** — White left / gradient right split layouts
- **Animation timing** — ENTER_DELAY=35, exitOpacity fade, TRANSITION_FRAMES=45
- **12 v2 scene components** + 2 shared components (GradientBackground, BrandedCard)

## Project Structure

```
elevenlabs-academy-plugin/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── skills/
│   ├── asset-setup/         # Project bootstrap + asset download
│   ├── remotion-builder/    # Code generation from specs
│   │   ├── rules/           # Brand system, animations, components, compositions
│   │   └── references/      # Component inventory, bundled assets
│   ├── remotion-spec/       # Spec drafting
│   │   ├── rules/           # Remotion API reference files
│   │   └── references/      # Brand guidelines, asset inventory
│   ├── remotion-best-practices/  # Remotion API patterns
│   │   └── rules/           # Animations, timing, transitions, audio, 3D, etc.
│   ├── lesson-builder/      # Full lesson production (instructional design + all deliverables)
│   ├── brand/               # Brand guideline enforcement
│   └── project-context/     # Curriculum and project context
└── README.md
```

## License

For ElevenLabs internal use only. This plugin is for authorized use by ElevenLabs employees. Brand assets, guidelines, fonts, and curriculum content are proprietary to ElevenLabs. No unauthorized use, reproduction, or distribution is permitted.
