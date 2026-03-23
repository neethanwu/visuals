---
name: Color Field
category: aesthetica
suitable_for: slides
---

# Color Field

## Visual Direction
Color Field painting — particularly the work of Mark Rothko — understood that color itself carries emotional weight without requiring form or narrative. This slide style translates that insight directly: the entire background is divided into three massive, softly blurred horizontal bands of burnt orange (#d94f00), deep sienna (#8b3a1a), and midnight blue (#1a3a6a), with their boundaries dissolved by a 12px blur at the meeting edges. Text floats in the center at low opacity, deferring to the color as the primary communicative force. The palette is warm-to-cool — fire descending into depth — and the emotional register is contemplative, weighty, and unhurried. Cormorant Garamond at light weight reinforces the sense of words appearing within a field rather than being imposed upon it.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background Base | #4a2a3a | Deep plum — the unifying undertone visible at edges |
| Upper Field | #d94f00 | Burnt orange, occupying the upper 35% of the composition |
| Middle Field | #8b3a1a | Deep sienna-brown, occupying the middle 35% |
| Lower Field | #1a3a6a | Midnight blue, occupying the lower 30% |
| Text Primary | rgba(255,255,255,0.85) | Near-white with 15% transparency, softened against the fields |
| Text Secondary | rgba(255,255,255,0.55) | Dimmed white for body copy |
| Text Muted | rgba(255,255,255,0.40–0.45) | Very faint white for labels, metadata, and apply notes |
| Text Subtle | rgba(255,255,255,0.25) | Ghost white for decorative separators |

## Typography

### Display Font
- **Family:** Cormorant Garamond
- **Weights:** 300 (Light)
- **Size Range:** 36–60px
- **Letter Spacing:** 0.06em
- **Style Notes:** Light weight is essential — heavy type would clash with the atmospheric color fields. Text-shadow (0 2px 16px rgba(0,0,0,0.4)) ensures legibility against the saturated backgrounds. Centered alignment. Line-height 1.2.

### Body Font
- **Family:** Cormorant Garamond
- **Weights:** 300 (Light), 400 Italic
- **Size Range:** 13–14px for slides
- **Line Height:** 2.4

### Label Font
- **Family:** Cormorant Garamond
- **Weights:** 300
- **Size Range:** 10px
- **Letter Spacing:** 0.25–0.4em
- **Style Notes:** All-caps with moderate tracking; color rgba(255,255,255,0.45); text-shadow on all label text to maintain separation from the color fields beneath

## Design Principles
1. The color fields are the subject — text is a visitor. Every typographic decision (light weight, low opacity, centered layout) honors the primacy of color.
2. The three-band structure (warm / transitional / cool) is inviolable; the proportions (35% / 35% / 30%) and colors define the emotional arc of the composition.
3. Blurred edges between fields (12px filter blur at transition zones) are critical — they create the breathing, luminous quality of Rothko's painted edges and prevent the slide from reading as a flag or stripe.
4. Maximum content width is 600px, centered, keeping the color fields fully visible in the margins and preventing text from bleeding into the field edges.
5. All text carries a subtle drop shadow (0 1px 6px to 0 2px 16px rgba(0,0,0,0.3–0.4)) — not for decoration but for physical lift above the color surface.

## Slide Application Notes
- **Title Slides:** Single Cormorant Garamond headline at 48–60px, weight 300, rgba(255,255,255,0.85), centered. Italic sub-line at 14px, rgba(255,255,255,0.5). Section number in 10px, 0.4em tracking, rgba(255,255,255,0.45), placed above the headline with 40px margin. Let the color fields occupy 100% of the canvas — no additional background or frame.
- **Content Slides:** Center-aligned content column at max-width 600px. Body text at 13px, 2.4 line-height, rgba(255,255,255,0.55). Use a centered tags/keywords line with dot separators (·) in rgba(255,255,255,0.25) to create a floating annotation layer below the body. The mid-field sienna zone should be visible on either side of the text column.
- **Data/Chart Slides:** This style is not well-suited for dense data visualization. If data must appear, present it as a single large figure or ratio in Cormorant Garamond at display size, with a supporting annotation in italic at 14px. Avoid bar charts or line graphs entirely — instead use text-based data presentation (comparative statements, key metrics only).
- **Closing Slides:** Reduce to a single closing phrase at maximum display size, weight 300, rgba(255,255,255,0.85). Below it, an italic attribution or provenance line at rgba(255,255,255,0.4). The three color fields should be the lasting visual memory — let the closing text echo quietly within them.
- **Do:** Preserve the three-band color structure on every slide; apply text-shadow to all type; keep the content column narrow and centered so the color fields breathe around it.
- **Don't:** Add any geometric graphic elements, icons, or borders — they destroy the atmospheric quality; use bold or heavy type weights; introduce any color outside the established warm-to-cool palette.
