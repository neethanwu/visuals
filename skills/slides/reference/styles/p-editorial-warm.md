---
name: Editorial Warm
category: pencil-builtin
suitable_for: slides
source: web-02-editorialwarm_light
---

# Editorial Warm

## Visual Direction
A bento grid architecture where the entire slide is a master container — warm gray (#C5BEB6) serves as the gap material between cards, making every slide feel like a curated collection of editorial tiles rather than a flat page. The default card fill is a rich warm cream (#F3EBE2), evoking handmade paper or a linen background. Against this, three carefully chosen cool pastel accent fills (sage-teal #C3DED8, periwinkle-gray #C4CFDE, and muted olive #D5DCBA) provide color variation without visual temperature clash. A decorative terracotta-coral (#D4916E) appears as a mesh gradient element, illustrating organic warmth without being a semantic accent. Funnel Sans is the single typeface across all functions, with hierarchy built entirely from weight (400 headlines, 500 nav, 700 CTAs) and scale. Corner radii of 16–20px on cards and 50%+ on decorative visual frames give the system its signature soft, approachable roundness.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Outer Frame / Gap | #C5BEB6 | Warm gray — the bento grid gap that surrounds all cards |
| Default Card | #F3EBE2 | Warm cream — primary card fill for most content blocks |
| Accent Card 1 | #C3DED8 | Sage teal — cool pastel accent for variety or emphasis cards |
| Accent Card 2 | #C4CFDE | Periwinkle gray — cool neutral pastel for secondary accent cards |
| Accent Card 3 | #D5DCBA | Muted olive — warm-cool bridge, charts or supporting data cards |
| Text Primary | #1A1A1A | Near-black — primary type on all card surfaces |
| Text Secondary | #3D3D3D | Dark gray for secondary copy with more warmth than #555 |
| Text Tertiary | #6B6B6B | Medium gray for captions, timestamps, metadata |
| Decorative | #D4916E | Terracotta coral — mesh gradient decorative elements only |

## Typography

### Display Font
- **Family:** Funnel Sans
- **Weights:** 400 (display headlines — the signature lightness of this system's large text)
- **Size Range:** 44–60px for slide titles (400), 28–36px for section headings (400–500)
- **Letter Spacing:** -0.5 to -1px on hero headlines (44px+); standard tracking on mid-size headings
- **Style Notes:** Funnel Sans 400 at display sizes creates an editorial warmth — it is confident without aggression. Hero headlines with slightly negative tracking (-0.5 to -1px) feel measured and refined. Never use heavy weight (700) for headlines; that weight belongs to CTAs and action elements only.

### Body Font
- **Family:** Funnel Sans (same family — single-font system)
- **Weights:** 500 (navigation labels, metadata, card labels), 400 (body copy and descriptions)
- **Size Range:** 13–16px body (400), 11–14px labels (500)
- **Line Height:** 1.65 for body copy to match the generous, airy card interiors

### Data/Mono Font (if applicable)
- **Family:** Funnel Sans
- **Weights:** 700 (large featured metrics treated as CTA-weight elements)
- **Usage:** Key metrics and KPIs. Set at 40–56px in Funnel Sans 700 — the bold weight reserved for these moments creates an implicit emphasis hierarchy (only metrics and CTAs use 700). +1–2px tracking on uppercase micro labels (e.g., unit labels beneath metrics).

## Design Principles
1. The bento grid is the layout system — slides are not open canvases; they are grids of cards separated by warm gray (#C5BEB6) gaps of 8–16px. Every content element lives inside a card.
2. Roundness signals approachability — 16–20px card radius is a consistent commitment; 50%+ on circular decorative frames creates focal softness. This is not a hard-edged system.
3. Single font, three weights — Funnel Sans at 400 (editorial), 500 (navigational), and 700 (action). Case and size create all remaining hierarchy; font-switching is never needed.
4. Cream is default, pastels are accents — most cards are warm cream (#F3EBE2); the three pastel fills (#C3DED8, #C4CFDE, #D5DCBA) appear for variety, emphasis, or functional differentiation — typically no more than one per slide.
5. Decorative warmth is isolated — the terracotta-coral (#D4916E) appears only as a mesh gradient in decorative circular/blob elements, never as a text color, border, or semantic indicator.

## Slide Application Notes
- **Title Slides:** Warm gray outer frame (#C5BEB6) with a large cream card (#F3EBE2, 20px radius) centered or spanning the inner area. Funnel Sans 400 title at 52–60px (-1px tracking). One accent pastel card (typically sage-teal) for the subtitle or category label. Decorative terracotta mesh gradient element in a corner or background position.
- **Content Slides:** Bento grid layout — multiple cream and pastel cards in an 8–16px warm gray grid. Funnel Sans 500 card labels at top of each tile. Body copy in 400 at 14–15px. One pastel accent card per slide maximum for visual emphasis.
- **Data/Chart Slides:** Cream or muted olive (#D5DCBA) card backgrounds for chart containers. Funnel Sans 700 at 44–52px for primary KPI. Muted olive cards work particularly well for numerical data tiles. Chart fills use the pastel palette rather than arbitrary colors.
- **Closing Slides:** Full-width cream card with generous padding inside the warm gray frame. Funnel Sans 700 CTA text at 20–24px. Funnel Sans 400 closing statement at 44–52px (-1px). Decorative terracotta element for visual warmth in the closing moment.
- **Do:** Structure every slide as a bento grid — even single-content slides should have the warm gray outer frame and at least one rounded card container. Use 16–20px radius consistently.
- **Don't:** Use decorative terracotta (#D4916E) as a text color, semantic indicator, or border. Use more than one pastel accent fill per slide — too many warm-cool combinations undermine the calm editorial tone. Apply negative tracking to body text (only headlines 44px+ get it).
