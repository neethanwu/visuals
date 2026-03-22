# Slides

Agent Skill to build stunning presentations in single-page HTML, with 32 curated design styles, interactive effects, and smart style inference.

## What it does

Give it your content (or just a topic) and it builds a complete, self-contained HTML presentation. One file, opens in any browser, no build step.

The skill picks the right design style, fonts, colors, animations, and effects based on your content — so you don't need to know anything about design. It handles everything from a quick 5-slide pitch to a 40-slide keynote.

## Install

```bash
npx skills add https://github.com/neethanwu/slides --skill slides
```

## Usage

You can trigger the skill anytime — with a direct command, mid-conversation, or whenever you have something worth presenting:

```
/slides My startup pitch for an AI-powered design tool
```

```
/slides Turn my notes into a presentation
```

```
I've been researching market trends all morning... let's turn this into slides
```

The skill picks up context from your conversation. If you've been working on content, research, or an outline with Claude, it uses what's already there — no need to repeat yourself. Just say "make slides" whenever you're ready.

## What's inside

### 32 Design Styles

From minimal Swiss typography to bold neon-on-dark to warm editorial — each style defines colors, fonts, spacing, layout rules, and do/don't guidelines.

A few examples:

- **Editorial Financial** — warm parchment, newspaper grid, authoritative serifs
- **Dark Classy** — premium dark mode, warm orange accent, editorial serif titles
- **Bold Signal** — neon lime on black, condensed type at extreme scale, high energy
- **Swiss Clean** — Zurich-school precision, vivid red accent, geometric rigor
- **Nordic Brutalist** — warm cream + charcoal, terracotta accent, heavy borders

The skill matches your content to the best style automatically. Data-heavy content gets an editorial style. A product launch gets Bold Signal. A corporate report gets Swiss Clean. You can also ask for a specific mood and the skill will narrow it down.

### 50 Font References

Curated heading + body + monospace combinations (including the Geist family) loaded via Google Fonts. The skill cross-references fonts with styles for the best pairing.

### Interactive Effects

Not just static slides — the skill can add:

- Entrance animations and slide transitions
- WebGL shader backgrounds (noise fields, aurora bands, particle drift)
- GSAP-powered staggered reveals and counter animations
- CSS techniques like frosted glass, neon glow, text stroke, clip-path reveals
- Three.js 3D particle fields and scenes

Effects are matched to the style. A minimalist deck gets subtle fades. A futuristic deck gets particle fields. A corporate deck gets nothing extra — restraint is a feature.

### Data Visualization

Charts and data are styled to match the deck — not default Chart.js blue. Supports:

- Chart.js for standard charts (bar, line, pie, doughnut)
- D3.js for custom editorial-quality visualizations
- Styled tables, KPI cards, and metric displays

### On-Brand Support

Provide your logo, brand colors, or brand fonts and the skill adapts the chosen style to your brand identity.

## How it works

The skill doesn't follow a rigid step-by-step wizard. It assesses what you already have — content, files, conversation context — and fills in the gaps:

- **Have full content?** It picks a style and builds.
- **Have a topic only?** It helps structure your content first.
- **Have existing slides to improve?** It reads them and enhances.
- **Have nothing?** It asks what the presentation is about.

Design decisions (style, colors, fonts, animations) are inferred from your content. The skill only asks you when there are genuinely multiple strong options — and even then, it presents 2-3 choices in plain language, not technical specs.

## Output

A single `.html` file that:

- Opens in any modern browser
- Uses Reveal.js for navigation, keyboard controls, and speaker notes
- Loads fonts and libraries from CDN — no local dependencies
- Contains all styles and scripts inline — fully self-contained
- Supports presenter mode (press `S` for speaker notes)

## Design Polish

The skill automatically installs [impeccable.style](https://impeccable.style/) on first run. Every deck gets a final design upgrade with `/polish`, `/animate`, and `/delight` before delivery — fixing alignment, enhancing motion, and adding moments of personality.

## License

MIT
