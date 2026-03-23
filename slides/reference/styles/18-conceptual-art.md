---
name: Conceptual Art
category: aesthetica
suitable_for: slides
---

# Conceptual Art

## Visual Direction
Conceptual Art presentation style takes its cue from Lawrence Weiner, Joseph Kosuth, and Sol LeWitt: the idea is the work, and the visual apparatus should recede as far as possible to let language carry full weight. The background is near-white (#fafaf8) — not pure white, but the slight warmth of a gallery wall. IBM Plex Mono is the sole typographic system, positioning content as instruction, documentation, or proposition rather than persuasion. Text is set at unexpectedly small sizes with extreme sparsity — vast margins, 56px gaps between sections, 2.4 line-height — so that each element feels deliberately placed and fully considered. The overall effect is rigorous, cerebral, and uncomfortably honest.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #fafaf8 | Off-white with a trace of warmth, gallery wall quality |
| Text Primary | #333333 | Dark grey for main statements — not pure black, slightly receded |
| Text Emphasis | #111111 | Near-black for strong-weighted keywords within statements |
| Text Body | #888888 | Mid-grey for supporting prose and statements |
| Text Muted | #ccc | Light grey for metadata, labels, footnotes, and section numbers |
| Border | #dddddd | Hairline rule for left-border statement blocks |
| Grid Separator | #eeeeee | Very light rule for concept grid top borders |

## Typography

### Display Font
- **Family:** IBM Plex Mono
- **Weights:** 300 (Light), 600 (SemiBold)
- **Size Range:** 24–40px
- **Letter Spacing:** Default monospace (no modification)
- **Style Notes:** Headlines are not large — the conceptual register comes from understatement. Light weight (300) for the full statement; bold/strong inline for the key term. Line-height 1.6 allows the proposition to unfold across multiple lines.

### Body Font
- **Family:** IBM Plex Mono
- **Weights:** 300 (Light)
- **Size Range:** 12–13px for slides
- **Line Height:** 1.9–2.4

### Label Font
- **Family:** IBM Plex Mono
- **Weights:** 500
- **Size Range:** 8–10px
- **Letter Spacing:** 0.35–0.4em
- **Style Notes:** All-caps with extreme wide tracking; used for section numbers and concept grid labels; color #ccc — labels identify without asserting

## Design Principles
1. The proposition is the design: formulate every headline as a complete, declarative statement rather than a noun phrase or fragment.
2. Extreme negative space is structural — 56px margins between every content zone signal that what is present is chosen, not filled.
3. A single 1px left-border rule in #ddd on indented statement blocks is the only graphic device allowed; it functions as a quotation mark.
4. Hierarchy is built through weight contrast within a single typeface: light (300) for context, semibold (600) inline for the operative term.
5. The concept grid (2-column, 1fr/1fr) breaks information into minimal label/value pairs — not bullet points, but dictionary-style entries.

## Slide Application Notes
- **Title Slides:** A single IBM Plex Mono statement at 24–40px, weight 300, color #333, line-height 1.6. The key term within the statement is wrapped in `<strong>` — weight 600, color #111. No decorative elements. Section number in 9px, letter-spacing 0.4em, color #ccc, positioned above with 56px margin below.
- **Content Slides:** Statement (indented, left-border rule, #888, 2.4 line-height) followed by a 2-column concept grid. Each grid item has a top rule in #eee, an 8px all-caps label in #ccc, and a 12px value in #777 at weight 300. Maintain the 56px rhythm between all content blocks.
- **Data/Chart Slides:** Label all data as propositions: not "Revenue Q3" but "Revenue in Q3 exceeded prior period by 12%." Use pure monochrome fills (#333, #888, #ccc, #eee). Avoid any chart chrome — no borders, legends, or backgrounds. Data should read as documentation.
- **Closing Slides:** A single terminal statement, no larger than the opening headline. Below it, a 10px monospace footer in #ccc with italic weight, functioning as a provenance line or instruction note (e.g., "This presentation was produced on [date]. It is subject to revision.").
- **Do:** Write complete sentences in headlines; use extreme sparsity — resist the impulse to fill empty space; treat the monospace font as the only voice in the entire deck.
- **Don't:** Add any imagery, icons, or graphical fills; use a sans-serif or serif typeface anywhere; increase font sizes to "readable from the back of the room" — this style privileges intimate, deliberate reading.
