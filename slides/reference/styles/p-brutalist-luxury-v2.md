---
name: Brutalist Luxury Gold
category: pencil-builtin
suitable_for: slides
source: mobile-02-brutalistluxury_light
---

# Brutalist Luxury Gold

## Visual Direction
The purist's dark luxury system: a single font (Space Grotesk), all uppercase, on a near-black canvas, with gold (#D4AF37) as the sole chromatic event. Where Brutalist Luxury Dark employs the dramatic contrast of two typefaces, this variant achieves its power through radical reduction — one font, one accent, one rule: ALL-CAPS. The gold accent appears not just as a color but as a physical mark: 3×14px gold bars precede section labels as a systematic rhythmic device, creating a visual pulse across the slide deck. The tab bar (if rendered in a UI context) takes a 36px radius as the only exception to the zero-radius rule; all content surfaces are absolutely square. Letter-spacing swings between -1 to -2px at display sizes for compressed authority and +1 to +2px on ALL-CAPS labels for airy legibility.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #111111 | Near-black primary canvas |
| Surface | #1C1C1C | Card and content block backgrounds |
| Elevated | #282828 | Second-level surfaces, nested containers |
| Text Primary | #FFFFFF | Pure white — maximum contrast on dark |
| Text Secondary | #A0A0A0 | Mid-gray for metadata, supporting copy |
| Accent | #D4AF37 | Classic gold — richer and warmer than v1's matte gold |
| Border | #2A2A2A | Subtle structural borders between zones |

## Typography

### Display Font
- **Family:** Space Grotesk
- **Weights:** 700 (display titles, hero metrics), 600 (section headings, card titles), 500 (labels), 400 (body)
- **Size Range:** 52–72px for slide titles, 32–44px for section headings, 16–20px for card titles
- **Letter Spacing:** -2px at 52px+; -1px at 32–52px; +1–2px on ALL-CAPS labels (14px and below)
- **Style Notes:** ALL-CAPS is the default case treatment for this system. Title case is used only for long body sentences where readability demands it. Space Grotesk's geometric character holds well at all-caps, avoiding the stilted feel of all-caps serifs.

### Body Font
- **Family:** Space Grotesk (same family — single-font system)
- **Weights:** 400 (body copy), 500 (metadata, captions with slightly more presence)
- **Size Range:** 13–16px body, 11–12px captions
- **Line Height:** 1.6 for body paragraphs, 1.4 for metadata stacks

### Data/Mono Font (if applicable)
- **Family:** Space Grotesk
- **Weights:** 700
- **Usage:** All KPIs and large metric figures. Set in gold (#D4AF37) at 52–72px with -2px tracking. The gold-on-black combination with tight tracking creates an almost engraved, medallion-like quality for key numbers.

## Design Principles
1. One font rules — Space Grotesk at every level; hierarchy is communicated through weight (400–700), size, and case (UPPERCASE vs. sentence case), never through font-switching.
2. Gold bars are rhythm markers — the 3×14px gold vertical bars before section labels are systematic, not decorative. They appear before every section label without exception.
3. ALL-CAPS is the default mode — body paragraphs may use sentence case for pure readability; everything else (titles, labels, tags, metrics, CTAs) is uppercase.
4. Gold used maximally but not carelessly — unlike v1 where gold appears once, this system allows gold on all section markers and key metrics simultaneously, but never on body text or structural borders.
5. Negative tracking at scale creates authority — display sizes must use -1 to -2px tracking; optically spaced ALL-CAPS at large sizes reads as loose and weak.

## Slide Application Notes
- **Title Slides:** #111111 canvas, Space Grotesk 700 ALL-CAPS title at 64–72px (-2px tracking) in white. Gold 3×14px bar at upper-left before the presentation title label. Subtitle in Space Grotesk 400 sentence case at 18px.
- **Content Slides:** Surface cards (#1C1C1C) on base canvas, #2A2A2A border separation. Gold bar + ALL-CAPS Space Grotesk 600 (+1px) section label at top of each card. Body in Space Grotesk 400. Key metric or primary figure in gold 700.
- **Data/Chart Slides:** Primary KPI in Space Grotesk 700 gold at 56–72px (-2px). Secondary metrics in white 600. Chart labels in ALL-CAPS 12px +1px Space Grotesk 500. Elevated surfaces (#282828) for chart backgrounds.
- **Closing Slides:** Full #111111 canvas. Space Grotesk 700 ALL-CAPS closing statement at 64px (-2px). Gold bar + ALL-CAPS label marks the section type. Gold CTA button text on #1C1C1C button (zero radius).
- **Do:** Apply the 3×14px gold bar before every section label without exception — it is the system's visual signature. Use negative tracking at all display sizes.
- **Don't:** Apply the 36px tab radius to any content element. Mix case treatments arbitrarily — establish which elements are ALL-CAPS and be consistent throughout the deck.
