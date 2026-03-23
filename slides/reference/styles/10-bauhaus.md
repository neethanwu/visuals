---
name: Bauhaus
category: aesthetica
suitable_for: slides
---

# Bauhaus

## Visual Direction
The Dessau school's founding principle — form follows function — expressed through the three primary shapes and three primary colors. The ground is a warm off-white (#f3f0e8), slightly warmer than pure white, evoking the Bauhaus school's institutional papers. A large red circle, a blue rectangle, and a yellow triangle compose the right-column "Komposition" — the geometric painting that anchors every layout — framed by a 3px solid #1a1a1a border. These shapes appear at scale on the right side of every slide while reduced ghost versions (at 8–10% opacity) populate the background. DM Sans at weight 900 gives the headline a mechanical density that references Herbert Bayer's universal type. The three Bauhaus colors — Itten's circle red (#e63333), Albers' deep blue (#1a5ba0), and Klee's yellow (#e8a820) — appear only as solid fills, never as gradients.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #f3f0e8 | Warm off-white, institutional paper tone |
| Text Primary | #1a1a1a | Near-black for all typography and structural lines |
| Body Text | #555555 | Medium grey for body copy and principle labels |
| Bauhaus Red | #e63333 | Circle — the primary shape color for emotion/movement |
| Bauhaus Blue | #1a5ba0 | Rectangle — the primary shape color for reason/space |
| Bauhaus Yellow | #e8a820 | Triangle — the primary shape color for thought/spirit |
| Section Number | #e63333 | Section label uses the red, reinforcing the circle association |
| Composition Border | #1a1a1a | 3px border framing the right-column geometric composition |

## Typography

### Display Font
- **Family:** DM Sans
- **Weights:** 900 (headline)
- **Size Range:** 80–130px; clamp(80px, 9vw, 130px)
- **Letter Spacing:** -0.03em (tightened to compress the mechanical mass)
- **Style Notes:** The headline splits across two lines with color applied to individual words — one line in Bauhaus Red (#e63333), one in Bauhaus Blue (#1a5ba0), creating a painted-type effect. Never use more than two colors within a single headline.

### Body Font
- **Family:** DM Sans
- **Weights:** 400 (body), 700 (principle labels)
- **Size Range:** 11–14px
- **Line Height:** 2.0 (body); principle items use 11px at 0.1em tracking, uppercase, weight 700
- **Style Notes:** Principle list items use shape icons (filled circle, filled square, triangle via CSS borders) in the three Bauhaus colors as list markers. The shape-to-meaning mapping is Bauhaus doctrine: circle = red, square = blue, triangle = yellow.

## Design Principles
1. Composition is built from exactly three shapes (circle, rectangle, triangle) in exactly three colors (red, blue, yellow) — no other shapes or colors permitted.
2. The geometric composition belongs in a bordered frame on the right side of the layout; the frame (3px solid black) makes it a painting, not a diagram.
3. Typography functions as geometry: the DM Sans 900 headline at large scale is a rectangular mass, visually equivalent to the blue rectangle in the composition.
4. Structural dividers are 2–3px solid #1a1a1a lines — never dashed, never lighter. They are load-bearing beams, not decorations.
5. Background ghost shapes (at 8–10% opacity) establish the Bauhaus spatial system without competing with foreground content.

## Slide Application Notes
- **Title Slides:** DM Sans 900 headline across the left column with color-split words. Section number in Bauhaus Red (#e63333) at 10px uppercase. Right column: full-size geometric composition in its 3px-bordered frame. Composition contains the three shapes overlapping, divided by horizontal and vertical black rules.
- **Content Slides:** Two-column grid with 80px gap. Left: headline + body paragraph + principle list with shape markers. Right: geometric composition (scaled to column width). Body text in DM Sans 400 at 14px/2.0.
- **Data/Chart Slides:** Use the three Bauhaus colors as data series colors. Bar charts with flat fills (no gradients). Horizontal rules in 2px #1a1a1a separate chart from labels. Chart background #f8f6f0 (slightly warmer than the main ground).
- **Closing Slides:** Left column: large DM Sans 900 headline with color splits. Right column: simplified composition — just the three shapes without dividing lines. Apply text in DM Sans 700 uppercase at 10px, 0.15em tracking, grey (#999).
- **Do:** Use the three colors only as solid fills; maintain the 3px black border on the composition frame in every layout; apply the shape-marker system to all list elements.
- **Don't:** Introduce gradients, shadows, or tints of the three colors; use the shapes without the black structural lines in the composition; exceed three colors plus black-and-white in any single slide.
