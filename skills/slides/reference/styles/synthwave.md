---
name: Synthwave
category: aesthetica
suitable_for: slides
---

# Synthwave

## Visual Direction
1980s retro-futurism: a horizon line dividing deep purple-black sky from a neon-pink-to-cyan gradient ground, overlaid with a perspective grid receding to infinity. The palette is electric — hot pink, electric cyan, warm purple — all glowing against near-black. Chrome and metallic text effects evoke VHS covers and arcade cabinets. Typography is bold condensed display at large scale, often with a glow or text-shadow halo. The overall mood is nostalgic, cinematic, and unapologetically stylized. This is not subtle — it's a deliberate aesthetic statement that works for dev conferences, creative talks, retrospectives, and anything that benefits from personality over restraint.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #0d0221 | Deep purple-black void — the night sky |
| Surface | #1a0a2e | Slightly lighter purple — elevated panels |
| Text Primary | #ffffff | Pure white — high contrast on dark |
| Text Secondary | #b794d6 | Muted lavender — for body and metadata |
| Neon Pink | #ff2a6d | Hot pink — primary neon accent |
| Neon Cyan | #05d9e8 | Electric cyan — secondary neon accent |
| Warm Purple | #7b2d8e | Deep magenta-purple — tertiary, gradient use |
| Grid Line | #ff2a6d | Pink at 15-25% opacity — the perspective grid |
| Sun Gradient | #ff6b35 to #ff2a6d | Orange-to-pink — the horizon sun |

## Typography

### Display Font
- **Family:** Bebas Neue or Oswald
- **Weights:** 700
- **Size Range:** 72–160px; clamp(72px, 10vw, 160px)
- **Letter Spacing:** 0.05em (slightly open for glow readability)
- **Style Notes:** All-caps always. Apply `text-shadow` glow: `0 0 20px rgba(255,42,109,0.5), 0 0 60px rgba(255,42,109,0.2)` in Neon Pink. Headlines can also use a CSS gradient fill (pink → cyan) via `background-clip: text`.

### Body Font
- **Family:** Exo 2 or Inter
- **Weights:** 300, 400
- **Size Range:** 14-20px
- **Line Height:** 1.6
- **Style Notes:** Light weight preferred — the thin strokes contrast with the heavy display. Use white or lavender depending on background darkness.

## Design Principles
1. **The grid is iconic.** A CSS perspective grid receding to a horizon line is the signature visual. Use `linear-gradient` with thin pink lines on a dark ground, transformed with CSS `perspective` and `rotateX`. It appears on at least the title and closing slides.
2. **Glow is structure, not decoration.** Text-shadow and box-shadow with neon colors create the "lit from within" quality. Apply to headlines, accent borders, and key data. Don't glow everything — it loses impact.
3. **Two neon accents maximum.** Hot pink and electric cyan. They alternate roles but never compete equally on one slide — one dominates, one accents.
4. **Dark backgrounds only.** The entire palette collapses on light backgrounds. Every slide is dark — the void is the canvas.
5. **Horizon composition.** Many slides benefit from a horizontal division: dark sky above, grid/gradient below. Content floats in the upper portion.

## Slide Application Notes
- **Title Slides:** Full perspective grid background. Large all-caps headline with neon pink glow centered above the horizon. Subtitle in lavender below. Optional: a large circle gradient (the "sun") positioned at the horizon center.
- **Content Slides:** Dark background with a subtle grid at very low opacity (5-10%). Content in white/lavender on the left. A vertical neon accent line (2px, pink or cyan) separating columns or marking sections.
- **Data/Chart Slides:** Charts use neon pink and cyan for data series on dark background. Axis labels in lavender. Grid lines at 10% opacity. Bar charts and line charts work well — the glow effect on data points adds visual interest.
- **Section Dividers:** Full perspective grid. Large section number in outline type (stroke only, no fill) with neon glow. Section title below in solid white.
- **Closing Slides:** Matching the title composition. Headline with glow, perspective grid, contact info in mono font at the bottom.
- **Do:** Use the perspective grid consistently; apply glow selectively to headlines and key elements; maintain the dark-only palette; let the neon colors create visual hierarchy.
- **Don't:** Use light backgrounds; apply glow to body text; use more than two neon colors; add realistic photography (it clashes with the stylization).
