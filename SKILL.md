---
name: slides
description: Build beautiful single-file HTML presentations with professional design, animations, and interactive effects. Use when the user wants to create slides, a presentation, a deck, a pitch deck, a talk, a keynote, or a lecture. Triggers on "make slides", "build a presentation", "slide deck", "create a deck", "presentation about", "slides for my talk", "pitch deck for", "turn this into slides", "present this", "/slides". Also triggers when user has accumulated content (notes, outlines, research) and wants it turned into a visual presentation.
argument-hint: [topic or content]
effort: high
allowed-tools: Read, Write, Bash, Glob, Grep, Agent, AskUserQuestion
---

# Slides — Single-File HTML Presentation Builder

## Context Assessment

Before doing anything, assess what context already exists. Do NOT follow a rigid step-by-step wizard. Figure out what you have, what you need, and fill the gaps.

### Check for existing context

1. **Conversation history** — has the user been working on content, research, or an outline?
2. **Working directory** — are there markdown files, outlines, notes, or existing HTML slides?
3. **User arguments** — did they pass a topic, file path, or content directly?

### Determine what's missing

| If you have... | Then... |
|---|---|
| Full content + style preference | Build directly |
| Full content, no style preference | Infer style from content, confirm briefly, build |
| Topic only | Help structure content, then infer style, build |
| Existing HTML slides to improve | Read them, identify gaps, enhance |
| Nothing (bare `/slides` invocation) | Ask what the presentation is about |

## When to Ask vs When to Infer

**Only ask for what you genuinely cannot infer.** Most users don't know design terminology.

### Use `AskUserQuestion` when:

- **Content is missing or ambiguous** — you need the user's actual content, topic, or key points. Don't fabricate content.
- **Multiple strong style options exist** — present 2-3 choices with plain-language descriptions:
  > "Your content has a data-journalism feel. I see two directions:\n\n1. **Editorial Financial** — warm parchment tones, newspaper-grid layout, authoritative serif headlines\n2. **Editorial Data** — magazine-quality, italic headlines, monochromatic and restrained\n\nWhich feels right, or should I pick?"
- **User-provided assets** — ask if they have images, logos, data, or brand colors to incorporate.
- **Ambiguous audience/tone** — if content could go formal or casual and it affects style choice.
- **Refinement after first build** — ask what to adjust rather than guessing.

### Do NOT ask about:

- Hex colors, font names, animation easing, CSS values, or technical implementation details
- Which of 31 styles to use — curate for them
- Things you can infer from content (data-heavy → data-appropriate style)
- Things with a clear single best answer

When using `AskUserQuestion`, keep options to **2-3 max**. Describe in terms users care about (mood, feel, impression), not specs. Always include: "or should I just pick?"

## Content Structuring

### Slide types
- **Opening**: Title + subtitle/tagline + optional author/date
- **Section divider**: Bold section title + optional section number
- **Content**: Heading + body (text, bullets, two-column, image+text)
- **Data**: Heading + chart/table/metrics
- **Quote**: Large quote + attribution
- **Comparison**: Side-by-side columns
- **Code**: Syntax-highlighted code block + annotation
- **Image**: Full-bleed or framed image with caption
- **Closing**: Final message + CTA/contact/links

### Slide count
- Lightning talk (5 min): 5-8 slides
- Standard talk (15-20 min): 12-20 slides
- Keynote (30-45 min): 25-40 slides
- Pitch deck: 10-15 slides

One idea per slide. Dense slides lose audiences.

## Style Selection

31 curated design styles live in `references/styles/`. Read the chosen style file for its Color Palette, Typography, Design Principles, and Slide Application Notes. Apply with taste — they're guides, not rigid templates.

### Interpreting style files — terminology glossary

Style files use inconsistent terminology across the 31 files. Normalize when reading:

