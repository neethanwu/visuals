---
name: Neo-Brutalism
category: aesthetica
suitable_for: slides
---

# Neo-Brutalism

## Visual Direction
Digital brutalism with a candy-coated palette: the raw structural vocabulary of offset drop shadows, heavy borders, and maximum contrast applied to a warm cream ground (#f5e6c8) and a cast of saturated pastel fills. Everything has a 3px solid #1a1a1a border. Every interactive or card element has a hard offset box-shadow of 6px 6px 0 #1a1a1a — no blur, no spread, just a displaced black duplicate. The section number badge is the clearest statement of the style: #ff6b35 (orange) fill, white text, 3px black border, 4px offset shadow. Typography is Space Mono — monospaced, technical, unapologetically flat — paired with DM Sans for body text. The four card colors (mint green #a8e6cf, peach #ffd3b6, sage #dcedc1, coral #ffaaa5) give the otherwise harsh system its neo quality: brutal structure, playful palette.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #f5e6c8 | Warm cream — the brutalist canvas |
| Text Primary | #1a1a1a | Near-black; used for all typography and all borders |
| Orange Accent | #ff6b35 | The badge/button color — punchy, high-contrast against cream |
| Card: Mint | #a8e6cf | Green pastel — card background option 1 |
| Card: Peach | #ffd3b6 | Orange-peach pastel — card background option 2 |
| Card: Sage | #dcedc1 | Yellow-green pastel — card background option 3 |
| Card: Coral | #ffaaa5 | Pink-coral pastel — card background option 4 |
| White Tag | #ffffff | Tag/chip background — pure white against the cream field |
| Card Text | #333333 | Dark grey for body text inside cards |

## Typography

### Display Font
- **Family:** Space Mono
- **Weights:** 700
- **Size Range:** 52–110px; clamp(52px, 7vw, 110px)
- **Letter Spacing:** Default monospace spacing (no adjustment)
- **Style Notes:** All-caps always. Line height 0.85 — maximum stacking compression. The headline reads as a raw industrial stamp. Section number uses Space Mono 700 in the orange badge at 11px, 0.15em tracking, uppercase.

### Body Font
- **Family:** DM Sans
- **Weights:** 400
- **Size Range:** 13px (card body), 10px (card titles and tags)
- **Line Height:** 1.7 (card body)
- **Style Notes:** Card titles use Space Mono 700 at 10px uppercase with 0.15em tracking, followed by a 2px solid #1a1a1a bottom border at 8px padding. Tags/chips use Space Mono 700 at 10px uppercase with 2px borders.

## Design Principles
1. The hard offset shadow (6px 6px 0 #1a1a1a, no blur) is the system's defining structural element — every card, every badge, every interactive element carries it.
2. Borders are always 3px solid #1a1a1a — never 1px hairlines, never rounded, never colored.
3. The pastel card fills (mint, peach, sage, coral) provide the "neo" — without them, this becomes plain brutalism. Use all four in a 2×2 grid for variety.
4. Type and borders do all the work — no gradient fills, no drop shadows with blur, no rounded corners anywhere.
5. Tags and chips are standalone structural objects: white fill, 2px black border, uppercase Space Mono. They function as labels and navigation anchors simultaneously.

## Slide Application Notes
- **Title Slides:** All-caps Space Mono headline at maximum size. Orange badge containing the section number at top left. Header group aligns the badge and headline at their baselines with a 28px gap.
- **Content Slides:** 2×2 card grid with 16px gaps. Each card: 24px padding, 3px border, 6px offset shadow, one of the four pastel fills. Card title in Space Mono 700 10px uppercase with a 2px border-bottom. Card body in DM Sans 400 13px.
- **Data/Chart Slides:** Replace cards with a data table using the same border system. Table header row: Space Mono 700 uppercase, 2px bottom border in #1a1a1a. Each row uses alternating card fills (mint / peach) to distinguish rows without traditional zebra striping.
- **Closing Slides:** All-caps headline at full size. A row of tag chips below listing key takeaways. Orange badge in the corner. No other elements.
- **Do:** Keep the 6px offset shadow on every card and badge; use all four pastel colors in layouts with multiple cells; maintain the 3px border weight consistently.
- **Don't:** Apply border-radius anywhere; use drop shadows with blur; mix in light or thin font weights; reduce borders below 2px.
