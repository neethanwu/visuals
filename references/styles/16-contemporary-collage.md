---
name: Contemporary Collage
category: aesthetica
suitable_for: slides
---

# Contemporary Collage

## Visual Direction
Contemporary Collage translates the physical act of cutting, layering, and taping paper into a digital slide aesthetic. The background is warm cream (#f0e8df) — the color of aged cartridge paper — against which torn-paper shapes, translucent tape strips, and slightly rotated text elements create an assembled, handmade quality. Typography deliberately clashes: an italic serif headline sits next to monospaced technical labels, evoking the tension between editorial craft and archival documentation. The overall mood is personal, curated, and intellectually alive — a deck that feels like a well-researched moodboard rather than a corporate template.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #f0e8df | Warm cream, aged paper tone |
| Torn Paper Overlay | #d4c0a8 | Medium warm tan for torn paper fragments |
| Text Primary | #2a2218 | Deep warm near-black for headlines |
| Text Body | #5a4a3a | Medium warm brown for body copy |
| Text Muted | #999 / #bbb | Cool greys for mono labels and metadata |
| Tape Accent | rgba(255,230,180,0.35) | Translucent amber for tape strip motif |
| Red Accent Border | #c88 | Desaturated terracotta for left-border rule on mono items |

## Typography

### Display Font
- **Family:** Playfair Display
- **Weights:** 900 (Black), 400 Italic
- **Size Range:** 42–72px
- **Letter Spacing:** Default (no tracking modification)
- **Style Notes:** Headline uses weight 900 for the primary word; italic 400 applied to secondary word via `.serif-w` class; line-height 1.05 for tight stacking

### Body Font
- **Family:** Libre Baskerville
- **Weights:** 400 (Regular)
- **Size Range:** 14px for slides
- **Line Height:** 2.2

### Label / Accent Font
- **Family:** IBM Plex Mono
- **Weights:** 400, 500
- **Size Range:** 10–11px
- **Letter Spacing:** 0.1–0.25em
- **Style Notes:** All-caps with moderate tracking; used for section numbers, subtitles, and even-numbered list items; creates the "archival tag" aesthetic

## Design Principles
1. Collision is compositional — mix serif italic and monospaced type within the same content area to evoke layered media sources.
2. Micro-rotations (–0.5deg to +0.5deg) on text elements simulate hand-placed paper; keep them subtle enough to feel accidental rather than designed.
3. Warm neutrals only — resist adding saturated color; the collage effect comes from tonal contrast between cream, tan, and brown, not from hue variation.
4. The torn paper shapes (clip-path polygons) should appear in the corners and margins, never obscuring primary content.
5. Asymmetric two-column grids (1.3fr / 1fr) reflect the uneven, found-object quality of real collage.

## Slide Application Notes
- **Title Slides:** Large Playfair Display headline with mixed-weight italic/bold treatment; monospace subtitle in #bbb at 0.1em tracking; torn paper shape in upper-right corner rotated 7deg; tape strip accent near the top edge.
- **Content Slides:** Two-column grid (wider left for body, narrower right for a characteristics list). Alternate list items between Playfair italic (for qualitative descriptors) and IBM Plex Mono uppercase (for categorical labels). Apply a 2px #c88 left border on mono items.
- **Data/Chart Slides:** Use the warm brown palette (#5a4a3a, #d4c0a8, #2a2218) for chart fills. Add monospaced data labels in #999. Avoid ruled grid lines — use tonal fills instead to keep the handmade quality.
- **Closing Slides:** Reduce content density significantly. One large Playfair Display phrase in #2a2218, a tape strip motif, and a single IBM Plex Mono line in #bbb. Let the cream background breathe.
- **Do:** Embrace slight imperfection — small rotations, offset alignments, and tonal variation are features; use the tape and torn-paper shapes as genuine compositional anchors, not afterthoughts.
- **Don't:** Use clean digital sans-serif fonts anywhere in this style; apply saturated colors; over-layer the collage shapes to the point of obscuring type.
