# Visuals

Agent skills for creating beautiful visual output — presentations, graphics, and more. Zero dependencies, single-file HTML, professional design quality.

## Install

```bash
npx skills add neethanwu/visuals --skill slides
```

## Skills

### slides

Give it your content (or just a topic) and it builds a complete, self-contained HTML presentation. One file, opens in any browser, no build step.

```
/slides A talk on how we scaled our API to 10M requests per day
```

```
/slides Turn my notes into a presentation
```

Or just say "make slides" mid-conversation — the skill picks up context from what you've been working on.

**37 design styles** — from Swiss typography to synthwave to glassmorphism to risograph. The skill matches your content to the best style automatically.

**49 font trios** — curated heading + body + mono combinations loaded via Google Fonts. The skill cross-references fonts with styles for the best pairing.

**Zero dependencies** — no framework. Pure HTML/CSS/JS with CSS scroll-snap. Natively responsive, works on desktop, tablet, and mobile.

**Interactive effects** — entrance animations, GSAP stagger, WebGL shaders, and style-specific effects (perspective grids, halftone dots, scan lines, gradient mesh). Effects are matched to the style — a minimalist deck gets subtle fades, a tech demo gets particle fields.

**Data visualization** — Chart.js, D3.js, styled tables, and KPI cards, all themed to match the deck.

**Smart inference** — design decisions (style, fonts, colors, animations) are inferred from your content. The skill only asks when there are genuinely multiple strong options, and presents choices in plain language — not technical specs.

### Coming soon

- **social** — graphics for social platforms (1:1, 16:9, 9:16) with PNG export
- **poster** — print-ready posters and flyers
- **on-brand** — brand asset management across all skills

## How it works

The skill doesn't follow a rigid wizard. It assesses what you already have — content, files, conversation context — and fills in the gaps:

- **Have full content?** It picks a style and builds.
- **Have a topic only?** It helps structure your content first.
- **Have existing slides?** It reads them and enhances.
- **Have nothing?** It asks what the presentation is about.

## Output

A single `.html` file with:

- Keyboard and touch navigation
- Entrance animations and smooth transitions
- Fragment support (click-to-reveal) for talks and lectures
- Responsive sizing via `clamp()` — scales from phone to projector
- All styles and scripts inline — fully self-contained

## License

MIT