| You may see in a style file | Treat as | CSS custom property |
|---|---|---|
| Background, Canvas, Outer Frame | Background color | `--bg-color` |
| Surface, Card Surface, Elevated, Panel | Card/container background | `--surface-color` |
| Text Primary, Text Emphasis, Text Body (dark) | Primary text color | `--text-primary` |
| Text Secondary, Text Muted, Body Text | Secondary text color | `--text-secondary` |
| Accent, Accent Color, CTA, Emphasis | Primary accent | `--accent-color` |
| Border, Rule, Divider, Grid Line | Border color | `--border-color` |
| Positive, Success, Green | Positive semantic color | `--color-positive` |
| Negative, Danger, Red | Negative semantic color | `--color-negative` |
| Display Font, Headline Font | Display/heading typeface | `--display-font` |
| Body Font, Text Font, UI Font | Body typeface | `--body-font` |
| Data Font, Mono Font, Code Font | Monospace typeface | `--mono-font` |

Always map style file tokens to these CSS custom properties in your output. This keeps the HTML consistent regardless of which style file was used.

### How to choose

Infer from content. Do NOT present all 31 as a menu.

| Content type | Recommended styles |
|---|---|
| Startup pitch / product launch | p-bold-signal, p-minimal-corporate, p-dark-classy, p-swiss-clean |
| Financial / data-heavy | p-editorial-financial, p-editorial-data, p-swiss-elegant |
| Technical / engineering | p-bauhaus-digital, p-swiss-clean-expressive, 08-neo-brutalism |
| Creative / portfolio | 05-neo-expressionism, 16-contemporary-collage, p-monochrome-expressive |
| Corporate / formal | p-minimal-corporate, p-swiss-clean, p-editorial-calm |
| Academic / research | p-editorial-calm, p-swiss-elegant, 01-minimalist |
| Luxury / premium brand | p-elegant-luxury, p-brutalist-luxury, p-dark-classy |
| Futuristic / tech-forward | 07-neo-futurism, p-bold-signal, p-bauhaus-digital, p-dark-classy |
| Editorial / storytelling | p-editorial-warm, p-editorial-calm, p-industrial-humanist |
| Bold / high-impact | p-bold-signal, p-nordic-brutalist-v2, p-brutalist-luxury-v2, 08-neo-brutalism |
| Warm / approachable | p-editorial-warm, p-industrial-humanist, 01-minimalist |
| Elegant / refined | p-swiss-elegant, 12-art-deco, 06-neo-classicism |

Strong single match → just use it. Multiple equally good → `AskUserQuestion` with 2-3 visual descriptions.

## Font Selection

49 curated font trios (heading + body + mono) in `references/font-guide.md`. Cross-reference with the style rather than blindly using fonts hardcoded in style files.

**Important:** The font guide lists `npx shadcn` install commands — ignore those. For slides, load fonts via Google Fonts `<link>` tags. To convert a trio name to a Google Fonts URL, take the font family names from the trio and build: `https://fonts.googleapis.com/css2?family=Font+Name:wght@400;500;600;700&display=swap`

| Style mood | Strong trio matches |
|---|---|
| Editorial / serif authority | editorial, gazette, novel, literary |
| Swiss / geometric precision | swiss, creative, modern-clean, minimal |
| Brutalist / raw power | brutalist, poster, headline, dossier |
| Corporate / neutral clarity | corporate, document, technical, product |
| Luxury / premium | classic, folio, scholar, memoir |
| Warm / humanist | storyteller, journal, commons, health |
| Data / dashboard | dashboard, fintech, devtool, technical |
| Bold / condensed impact | headline, impact, poster, brutalist |

## References — Load on Demand

Do NOT read all references upfront. Load each **only when you need it**:

- Read `references/libraries.md` **first, always** — it has the CDN links and Reveal.js config you need to scaffold the HTML.
- Read `references/animations.md` **when choosing transitions and entrance animations** for the selected style.
- Read `references/effects.md` **when the style calls for background effects** (Neo-Futurism, Dark Classy, Color Field) or the user requests immersive/interactive visuals. Skip for restrained styles.
- Read `references/data-viz.md` **when the slide outline includes data, metrics, charts, comparisons, or tables**.
- Read `references/media.md` **when the user provides images, video, logos, or screenshots**, or the outline includes image/video slides.
- Read `references/elements.md` **when you need icons, code blocks, diagrams (Mermaid), decorative SVGs, or styled lists**.

## Building the HTML

Read `references/example-output.md` **before building your first deck in a session** — it's a complete working 5-slide example showing correct structure, load order, theming, chart rendering, and animations. Pattern-match against it, don't copy it verbatim.

### Output

