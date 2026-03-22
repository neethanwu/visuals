---
name: Editorial Financial
category: pencil-builtin
suitable_for: slides
source: web-03-editorialfinancial_light
---

# Editorial Financial

## Visual Direction
Editorial Financial is the visual language of financial journalism — The Financial Times, The Economist, Bloomberg. The system is built on a newspaper-grid architecture where 1px ruled lines divide the canvas into cells, each cell functioning as an independent editorial unit. The parchment background (#F4F2EF) is the foundational warmth that distinguishes this from generic business decks. Playfair Display operates at display sizes for headlines and large data callouts, while IBM Plex Mono — set uppercase throughout — carries all UI text, labels, and navigation. Geist handles body copy with clean neutrality. The navy and gold accents are conservative but distinctive: navy for institutional authority, gold for premium data callouts. This style is built for financial services, consulting, macroeconomic analysis decks, and any presentation where institutional credibility is the primary communication goal.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #F4F2EF | Warm parchment — the newspaper foundation |
| Text Primary | #1A1A1A | Near-black for maximum body legibility |
| Text Secondary | #4A4A4A | Dark gray for supporting copy and captions |
| Accent Navy | #384F84 | Institutional navy — authority, data headers, emphasis |
| Accent Gold | #C8B496 | Warm gold — premium data highlights, ruling accents |
| Border | #E5E0D8 | Warm parchment border — for cell dividers and ruled lines |

## Typography

### Display Font
- **Family:** Playfair Display
- **Weights:** 400 (regular), 700 (bold) — regular for editorial titles, bold for major data callouts
- **Size Range:** 56–72px for title slides, 36–48px for section headers, 48–64px for hero KPI callouts
- **Letter Spacing:** 0px default; never apply tight negative tracking — Playfair's letterforms require room
- **Style Notes:** Italic for editorial pull quotes and market commentary. Bold for hero numbers and decisive statements. The combination of Playfair italic at medium size alongside IBM Plex Mono uppercase labels is the visual signature of this system.

### Body Font
- **Family:** Geist
- **Weights:** 400 (regular)
- **Size Range:** 15–17px body copy, 12–13px supporting, 11px footnotes
- **Line Height:** 1.6 for paragraphs, 1.4 for structured lists

### Data/Mono Font (if applicable)
- **Family:** IBM Plex Mono
- **Weights:** 500 (medium), set in uppercase throughout
- **Usage:** All UI text, navigation labels, table headers, category markers, CTA text, axis labels, badges, and data identifiers. The uppercase monospace setting is the non-negotiable signature of this style — IBM Plex Mono lowercase is not used. Letter spacing: +1px for navigation and labels, +2px for CTA text.

## Design Principles
1. The newspaper grid is the structural foundation. All content is organized into cells defined by 1px ruled lines in the border color (#E5E0D8). These rules are structural load-bearing elements — they are not decorative dividers. Every piece of content lives in a cell.
2. IBM Plex Mono uppercase is the voice of the system. Every label, navigation item, table header, data tag, and CTA is set in IBM Plex Mono uppercase. This is non-negotiable — it is the single most distinctive element of this style and must be applied consistently.
3. Zero corner radius, completely flat. The newspaper metaphor requires sharp edges throughout. No rounding on any element — cards, tables, callout boxes, or CTA elements.
4. Parchment is the canvas, not just a background color. The #F4F2EF tone should be treated as the paper stock of a premium financial publication. It carries warmth that pure white cannot, and it makes the navy and gold accents read with greater depth.
5. Playfair and IBM Plex Mono create a deliberate tension. The serif-monospace duality is the editorial-financial voice — one carries cultural weight (Playfair), the other carries systematic precision (IBM Plex Mono). They should never be used interchangeably.

## Slide Application Notes
- **Title Slides:** Parchment background. A 1px horizontal ruled line in #E5E0D8 across the full width, positioned at 25% from the top (masthead rule). Title in Playfair Display 400 at 60–72px, #1A1A1A, flush-left below the rule. Volume/edition marker in IBM Plex Mono 500 uppercase, 10px, +1px tracking, #4A4A4A, above the masthead rule. Date and presenter in IBM Plex Mono 500 uppercase, 10px, bottom-left.
- **Content Slides:** Parchment background divided into columns by 1px ruled lines. IBM Plex Mono 500 uppercase, 10px column headers above each cell. Body in Geist 400, 16px. Pull quote in Playfair Display 400 italic, 22–28px, with a 1px left border in #C8B496 (gold).
- **Data/Chart Slides:** The chart lives within a cell defined by 1px parchment-border rules. Chart title in Playfair Display 700, 22–28px. Axis labels in IBM Plex Mono 500 uppercase, 10px. Data values in IBM Plex Mono 500, 13px. Primary data series in #384F84 (navy). Secondary in #C8B496 (gold). A horizontal 1px gold rule separates the chart title from the chart body.
- **Closing Slides:** Parchment background. Masthead rule at top. Playfair Display 400 italic closing statement at 48–56px. IBM Plex Mono 500 uppercase CTA at 12px, +2px tracking, flush-left below. Contact details in IBM Plex Mono 500 uppercase, 10px, #4A4A4A.
- **Do:** Use IBM Plex Mono uppercase for every UI text element. Divide content with 1px ruled lines. Treat the grid cells as editorial units. Use the parchment background on every slide.
- **Don't:** Round any corners. Use lowercase IBM Plex Mono. Apply navy or gold fills to large areas. Add drop shadows or gradients. Break the ruled-line grid structure.
