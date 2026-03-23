---
name: Swiss Elegant
category: pencil-builtin
suitable_for: slides
source: webapp-03-swisselegant_light
---

# Swiss Elegant

## Visual Direction
Swiss Elegant marries the structural discipline of Swiss typographic design with the warmth of editorial print publishing. The ivory background (#FAFAF7) replaces clinical white with a quality that feels like premium paper stock, and Cormorant Garamond's elegant serifs at dramatic sizes (64px+) introduce a cultural authority absent from pure sans-serif systems. The cardinal red accent is deeper and more refined than a typical brand red — it carries editorial weight rather than digital urgency. JetBrains Mono handles data with technical precision, while Inter bridges the editorial and functional layers in body copy. Hairline 1px borders and zero shadows complete the picture: this is a style for boardrooms, investor presentations, cultural institutions, and premium brand decks where sophistication signals competence.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #FAFAF7 | Warm ivory — paper-like, premium, non-clinical |
| Text Primary | #0F0F0F | Near-black with slight warmth |
| Text Secondary | #666666 | Medium gray for supporting content and captions |
| Accent | #C41E3A | Cardinal red — editorial authority, deeper than brand red |
| Border | #E0E0E0 | Hairline dividers — 1px only, never thicker |

## Typography

### Display Font
- **Family:** Cormorant Garamond
- **Weights:** 500 (medium) — the single weight used for all display text
- **Size Range:** 64–80px for titles, 40–52px for section headers, 28–36px for slide subtitles
- **Letter Spacing:** -2px at display sizes (64px+); -1px at section header sizes; 0px below 32px
- **Style Notes:** Italic is permitted for pull quotes and single-word editorial emphasis. Never bold (700+) — Cormorant's elegance lives in medium weight. The dramatic scale contrast between 64px titles and 10px metadata is intentional and essential.

### Body Font
- **Family:** Inter
- **Weights:** 400 (regular), 500 (medium)
- **Size Range:** 15–17px body copy, 11–12px captions, 10px metadata and footnotes
- **Line Height:** 1.6 for paragraphs, 1.4 for lists, 1.2 for tight metadata rows

### Data/Mono Font (if applicable)
- **Family:** JetBrains Mono
- **Weights:** 400 (regular)
- **Usage:** All numeric metrics, data table values, percentage callouts, timestamps, and technical annotations. Provides a deliberate stylistic contrast with the serif display type — the tension between Garamond and Mono is a feature, not a bug.

## Design Principles
1. Dramatic scale contrast is the primary tool of hierarchy. The gap between the largest type on a slide (64px+) and the smallest (10px metadata) should feel intentional and significant — compress this range and the elegance collapses.
2. The ivory background is not negotiable. It defines the warmth and materiality of the system. Pure white makes Cormorant look cold; #FAFAF7 makes it look printed.
3. Cardinal red appears once per slide, maximum. It is an editorial mark — a pull quote source, a critical number, a section marker — never a button color or a highlight tool.
4. Hairline 1px borders only. Any border heavier than 1px is structurally wrong for this style. Borders divide without shouting.
5. Zero shadows, zero gradients, zero rounded corners. Every softening element conflicts with the print-editorial sensibility that defines this style.

## Slide Application Notes
- **Title Slides:** Ivory background. Title in Cormorant Garamond 500 at 72–80px, flush-left, upper-center of the slide. A hairline 1px cardinal red rule (not black) beneath the title spanning 40% of the slide width. Subtitle or deck description in Inter 400, 16px, #666666. Presenter name/date in Inter 400, 10px, #666666, bottom-left.
- **Content Slides:** Single or two-column layout. Section label in Inter 500 uppercase, 10px, #666666, +1.5px tracking. Body in Inter 400, 16px, line-height 1.6. Pull quotes or key statements in Cormorant Garamond 500 italic, 28–36px, with a hairline left border in cardinal red.
- **Data/Chart Slides:** Chart title in Cormorant Garamond 500, 28px. Axis labels and data values in JetBrains Mono 400, 11–12px. Cardinal red for the primary data series only. All other series in #0F0F0F and #666666. Table headers in Inter 500 uppercase, 10px, +1px tracking, with a 1px bottom border in #E0E0E0.
- **Closing Slides:** Mirror the title slide structure. A single Cormorant Garamond 500 statement at 64px. Optional Cormorant italic pull quote at 28px in #666666. Hairline red rule. Contact details in JetBrains Mono 400, 11px, bottom-left.
- **Do:** Embrace the scale extremes. Use JetBrains Mono for every data point. Keep the ivory background sacred.
- **Don't:** Use bold weights in Cormorant. Add drop shadows. Use borders heavier than 1px. Place accent red on more than one element per slide.
