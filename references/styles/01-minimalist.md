---
name: Minimalist
category: aesthetica
suitable_for: slides
---

# Minimalist

## Visual Direction
Radical reduction to what is essential. This style operates on a warm off-white field (#fafaf8) with near-weightless typography — headlines set at weight 200, letter-spaced tight, at display scale. The visual language is governed by restraint: a single circle with a 1px border, hairline rules, and generous negative space do more communicative work than decoration ever could. For slides, this translates into wide breathing room between elements, a strict two-column or centered layout, and the courage to leave large areas empty. Every element earns its presence by necessity.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #fafaf8 | Warm off-white, slightly cream — not clinical |
| Text Primary | #1a1a1a | Near-black, soft; used for headlines and anchors |
| Text Secondary | #888888 | Medium grey for body copy |
| Text Tertiary | #aaaaaa | Light grey for trait labels and supporting text |
| Rule / Border | #eeeeee | Hairline dividers between list items |
| Accent Neutral | #bbbbbb | Section numbers, eyebrow labels |
| Subtle Lines | #f0f0f0 | Background cross-hair lines, near-invisible |

## Typography

### Display Font
- **Family:** Plus Jakarta Sans
- **Weights:** 200 (headline), 500 (labels)
- **Size Range:** 64–110px display; scales with clamp(64px, 7vw, 110px)
- **Letter Spacing:** -0.04em (tight, optical)
- **Style Notes:** Lowercase or sentence case preferred; no uppercase for headlines. Weight 200 creates the signature "almost there" lightness.

### Body Font
- **Family:** Plus Jakarta Sans
- **Weights:** 300 (body), 400 (traits/labels)
- **Size Range:** 11–14px
- **Line Height:** 2.0 (body); traits use uppercase at 11px with 0.15em letter spacing

## Design Principles
1. Every element must justify its inclusion — if it can be removed without loss of meaning, remove it.
2. White space is not empty; it is the primary visual element that creates emphasis.
3. Typography does all the expressive work: weight contrast between 200 and 500 creates hierarchy without color.
4. One accent element per composition — a single thin circle, a single hairline rule — anchors the eye.
5. Color palette stays within a monochromatic warm-neutral range; no hue-based accent colors.

## Slide Application Notes
- **Title Slides:** Large weight-200 headline at 80–110px, section label in small caps above, single hairline rule below. Vast empty field around text.
- **Content Slides:** Two-column grid with 120px gap. Left: headline + body at 14px/2.0. Right: trait list with 1px border-bottom dividers. Never fill the right column entirely.
- **Data/Chart Slides:** Charts use only #1a1a1a, #888, and #eee. No grid lines heavier than 1px. No fills, only strokes. Data labels in Plus Jakarta Sans 300.
- **Closing Slides:** One line of text, centered, weight 200, large size. Nothing else.
- **Do:** Use clamp() for responsive type sizing; maintain at least 80px padding on all edges; favor asymmetric balance.
- **Don't:** Add decorative borders, icons, or color blocks; never use font weight above 500; never center-align body copy.