Single self-contained `.html` file. Styles in `<style>`, scripts in `<script>`, libraries via CDN.

**Content sanitization:** When interpolating user-provided text into slides, escape `<script>`, `</style>`, and raw HTML tags in body content to prevent accidental breakage of the document structure.

### Structure (follow this exactly)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Presentation Title</title>

  <!-- 1. Google Fonts (MUST be first, before any CSS that references them) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=...&display=swap" rel="stylesheet">

  <!-- 2. Reveal.js CSS -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/theme/white.css">

  <!-- 3. Optional: Highlight.js theme CSS -->

  <!-- 4. Custom styles (MUST come after Reveal.js CSS to override it) -->
  <style>
    /* CSS custom properties from chosen style */
    :root {
      --display-font: 'Font Name', sans-serif;
      --body-font: 'Font Name', sans-serif;
      --mono-font: 'Font Name', monospace;
      --text-primary: #1A1A1A;
      --text-secondary: #777;
      --bg-color: #FAFAF7;
      --accent-color: #C41E3A;
      --border-color: #E0E0E0;
    }
    /* Override Reveal.js defaults — see Gotchas */
    .reveal { font-family: var(--body-font); color: var(--text-primary); }
    .reveal h1, .reveal h2, .reveal h3 { font-family: var(--display-font); }
    /* Animation keyframes */
    /* Slide-specific layouts */
  </style>
</head>
<body>
  <!-- Optional: background canvas for effects (z-index: 0) -->

  <div class="reveal">
    <div class="slides">
      <section><!-- slide --></section>
    </div>
  </div>

  <!-- 5. Reveal.js JS -->
  <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.js"></script>

  <!-- 6. Optional libs: GSAP, Chart.js, D3, Lucide, Mermaid, Highlight.js plugin -->

  <!-- 7. Optional: Three.js (importmap + module script, must be last) -->

  <script>
    // Reveal.js init
    Reveal.initialize({
      hash: true,
      transition: 'fade',
      transitionSpeed: 'default',
      backgroundTransition: 'fade',
      center: true,
      width: 1920,
      height: 1080,
      margin: 0.04,
      controls: true,
      progress: true,
      slideNumber: 'c/t',
    });

    // GSAP slide-change hook (if GSAP included)
    // Chart rendering on slide entry (if Chart.js included)
    // Lucide init (if Lucide included)
    // Mermaid init (if Mermaid included)
  </script>
