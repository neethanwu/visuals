---
name: Neo-Classicism
category: aesthetica
suitable_for: slides
---

# Neo-Classicism

## Visual Direction
The grammar of ancient Greece and Rome, distilled into quiet authority. The ground is a warm stone-white (#f6f3ee) — the color of aged marble in soft light. All content is centered with extreme ceremony: the layout is a single column of text crowned by ornamental dividers, flanked by vertical column lines at 14% from each edge. Typography is split between Cinzel for display (evoking Roman inscriptions) and Cormorant Garamond for body (elegant, scholarly, italic). The gold-tan accent (#b4a078) functions like gilt lettering — used sparingly on dividers, labels, and decorative elements at low opacity. The overall mood is timeless gravitas: these slides invoke legacy, authority, and institutional permanence without ostentation.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #f6f3ee | Warm stone-white, marble-adjacent |
| Text Primary | #2c2620 | Deep warm brown-black for headlines |
| Body Text | #6a5e50 | Medium warm brown for italic body copy |
| Pillar Text | #7a6e60 | Slightly lighter warm brown for supporting text |
| Gold Accent | #b4a078 | The defining gilt tone — used at 15–55% opacity |
| Column Lines | rgba(180,160,120,0.15) | Very faint gold vertical rules |
| Divider | rgba(180,160,120,0.25) | Slightly more visible for horizontal ornamental rules |

## Typography

### Display Font
- **Family:** Cinzel
- **Weights:** 400 (headlines), 700 (section number labels)
- **Size Range:** 42–72px; clamp(42px, 5vw, 72px)
- **Letter Spacing:** 0.18em — wide, epigraphic, like text chiseled in stone
- **Style Notes:** Sentence case or small caps. Never all-lowercase. The wide letter spacing creates the Roman inscription effect. Section numbers use Cinzel 700 at 10px, 0.6em tracking, uppercase, in the gold accent at 55% opacity.

### Body Font
- **Family:** Cormorant Garamond
- **Weights:** 300 (body and apply notes), 600 (pillar labels)
- **Size Range:** 13–16px
- **Line Height:** 2.2 — stately, unhurried
- **Style Notes:** Body is always italic (font-style: italic). This is not an afterthought — italic Cormorant Garamond is the voice of the classical scholar. Pillar labels use Cinzel 9px, 0.35em tracking, uppercase.

## Design Principles
1. Symmetry is law: all primary content is centered; column lines flank the text at equal distances from each edge.
2. The gold accent (#b4a078) is used only as an echo, never as a focal color — it appears at 15–55% opacity, always subordinate to the warm black text.
3. Ornamental dividers (a hairline with a centered diamond ◆) mark transitions between content sections; they provide rhythm without weight.
4. Hierarchy is achieved through font-family switching (Cinzel vs. Cormorant) rather than size variation — the distinction feels qualitative, not loud.
5. Negative space around the centered column should feel like the space between columns in a portico.

## Slide Application Notes
- **Title Slides:** Cinzel headline centered, 42–72px, 0.18em letter spacing. Italic Cormorant subtitle below at 20px in gold at 60% opacity. A Greek-key meander SVG divider above the headline. Section number in a laurel-adjacent badge at top center.
- **Content Slides:** Centered single column, max-width 700px. Headline in Cinzel, body in italic Cormorant Garamond 300 at 16px/2.2. A three-column "pillars" grid for key points: Cinzel label at 9px + italic body text below each.
- **Data/Chart Slides:** Tables preferred over charts. Table headers in Cinzel 700 small caps; rows in Cormorant 300. Use the gold accent for header rule lines. Keep all values left-aligned within cells; total/summary rows in Cinzel.
- **Closing Slides:** A single Cinzel headline, a horizontal ornamental rule with ◆, and one line of italic Cormorant below. Column lines remain visible. No other elements.
- **Do:** Use the vertical column lines as a persistent framing device across all slides; maintain the warm tone of #f6f3ee as an inviolable background; set body text in italic Cormorant always.
- **Don't:** Use sans-serif fonts anywhere in this style; apply bright or saturated colors; break the centered axis with flush-left or flush-right text blocks.
