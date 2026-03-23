---
name: Blueprint
category: aesthetica
suitable_for: slides
---

# Blueprint

## Visual Direction
Technical drawing on engineering blue: white linework, precise grid coordinates, annotation-style labels, and the visual language of architectural and engineering documents. The background is the iconic blueprint blue — not bright, but a muted, slightly dusty medium blue. All content is rendered in white or light cyan, creating the effect of a cyanotype print. Typography is monospaced and technical — labels are small, uppercase, with coordinate-style numbering. Lines are thin and precise (1px). The grid is always present, faintly, underlying everything. Decorative elements are technical: dimension lines with arrows, coordinate markers, cross-hairs, and section callouts. This is ideal for engineering talks, architecture presentations, technical deep-dives, and any content where precision and systematic thinking are the message.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #1e3a5f | Blueprint blue — the cyanotype ground |
| Grid Line | #2a5080 | Slightly lighter blue — the background grid |
| Text Primary | #ffffff | Pure white — all linework and type |
| Text Secondary | #8ab4d6 | Light blue-grey — annotations and metadata |
| Line Work | #ffffff | White at 80-100% — structural lines |
| Dimension Line | #8ab4d6 | Light blue — annotation and dimension lines |
| Accent | #ff6b35 | Warm orange — for callouts and highlights (optional, used sparingly) |
| Surface | #1a3355 | Darker blue — for inset panels |

## Typography

### Display Font
- **Family:** JetBrains Mono or IBM Plex Mono
- **Weights:** 500, 700
- **Size Range:** 48–96px; clamp(48px, 6vw, 96px)
- **Letter Spacing:** 0.04em (open, technical)
- **Style Notes:** All-caps always. Mono is mandatory — it reinforces the technical drawing aesthetic. Headlines read as engineering labels at large scale.

### Body Font
- **Family:** JetBrains Mono or IBM Plex Mono
- **Weights:** 400
- **Size Range:** 13-16px
- **Line Height:** 1.6
- **Style Notes:** Mono for everything — display and body. This is the only style where a single monospaced family covers all roles. Labels use uppercase with generous tracking (0.1em+).

### Annotation Font
- **Family:** Same mono family
- **Weights:** 400
- **Size:** 10-11px
- **Style Notes:** Small uppercase labels with coordinate-style content: "SEC. 01", "REF: A-04", "SCALE: 1:1". These appear as annotations on dimension lines and section markers.

## Design Principles
1. **The grid is always present.** A subtle background grid (40-60px cells) in slightly lighter blue underlies every slide. Use `linear-gradient` in both directions. The grid is the drawing surface — content is placed on it.
2. **White on blue only.** All content is white or light blue on the blueprint ground. No other colors except an optional warm orange for rare callouts. The monochromatic palette is the identity.
3. **Technical annotation as design language.** Dimension lines (thin lines with small perpendicular end marks), coordinate labels, section markers, and cross-hairs are the decorative vocabulary. Use thin SVG lines with arrowheads for connecting elements.
4. **Precision in spacing.** Everything aligns to the visible grid. Spacing is systematic and even. This is the most grid-strict style in the collection.
5. **All type is mono.** No serif, no sans-serif. Monospaced only. The consistent character width reinforces the technical document feel.

## Slide Application Notes
- **Title Slides:** Blueprint grid background. Large all-caps mono headline in white. A horizontal dimension line below the title with small perpendicular end marks. Project metadata ("SEC. 01 / REV. A / DATE: 2025.03") in annotation font at the bottom.
- **Content Slides:** Grid background. Content aligned to grid intersections. Section label with coordinate marker ("A-01") at top left. Thin white horizontal rule separating header from body. Body text in mono.
- **Data/Chart Slides:** Charts rendered in white and light blue on blueprint background. Grid lines align with the background grid. Axis labels in annotation font. Dimension-line callouts pointing to key data points.
- **Diagram/Process Slides:** Flowcharts and diagrams rendered as technical drawings — white lines, right angles, annotation labels at connection points. This is where the blueprint style shines most.
- **Closing Slides:** Large headline in white mono. A drawing title block in the bottom-right corner (common in engineering drawings): project name, author, date, revision — all in annotation font inside a thin white-bordered rectangle.
- **Do:** Maintain the grid on every slide; use mono type exclusively; add technical annotations (coordinates, section marks, dimension lines); keep the white-on-blue palette strict.
- **Don't:** Use non-mono fonts; add color beyond the blue/white palette (orange is the only exception, used sparingly); use rounded corners; add shadows or gradients; break grid alignment.