</body>
</html>
```

**This load order is mandatory.** See Gotchas for why.

## Gotchas

These are real issues the agent will hit. Read before building.

- **Reveal.js overrides your font-size.** It sets `font-size` on `.reveal` and scales content to fit `width`/`height`. Your custom font sizes only work if you target `.reveal h1`, `.reveal p`, etc. — not bare `h1`, `p`. Always scope selectors under `.reveal`.

- **CDN load order matters.** Google Fonts `<link>` → Reveal.js CSS → your `<style>`. If your custom styles load before Reveal.js CSS, Reveal overrides them. If fonts load after your CSS, the first paint flashes unstyled text.

- **Reveal.js viewport scaling.** Reveal scales the entire `.slides` container to fit the window based on `width`/`height` config. `clamp()` and viewport units (`vw`, `vh`) behave relative to Reveal's virtual viewport (1920x1080), not the browser window. Use `px` or `em` for reliable sizing inside slides.

- **Chart.js canvases need explicit dimensions.** A `<canvas>` inside a Reveal slide collapses to 0x0 unless you set `width`/`height` attributes or wrap it in a container with explicit dimensions. Always set: `<canvas width="700" height="400">`.

- **Chart.js renders once, not per slide.** Charts should be created on `slidechanged` event, not on page load — otherwise they render invisible inside off-screen slides and miscalculate their size. Track rendered state with a `data-rendered` attribute.

- **Three.js `importmap` must precede module scripts.** The `<script type="importmap">` tag must appear before any `<script type="module">` that uses the imports. Place it right before the module script at the bottom.

- **Background canvas z-index.** If using a `<canvas>` for background effects, it must be `position: fixed; z-index: 0` and the `.reveal` div must be `position: relative; z-index: 1`. Without this, slides render behind the canvas.

- **Mermaid + Reveal.js timing.** Mermaid must initialize with `startOnLoad: false` and explicitly call `mermaid.run()` on `Reveal.on('ready')` and `Reveal.on('slidechanged')`. Otherwise diagrams on non-first slides never render.

- **Lucide icon re-init.** Call `lucide.createIcons()` on every `slidechanged` event — icons on slides that haven't been shown yet won't have been created.

- **Speaker notes need Reveal.js Notes plugin.** Import separately: `https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/notes/notes.esm.js` and add to `plugins: []` array.

## Validation

After writing the HTML file, verify before telling the user it's done:

1. **Read the file back** — scan for:
   - CDN load order matches the mandatory structure above
   - All `<section>` tags are properly closed
   - CSS custom properties are defined in `:root` and used consistently
   - No unstyled elements (bare `<table>`, `<ul>`, `<canvas>` without dimensions)
   - Font families in CSS match what's loaded in Google Fonts `<link>`

2. **Check for common breaks:**
   - Chart canvases have explicit width/height
   - Mermaid uses `startOnLoad: false`
   - GSAP `slidechanged` hook exists if GSAP is included
   - Three.js importmap appears before module script
   - All selectors scoped under `.reveal`

3. **If issues found** — fix them and re-read. Do not proceed until validation passes.

4. **Design polish pass** (optional — ask the user):
   - Offer: "Want me to run a polish pass to refine the design?"
   - If yes, invoke `/polish` on the generated HTML file — fixes alignment, spacing, consistency
   - Then `/animate` — reviews and enhances animations with purposeful motion
   - Then `/delight` — adds moments of personality and unexpected touches
   - If the user declines or wants the file as-is, skip this step.

5. **Tell the user:**
   - The file path
   - How to open it (`open filename.html` or browser)
   - Offer refinements: "Want me to adjust colors, swap the style, add speaker notes, or rework any specific slide?"

## Advanced CSS Techniques

Read `references/css-techniques.md` **when you want to elevate the visual quality** beyond basic layouts — frosted glass cards, text blending effects, outlined display type, animated gradients, or clip-path reveals. These are pure CSS, zero dependencies, and can dramatically improve the deck without adding libraries.

## On-Brand Customization

When users provide brand assets (logos, brand colors, brand fonts, style guides):

1. **Brand colors override the style's accent palette.** Map the user's primary brand color to `--accent-color`. Map secondary brand colors to `--color-positive` or secondary accent roles. Keep the style's background and text colors unless the brand guide specifies otherwise.
2. **Brand fonts override the style's typography.** If the user provides a brand font, use it for display. Fall back to the style's body font unless the brand specifies a body face too. Load brand fonts via Google Fonts if available, or ask the user for a hosted URL.
3. **Logos** — see `references/media.md` for placement patterns. Ask the user whether the logo should appear on every slide (persistent bottom-corner) or only on title/closing slides.
4. **Don't fight the brand.** If the user's brand is warm and rounded but they picked a brutalist style, gently suggest a better-fitting style via `AskUserQuestion` rather than forcing a mismatch.

## Design Quality & Polish

While building, ensure:
- Typography hierarchy is clear (display > heading > body > caption)
- Color palette applied consistently across all elements — charts, icons, tables, dividers
- Spacing feels intentional — vary it (tight for grouped elements, generous for hero content)
- Slide layouts vary within the style — don't make every slide look the same
- Opening and closing slides are distinct and memorable
- The overall deck feels cohesive — one design language throughout

### Polish pass

The `/polish`, `/animate`, and `/delight` skills in validation (step 4) can elevate the design further — offer them to the user after the initial build.

For advanced GSAP usage beyond what's in `references/animations.md`, the official GSAP skill provides deeper guidance on timelines, ScrollTrigger, and complex sequences.

## What NOT to do

- Don't ask users to pick hex colors, font names, or animation curves
- Don't present all 32 styles as a menu
- Don't add Three.js or shaders to a simple corporate deck
- Don't ignore the style's do/don't rules
- Don't generate placeholder content — if content is missing, ask for it
- Don't over-animate — restraint is professional
- Don't use default/unstyled charts — always theme to match
- Don't embed large images as base64 — use URLs or file paths
- Don't tell the user the file is ready before running validation
- Don't override brand colors with the style's default accent — brand takes priority
