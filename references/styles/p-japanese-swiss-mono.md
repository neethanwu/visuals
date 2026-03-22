---
name: Japanese Swiss Monochrome
category: pencil-builtin
suitable_for: slides
source: mobile-01-japaneseswiss_light
---

# Japanese Swiss Monochrome

## Visual Direction
The rarest and most demanding aesthetic in this library: a system where emptiness is the primary design material. Drawing equally from Japanese Ma (negative space as active presence) and Swiss International Typographic Style (grid discipline, function over ornament), this system uses a single typeface (Inter) in three weights across an almost-achromatic palette. Color appears only when it carries semantic meaning — green for positive, red for negative — never for decoration. The canvas is a cool near-white (#F5F5F5); cards are pure white; text is pure black (#000000). Hairline elements define the aesthetic: 8px dots, 4px bars, 1px borders. Wide-tracked uppercase labels (+2px) provide the Swiss editorial rhythm. Inter Light 300 at large display sizes creates a whispered-elegance effect — headlines that float rather than shout.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #F5F5F5 | Cool near-white canvas — not pure white, a fraction warmer |
| Card Surface | #FFFFFF | Pure white — cards lift slightly from the background |
| Text Primary | #000000 | Pure black — maximum typographic contrast |
| Text Secondary | #999999 | Mid-gray for supporting text and metadata |
| Tertiary | #C4C4C4 | Light gray for captions, dividers, and subordinate labels |
| Border | #E5E5E5 | Near-invisible hairline borders for card definition |
| Positive | #34A853 | Google Material green — positive data values only |
| Negative | #D93025 | Google Material red — negative data values only |

## Typography

### Display Font
- **Family:** Inter
- **Weights:** 300 (display headlines — the signature weight of this system)
- **Size Range:** 48–64px for slide titles (Light 300), 28–36px for section headings (Light 300)
- **Letter Spacing:** -2px on large metrics (48px+) for density; +2px on ALL-CAPS section labels (Swiss editorial convention)
- **Style Notes:** Inter 300 at large sizes creates deliberate lightness — the headline barely touches the canvas, which amplifies the surrounding negative space. Never use bold or semibold for primary titles; the fragility of the light weight is the intended effect.

### Body Font
- **Family:** Inter
- **Weights:** 400 (body copy, descriptions), 500 (labels, metadata, navigation items)
- **Size Range:** 13–16px body (400), 11–14px labels (500)
- **Line Height:** 1.65 for body — generous, matching the overall spaciousness of the system

### Data/Mono Font (if applicable)
- **Family:** Inter
- **Weights:** 300 (large display metrics), 500 (small inline metrics)
- **Usage:** Large KPIs use Inter 300 at 48–64px with -2px tracking — they float like a whisper. Positive values colored #34A853; negative values #D93025. All other values in #000000.

## Design Principles
1. Negative space is load-bearing — every element on a slide should have at least as much empty space around it as its own dimensions. The emptiness is not wasted space; it is the primary visual element.
2. Color is semantic, never decorative — #34A853 and #D93025 appear only to communicate positive/negative data meaning. They do not appear in backgrounds, borders, decorative bars, or any element without semantic purpose.
3. Hairline precision — borders are always 1px; accent bars are 4px; dot markers are 8px. Nothing heavier unless a specific structural hierarchy demands it.
4. Inter Light 300 earns its gravity — the display font weight is softer than body weight (400), which is unconventional; lean into this inversion. The headline floats; the body is the anchor.
5. The grid is invisible but absolute — all elements align to an invisible modular grid. Misalignment is not minimalism; it is error. The system's sophistication comes from grid perfection, not grid looseness.

## Slide Application Notes
- **Title Slides:** #F5F5F5 canvas, Inter Light 300 title at 56–64px in #000000, wide negative space margins (minimum 80px all sides). A single uppercase Inter 500 label (+2px tracking) in #999999 above the title marks the presentation category.
- **Content Slides:** White cards (#FFFFFF) on near-white canvas with 1px #E5E5E5 borders. Inter 500 ALL-CAPS label (+2px) as section marker. Body in Inter 400 at 14–15px. Generous internal card padding (32–40px).
- **Data/Chart Slides:** Inter Light 300 at 48–64px for primary KPI in #000000. Apply #34A853 or #D93025 only if the figure has positive or negative meaning. 4px accent bar before the figure label. Axis labels in Inter 500 10–11px.
- **Closing Slides:** Near-white canvas, Inter Light 300 closing statement at 48–56px, maximum white space. Single Inter 500 ALL-CAPS label (+2px) marks the slide type. Zero decorative elements.
- **Do:** Commit to extreme negative space — the system fails when crowded. Use weight and size to create hierarchy before reaching for any other device.
- **Don't:** Use color for anything other than semantic positive/negative data meaning. Use bold (700) or semibold (600) — the system's weight range is 300–500 only. Add decorative elements of any kind.
