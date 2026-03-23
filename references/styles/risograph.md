---
name: Risograph
category: aesthetica
suitable_for: slides
---

# Risograph

## Visual Direction
The aesthetic of risograph printing translated to screen: bold spot colors layered with slight misregistration, halftone dot textures at low opacity, and the deliberate imperfection of ink on rough paper. The palette is limited to 2-3 spot colors (no full-color blending) — typically a saturated primary paired with a warm secondary, both printed on a warm off-white ground that reads as uncoated stock. Where colors overlap, they multiply into a rich third tone. Typography is bold and flat, sitting directly on the paper ground without cards or containers. The grain texture of risograph ink is present but subtle — a noise overlay at 3-5% opacity. Everything feels hand-produced, tactile, and deliberately lo-fi in a way that signals creative confidence.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #f4efe6 | Warm off-white — uncoated paper stock |
| Text Primary | #1a1a1a | Near-black — dense ink on paper |
| Spot Color 1 | #e63946 | Risograph red — the dominant spot ink |
| Spot Color 2 | #264653 | Deep teal — the secondary spot ink |
| Overlap | #1d2d35 | Multiply blend of red + teal — appears at intersections |
| Halftone Dot | #e63946 | Red at 8-15% opacity — creates the dot texture |
| Text Secondary | #6b6256 | Warm dark grey — for captions and metadata |
| Accent Light | #f4a261 | Warm amber — optional third spot for highlights |

## Typography

### Display Font
- **Family:** Outfit or Space Grotesk
- **Weights:** 800-900
- **Size Range:** 64–140px; clamp(64px, 9vw, 140px)
- **Letter Spacing:** -0.03em (tight)
- **Style Notes:** Bold and flat — no italic, no thin weights. Headlines sit directly on the paper ground. Mix-case (not all-caps) feels more print-authentic.

### Body Font
- **Family:** DM Sans or Inter
- **Weights:** 400, 500
- **Size Range:** 14-18px
- **Line Height:** 1.6
- **Style Notes:** Clean sans-serif body. Keep it readable against the textured background.

## Design Principles
1. **Limited palette is non-negotiable.** 2-3 spot colors maximum. The constraint is the identity. No gradients, no full-color images — everything is expressed through spot color layers.
2. **Halftone dots as texture.** Use CSS `radial-gradient` repeating patterns at low opacity (8-15%) to create the riso dot screen effect. Apply to backgrounds, cards, or decorative blocks — never to text.
3. **Misregistration as decoration.** Duplicate key elements (headlines, shapes) with a slight offset (2-4px) in the second spot color at reduced opacity. This simulates the registration error of multi-pass printing.
4. **No containers, no cards.** Content sits directly on the paper ground, separated by whitespace and color blocks. If you need a container, it's a solid spot-color rectangle — not a bordered card.
5. **Geometric shapes are structural.** Circles, rectangles, and triangles in spot colors function as compositional anchors, not decoration. They occupy large portions of the slide.

## Slide Application Notes
- **Title Slides:** Large geometric shape (circle or rectangle) in Spot Color 1 occupying 40-60% of the slide. Headline in near-black overlapping the shape edge. Subtitle in Text Secondary below. Halftone dot texture across the background at 8% opacity.
- **Content Slides:** Two-column layout. Left column: headline + body text on paper ground. Right column: solid spot-color block with white or light text. Or: full-width with spot-color section header bars.
- **Data/Chart Slides:** Charts use only the spot colors. Bar charts work well — filled in Spot Color 1 and 2. No gridlines. Axis labels in mono font. The halftone texture can appear behind the chart area.
- **Quote Slides:** Large pull quote in Spot Color 2 with a misregistered ghost in Spot Color 1 offset 3px behind. Attribution in body font, Text Secondary.
- **Closing Slides:** Bold headline in Spot Color 1. Contact info in mono. Large geometric shape anchoring the composition.
- **Do:** Maintain the 2-3 color limit strictly; use halftone dot texture consistently; let geometric shapes be large and bold; embrace the lo-fi tactile quality.
- **Don't:** Use full-color photography; add gradients or shadows; use thin font weights; add rounded corners; use more than 3 colors.
