---
name: Minimal Corporate
category: pencil-builtin
suitable_for: slides
source: web-04-minimalcorporate_light
---

# Minimal Corporate

## Visual Direction
A system of structural extremes: the deck opens on near-black (#0A0A0A) and progressively lightens through the content sequence, arriving at pure white or near-white (#f7f8fa) by the final slides. This dark-to-light vertical flow is the system's primary narrative device — darkness signals entry and authority; lightness signals openness and possibility. A single font family (Geist) handles everything, with Inter reserved exclusively for tab labels. The restraint is absolute: zero shadows, zero gradients, zero decorative elements. What remains is pure structure — 80px uniform padding, precise type sizing, and a single muted steel blue (#4A9FD8) accent that appears rarely and only to mark interaction or primary action. The restraint itself becomes the identity.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Dark Surface | #0A0A0A | Near-black — title slides, opening sections, strong emphasis |
| Light Surface | #FFFFFF | Pure white — main content backgrounds in later slides |
| Alt Surface | #F7F8FA | Cool near-white — secondary content areas, alternating backgrounds |
| Text on Dark (Primary) | #FFFFFF | White text on dark surfaces |
| Text on Dark (Secondary) | #CCCCCC | Dimmed white for supporting text on dark backgrounds |
| Text on Light (Primary) | #1A1A1A | Near-black text on light surfaces |
| Text on Light (Secondary) | #666666 | Mid-gray for supporting text on light backgrounds |
| Accent | #4A9FD8 | Muted steel blue — CTAs, links, interactive elements, single highlights |

## Typography

### Display Font
- **Family:** Geist
- **Weights:** 600 (medium-large titles, section headings), 500 (standard headlines)
- **Size Range:** 44–60px for slide titles (500–600), 24–36px for section headings (600), 18–22px for feature titles (600)
- **Letter Spacing:** -1px on headlines 40px and above; 0 default at smaller sizes
- **Style Notes:** Geist's clean geometric character maintains legibility at all sizes. The -1px tracking at display sizes tightens the headline without compression. Never use Geist Mono for slide content — the proportional Geist only.

### Body Font
- **Family:** Geist
- **Weights:** 400 (body copy, descriptions)
- **Size Range:** 14–17px for body copy, 12–13px for captions and metadata
- **Line Height:** 1.6 for body paragraphs, 1.4 for compact stacks

### Data/Mono Font (if applicable)
- **Family:** Geist
- **Weights:** 600 (featured metrics), 400 (secondary figures)
- **Usage:** KPIs and large metrics use Geist 600 at 40–56px. No special mono treatment — Geist's clean figures serve numerical data well. Accent blue (#4A9FD8) on the single most important metric per dark-surface slide.

## Design Principles
1. The dark-to-light flow is the narrative — opening slides use #0A0A0A; middle content uses white or #f7f8fa; the progression itself communicates structural movement through the presentation.
2. Single font, total discipline — Geist governs every text element (Inter the sole exception for tab labels). Hierarchy is weight and size, never font variety.
3. 80px padding is inviolable — uniform generous padding on all four sides of every slide. This creates the extreme whitespace that makes the restraint legible as a design choice.
4. Zero decoration policy — no shadows, no gradients, no ornamental dividers, no background textures. If an element has no informational purpose, it does not exist.
5. The accent earns its place — #4A9FD8 appears on at most one element per slide. Its rarity is what makes it function as a true visual anchor.

## Slide Application Notes
- **Title Slides:** Full #0A0A0A background, Geist 600 title in white at 52–60px (-1px tracking). Subtitle in Geist 400 #CCCCCC at 18–20px. 80px minimum margins. Accent blue used on one supporting element only (tag, category label, or underline rule).
- **Content Slides:** White (#FFFFFF) or alt (#F7F8FA) backgrounds. Geist 500–600 section titles in #1A1A1A. Body in Geist 400 #1A1A1A. 80px padding on all slides. Structural dividers are 1px #E0E0E0 lines, nothing heavier.
- **Data/Chart Slides:** Light backgrounds (#FFFFFF or #F7F8FA). Geist 600 primary metric at 44–56px in #1A1A1A. Accent blue (#4A9FD8) on the single headline figure. Chart lines and bars in #1A1A1A primary, #666666 secondary, and #4A9FD8 for the key series.
- **Closing Slides:** Return to dark (#0A0A0A) or use pure white depending on desired closing tone. Geist 500–600 statement in appropriate contrast. Accent blue CTA element (8px radius button or pill if interactive context applies).
- **Do:** Honor the 80px padding rule absolutely. Use the dark-to-light progression as a deliberate narrative arc across the full deck.
- **Don't:** Add any shadow, gradient, or decorative element of any kind. Use accent blue on more than one element per slide. Deviate from the Geist-only rule except for explicit tab labels.
