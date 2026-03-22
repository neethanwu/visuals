---
name: Deconstructivist
category: aesthetica
suitable_for: slides
---

# Deconstructivist

## Visual Direction
Architecture's most disruptive movement applied to the slide canvas. The ground is a warm off-white (#f0ede8) that reads as neutral, but every element on it resists alignment: headlines are displaced horizontally (translateX 60px), subtitles rotate at -2.5 degrees, pull-quotes tilt at -1 degree, and grid cells rotate alternately at ±0.5 degrees. Space Mono — a monospaced font associated with code and systems — carries all typography, colliding the language of logic with intentional instability. A single red line (#cc0000) at 3px, rotated -5 degrees, bisects the layout as an interruption. Fragmented ghost rectangles float behind the content, rotated at various angles, suggesting plans that were never resolved. The effect is controlled disorientation — the content remains readable, but the slide refuses to let the viewer settle.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #f0ede8 | Warm off-white, slightly warmer than paper |
| Text Primary | #1a1a1a | Near-black; used for main headlines |
| Displaced Accent | #cc0000 | Red used for the displaced word and accent rule — the rupture |
| Body Text | #666666 | Medium grey for paragraph text |
| Pull Quote | #222222 | Dark grey for emphasized pull-quote text |
| Section Number | #aaaaaa | Light grey — the label recedes |
| Char Cell Text | #888888 | Medium-light grey for grid cell labels |
| Cell Borders | #dddddd | Soft grey borders on the character grid |

## Typography

### Display Font
- **Family:** Space Mono
- **Weights:** 700 (headlines and pull quotes), 400 (body and labels)
- **Size Range:** 44–80px; clamp(44px, 5.5vw, 80px)
- **Letter Spacing:** -0.04em (tight, resisting the monospace's natural openness)
- **Style Notes:** One word or phrase in the headline is displaced (translateX: 60px, rotate: -2.5deg) and colored #cc0000 — this is the deconstructive gesture. Do not center or justify headlines; left-align everything and let the displacement create visual tension.

### Body Font
- **Family:** Space Mono
- **Weights:** 400
- **Size Range:** 9–13px
- **Line Height:** 2.0 (body); grid cells use 9px at 0.15em letter spacing, uppercase

## Design Principles
1. Displacement is the primary tool: shift individual text elements off-axis using rotation and translation, never the entire layout.
2. The red accent (#cc0000) appears exactly once per slide as a rupture — a rotated rule, a displaced word, or a border-left on a pull-quote.
3. Ghost rectangles (1px borders, near-zero opacity) populate the background as remnants of abandoned structures.
4. The grid is 1.2:1 columns with an 80px gap — notably asymmetric, reinforcing the off-balance feeling.
5. Monospace type maintains legibility while the spatial displacement creates the deconstructive reading experience.

## Slide Application Notes
- **Title Slides:** Headline in Space Mono 700, one key word shifted right 60px and colored #cc0000. Subtitle rotated -2.5 degrees. Section number in light grey with 0.4em tracking above.
- **Content Slides:** Two-column asymmetric layout (1.2fr : 1fr). Left: body text + tilted pull-quote with red left-border. Right: character trait grid with alternating ±0.5deg cell rotations.
- **Data/Chart Slides:** Data cells in a 2×2 grid, each cell rotated slightly (odd: +0.5deg, even: -0.5deg). Labels in Space Mono 9px uppercase. The #cc0000 red accent appears only on the highest-value data point.
- **Closing Slides:** Large displaced headline; the final word breaks onto a second line shifted further right than expected. Single red horizontal rule 200px wide, rotated -5deg, placed above the text mass.
- **Do:** Let elements visually collide and overlap at the edges; use the translateX displacement system consistently; maintain readability as the baseline — deconstruction is not chaos.
- **Don't:** Apply rotation to more than 2–3 elements per slide (dilutes the effect); use the red on more than one element; add color fills to the ghost rectangles.
