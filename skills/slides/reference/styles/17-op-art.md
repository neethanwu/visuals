---
name: Op Art
category: aesthetica
suitable_for: slides
---

# Op Art

## Visual Direction
Op Art (Optical Art) for slides is a study in perceptual precision: pure white backgrounds, absolute black type, and geometric pattern systems that activate the viewer's visual field without resorting to color. Inspired by Bridget Riley and Victor Vasarely, this style weaponizes optical illusion — striped text fills, repeating conic gradients, concentric ring structures, and alternating skewed lines — to create movement and tension on an otherwise static slide. Typography is massive and tightly tracked, with striped-fill treatment on display text that makes letterforms vibrate. The aesthetic communicates analytical intelligence, systems thinking, and confident minimalism.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #ffffff | Pure white — the optical ground |
| Text Primary | #111111 | Near-black for all primary type |
| Text Body | #666666 | Medium grey for paragraph text |
| Text Muted | #888 / #aaa / #bbb | Stepped greys for secondary labels and metadata |
| Pattern Fill | #111111 at 4–5% opacity | Subtle optical texture: conic gradient checkers, concentric rings, wave lines |
| Rule / Border | #eeeeee | Light grey for list dividers and section separators |
| Strong Rule | #111111 | Full-weight 3px rule for section headers and app blocks |

## Typography

### Display Font
- **Family:** Outfit
- **Weights:** 900 (Black)
- **Size Range:** 64–140px
- **Letter Spacing:** –0.04em (tight)
- **Style Notes:** Line-height 0.85 for extreme vertical compression; primary headline word receives striped fill (repeating-linear-gradient 90deg, #111 0–3px, transparent 3–7px) applied as background-clip text to create the optical vibration effect; secondary word renders in solid #111

### Body Font
- **Family:** Outfit
- **Weights:** 400 (Regular), 600 (SemiBold)
- **Size Range:** 13–14px for slides
- **Line Height:** 2.0

### Label Font
- **Family:** Outfit
- **Weights:** 600, 700
- **Size Range:** 9–12px
- **Letter Spacing:** 0.15–0.35em
- **Style Notes:** All-caps with wide tracking; used for section numbers, characteristic labels, and application block headers

## Design Principles
1. The optical pattern (conic gradient checker at 5% opacity) is background texture only — it must never compete with content legibility.
2. Scale contrast is the primary compositional force: 64–140px headlines against 14px body text, with nothing in between.
3. Tight negative letter-spacing (–0.04em) on display type compresses letterforms into a mass, amplifying the optical density.
4. Horizontal rules at 2px (#eee) act as the grid — list items and content sections are separated by lines, not whitespace alone.
5. Geometry accumulates in the margins: concentric rings off the right edge, wavy lines at the left — these signal the movement vocabulary without intruding on the content zone.

## Slide Application Notes
- **Title Slides:** Maximum headline size (120–140px), line-height 0.85, with the stripe-fill treatment on the primary word. Sub-heading in 12px Outfit at 0.2em tracking, all-caps, color #aaa. No decorative elements in the center zone — let the type scale carry the composition.
- **Content Slides:** Two-column layout (1fr / 1fr). Left column: body text in Outfit 400 at #666, 2.0 line-height. Right column: characteristics list with top/bottom 2px #eee borders per item, all-caps labels in #888. Include a concentric ring motif positioned off the right canvas edge.
- **Data/Chart Slides:** Use stark black-and-white fills for chart elements — no color. Apply stripe or checker patterns as fill textures for categorical differentiation. Axes and grid lines in #eee; data labels in Outfit 600 #111.
- **Closing Slides:** Return to the maximum headline treatment. Add the 3px black horizontal rule above a single label line in 9px all-caps #bbb. Optical patterns can increase slightly in opacity (up to 8%) on closing slides to create a sense of visual resolution.
- **Do:** Push headline sizes to the extreme upper bound; use the stripe-fill treatment as a headline highlight, not on every text element; keep all color out of the palette.
- **Don't:** Use italic or serif type anywhere; reduce headline size to match "comfortable" proportions — the tension of scale is the point; add any color accent, even a small one.
