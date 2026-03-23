---
name: Nordic Brutalist Bold
category: pencil-builtin
suitable_for: slides
source: webapp-03-nordicbrutalist_light
---

# Nordic Brutalist Bold

## Visual Direction
An evolved, more assertive take on the Nordic Brutalist language. Where the original leans warm and measured, this variant goes constructivist — 64px display titles with -2px tight tracking, aggressive dark inversions for hero cards and table headers, and borders wielded as bold structural dividers at 2–4px. The palette retains the cream-and-charcoal core but intensifies the terracotta accent (#C45A3B) and introduces olive green (#6B8E5E) for a palette that feels earthy and forceful. Navigation numerals (01, 02, 03) and bold section anchors reinforce a systematic, almost editorial rhythm. The single exception to square corners is the active navigation indicator, which takes 8px radius to mark interactivity — everything else remains razor-edged.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #F5F2ED | Warm cream — primary slide canvas |
| Text Primary | #1A1A1A | Near-black for all primary text and borders |
| Accent | #C45A3B | Terracotta — heightened intensity vs. v1, used for active states and key callouts |
| Success / Positive | #6B8E5E | Olive green — positive data, growth indicators |
| Border | #1A1A1A | Same as text; borders and type read as one unified system |
| Card Active Nav | — | 8px radius only; all other surfaces are 0px |

## Typography

### Display Font
- **Family:** Space Grotesk
- **Weights:** 700 (headlines, display numerals, titles)
- **Size Range:** 56–72px for hero/title slides, 36–48px for section titles, 20–28px for card headings
- **Letter Spacing:** -2px on display sizes (56px+); +1px on section labels; +3px on logo/wordmark
- **Style Notes:** Tight negative tracking at display sizes creates monumental, poster-like weight. Pair with generous white space around the title to let the tracking breathe. ALL-CAPS for section labels and category tags only — headline titles use title case.

### Body Font
- **Family:** Inter
- **Weights:** 400 (body copy, descriptions, metadata)
- **Size Range:** 13–16px body, 11–12px captions
- **Line Height:** 1.6 for body blocks, 1.4 for metadata stacks

### Data/Mono Font (if applicable)
- **Family:** Space Grotesk
- **Weights:** 700
- **Usage:** All KPIs, large percentage figures, and data callouts. -2px tracking on numbers 40px and above for a dense, impactful read.

## Design Principles
1. Title scale is monumental — 64px+ display titles with -2px tracking are the signature of this system; never reduce for comfort.
2. Dark inversions are structural, not decorative — use #1A1A1A fields for hero cards, table headers, and full title slides to create sharp value contrast.
3. Borders double as content — 2px borders define columns, rows, and hierarchical zones; 4px borders mark the slide's single most important element.
4. The 8px exception is deliberate — the only rounded element marks active/selected states, making interactivity instantly readable.
5. Letter-spacing is directional — negative tracking (-2px) pulls headlines inward for power; positive tracking (+1–3px) pushes labels outward for legibility at small sizes.

## Slide Application Notes
- **Title Slides:** Full dark inversion (#1A1A1A bg), Space Grotesk 700 title at 64–72px with -2px tracking, cream text. Terracotta used for a single underline stroke or block beneath the subtitle line.
- **Content Slides:** Cream background, charcoal section labels in ALL-CAPS 14px with +1px spacing. Card containers with 2px #1A1A1A borders, no radius. Dark-inverted card variants for the primary stat or hero callout.
- **Data/Chart Slides:** Dark-inverted table headers (#1A1A1A rows with cream text). Terracotta for the primary data series, olive green for comparative/positive series. Space Grotesk 700 for all numeric labels.
- **Closing Slides:** Return to full dark inversion. Single large headline (64px, -2px tracking). Terracotta accent on the CTA element or a 4px border framing the closing statement.
- **Do:** Push display sizes large and lean on negative tracking. Use dark inversions to anchor the eye to the most critical content zone on any slide.
- **Don't:** Apply 8px radius to anything other than the single active nav indicator. Use terracotta for more than one element per slide.
