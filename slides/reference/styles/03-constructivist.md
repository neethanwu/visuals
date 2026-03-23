---
name: Constructivist
category: aesthetica
suitable_for: slides
---

# Constructivist

## Visual Direction
Soviet avant-garde monumentalism translated for the modern slide deck. The defining move is a large red wedge — a flat #c41e1e geometric form rotated at -15 degrees, consuming the right half of the composition and serving as both background and ideological statement. Type is set in Oswald, condensed and bold, with headlines stacked vertically at near-poster scale (up to 160px, weight 700, all-caps). The warm tan ground (#e6dac8) references aged propaganda posters. Black geometric accents — thick bars, circles with heavy borders, angular triangles — punctuate the layout with precision and aggression. Every slide should feel like a manifesto.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #e6dac8 | Warm tan, aged paper — the constructivist ground |
| Wedge / Primary Red | #c41e1e | The defining red wedge; used for dominant shapes |
| Text Primary | #1a1a1a | Near-black for all typography on light ground |
| Text on Red | #ffffff | White for text sitting within the red field |
| Body Text | #4a3a2a | Warm dark brown for body copy on the tan ground |
| Char Labels | #5a4a3a | Medium brown for supporting small text |
| Geo Accent | #1a1a1a | Black used for geometric shapes (bars, circles, triangles) |

## Typography

### Display Font
- **Family:** Oswald
- **Weights:** 700 (headlines), 500 (labels), 300 (light accents)
- **Size Range:** 72–160px; clamp(72px, 9vw, 160px)
- **Letter Spacing:** 0.05em on slogans; 0.4em on section number labels
- **Style Notes:** All-caps always. Line height 0.82 — lines stack tight, compressing into a single mass. Headlines should read as a single geometric block.

### Body Font
- **Family:** DM Sans
- **Weights:** 400 (body), 500 (char labels)
- **Size Range:** 10–13px
- **Line Height:** 1.9 (body); char items use 0.2em letter spacing at 10px uppercase

## Design Principles
1. The red wedge is the composition — all other elements orient themselves around it.
2. Typography is a geometric object: stack lines of all-caps Oswald to form rectangular masses.
3. Use only three colors per slide: the background tan, constructivist red, and near-black. No gradients, no tints.
4. Diagonal tension is essential — rotate elements at -15 degrees to match the wedge's angle and create kinetic energy.
5. Geometric primitives (thick-bordered circles, triangles, heavy bars) reinforce the industrial-mechanical aesthetic.

## Slide Application Notes
- **Title Slides:** Large all-caps Oswald headline on the left (tan ground), bold slogan on the right (within or adjacent to the red field in white). Section number with a 3px solid underline.
- **Content Slides:** Two-column grid: left column is content on tan, right column overlaps the red wedge with white text. Use `.slogan` typography for section titles within the red area.
- **Data/Chart Slides:** Bar charts only — never pie charts. Bars in #c41e1e and #1a1a1a, no fills between. Labels in Oswald 500 uppercase. Grid lines in rgba(0,0,0,0.1).
- **Closing Slides:** Single all-caps slogan at 80–120px spanning the full width, the red wedge bleeding off the right edge. White text over the red portion.
- **Do:** Bleed geometric shapes off slide edges; maintain the -15 degree rotational system across all decorative elements; use thick strokes (3–8px) for all geometric accents.
- **Don't:** Use rounded corners or drop shadows; mix serif fonts with the Oswald system; reduce the red wedge to a small accent — it must dominate.
