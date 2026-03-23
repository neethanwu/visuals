---
name: Pop Art
category: aesthetica
suitable_for: slides
---

# Pop Art

## Visual Direction
Warhol meets Lichtenstein: saturated primary colors, bold black outlines, halftone dot patterns, and comic-book energy. The palette is deliberately unsubtle — bright red, yellow, blue, and pink against white or black. Every element has a thick black stroke or border. Halftone dots (Ben-Day dots) appear as decorative texture on backgrounds, shapes, or inside letterforms. Typography is massive, condensed, and punchy — often rotated or placed at angles. The overall mood is bold, irreverent, graphic, and attention-grabbing. This is a style for decks that need personality and visual impact over corporate restraint.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #ffffff | Pure white — clean pop canvas |
| Text Primary | #000000 | Pure black — maximum contrast, comic outlines |
| Pop Red | #e3342f | Saturated warm red — primary pop color |
| Pop Yellow | #ffed4a | Bright yellow — secondary pop color |
| Pop Blue | #3490dc | Bright blue — tertiary pop color |
| Pop Pink | #f66d9b | Hot pink — accent pop color |
| Halftone Base | #e3342f | Red at 15-25% opacity — for dot patterns |
| Surface | #f7fafc | Very light grey — for alternate slide backgrounds |
| Outline | #000000 | 3-4px solid black — on everything |

## Typography

### Display Font
- **Family:** Archivo Black or Anton
- **Weights:** 900
- **Size Range:** 72–160px; clamp(72px, 10vw, 160px)
- **Letter Spacing:** -0.02em
- **Style Notes:** All-caps or mixed-case at massive scale. Headlines can be rotated ±2-5deg for dynamism. Use black fill with no additional effects — the weight and scale do the work. Individual words can be colored in different pop colors for emphasis.

### Body Font
- **Family:** DM Sans or Inter
- **Weights:** 400, 600
- **Size Range:** 14-20px
- **Line Height:** 1.5
- **Style Notes:** Clean sans-serif body. Use black on white or white on pop-color backgrounds.

## Design Principles
1. **Black outlines define everything.** Every shape, card, image frame, and decorative element gets a 3-4px solid black border. This is the comic-book DNA — without it, the style loses its pop quality.
2. **Halftone dots as signature texture.** Use CSS `radial-gradient` repeating patterns to create Ben-Day dot screens. Apply at 15-25% opacity to backgrounds, large shapes, or inside color blocks. Pattern: `radial-gradient(circle, color 1px, transparent 1px)` with `background-size: 6px 6px`.
3. **One pop color per slide dominates.** Each slide features one primary pop color covering 30-50% of the area. Rotate through the palette across slides for variety. Never use all four colors equally on one slide.
4. **Scale contrast is extreme.** Headlines are massive (140px+), body text is normal. The tension between giant and small creates the pop energy.
5. **White space is canvas.** The white background is active — it's the comic page. Don't fill every inch. Let the bold elements punch against white.

## Slide Application Notes
- **Title Slides:** Massive headline in black, rotated ±3deg. A large pop-color shape (circle, rectangle, or speech bubble) behind or overlapping the text. Halftone dot texture on the shape. Subtitle in body font below.
- **Content Slides:** One side: pop-color background block with white text. Other side: white background with black text. 4px black border separating them. Or: content cards with thick black outlines on white.
- **Data/Chart Slides:** Bar charts in pop colors with black outlines on each bar. No subtle gridlines — just bold data against white. Labels in body font, black.
- **Quote Slides:** Speech bubble shape (CSS border-radius + triangle) in pop yellow or pink with black outline. Quote text inside in black. Attribution outside the bubble.
- **Section Dividers:** Full pop-color background with massive white or black headline. Halftone dot texture overlay. Section number in a starburst or circle shape.
- **Closing Slides:** "POW!" or "THANKS!" energy — massive text with a starburst shape behind it. Contact info in a speech bubble.
- **Do:** Use thick black outlines on everything; rotate text slightly for energy; apply halftone dots as texture; keep one color dominant per slide; embrace the boldness.
- **Don't:** Use thin lines or hairline borders; apply gradients or shadows; use muted or desaturated colors; be subtle — this style is the opposite of restraint.
