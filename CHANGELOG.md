# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - April 10, 2026

### Added
- New `branded-web` skill — guidance for building ElevenLabs-branded web experiences (HTML, CSS, React, Tailwind, shadcn/ui)
- 7 web-specific rule files: css-tokens, tailwind-setup, shadcn-theming, card-variants, backgrounds, typography-web, voice-orbs-web

### Changed
- **BREAKING:** Rebrand from "ElevenLabs Remotion Kit" to "ElevenLabs Brand Kit"
- **BREAKING:** Plugin name changed from `elevenlabs-remotion-kit` to `elevenlabs-brand-kit` — all skill commands now use `/elevenlabs-brand-kit:` prefix
- README restructured with brand-first positioning; Remotion skills presented as one workflow
- brand-assets/CLAUDE.md updated to be framework-agnostic with web usage examples
- brand-assets/index.html catalog updated: "Remotion Catalog" → "Brand Catalog", copy payloads now show both web and Remotion paths
- asset-setup SKILL.md updated with web-first guidance and new plugin name
- Brand skill: clarified Core Brand vs. Monochrome mode — educational/training content uses Core Brand (not Monochrome)

### Optimized
- Brand asset images resized to max 1920px, JPEG quality 85, 72 DPI — archive reduced from ~278MB to ~75MB
- Removed legacy `images/` directory (superseded by `backgrounds/gradient/`)
- `seamless-texture.jpg` reduced from 4096x4096 (25MB) to 1024x1024 (~1MB)

### Unchanged
- All Remotion skills (remotion-spec, remotion-builder, remotion-best-practices) preserved without modification

## [1.1.0] - April 9, 2026

### Changed
- Rebrand from "ElevenLabs Academy Plugin" to "ElevenLabs Remotion Kit"
- Update README to reflect current skills (removed lesson-builder and project-context references)
- Update plugin.json name, description, and repo URL
- Consolidate skills: merge lesson-author into lesson-builder, rename remotion-spec to remotion-spec-builder

### Fixed
- Asset-setup: font paths, project type detection, dynamic versioning

## [1.0.0] - April 4, 2026

### Added
- Initial release as ElevenLabs Academy plugin for Claude Code
- 5 skills: asset-setup, remotion-spec, remotion-builder, remotion-best-practices, brand
- V2 design system with hero, content, and hybrid modes
- Brand asset distribution via GitHub Releases (~278MB optimized)
- Central storage support (`~/.elevenlabs-assets/`)
- 8-variant BrandedCard system with darkflat default
