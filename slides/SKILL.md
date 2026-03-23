---
name: slides
description: Builds beautiful single-file HTML presentations with professional design, animations, and interactive effects. Triggers when the user wants to create slides, a presentation, a deck, a pitch deck, a talk, a keynote, or a lecture. Activates on "make slides", "build a presentation", "slide deck", "create a deck", "presentation about", "slides for my talk", "pitch deck for", "turn this into slides", "present this", "/slides". Also triggers when user has accumulated content (notes, outlines, research) and wants it turned into a visual presentation.
user-invocable: true
args:
  - name: topic
    description: The topic, content, or file path to build slides from
    required: false
---

# Slides — Single-File HTML Presentation Builder

## MANDATORY PREPARATION

Before building anything, confirm you have sufficient context: content (or topic), audience/tone, and whether brand assets are involved. If any of these are unclear, STOP and use `AskUserQuestion` to clarify before proceeding.

Read `reference/template.md` before building your first deck in a session.

## Architecture

Zero dependencies. Each presentation is a single self-contained `.html` file using CSS scroll-snap — no framework.

- Slides are `100dvh` sections with `scroll-snap-type: y mandatory`
- Typography scales via `clamp()`, layouts are natively responsive
- Navigation, animations, fragments — agent-generated per deck, not a fixed engine
- Libraries (Chart.js, GSAP, D3, etc.) added via CDN only when the content needs them

## Context Assessment

Assess what context already exists. Do NOT follow a rigid step-by-step wizard. Figure out what you have, what you need, and fill the gaps.

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

## Communication Philosophy

Be an opinionated collaborator with taste, not a menu system. Make the best choices you can, and communicate with the user in plain language when there's a meaningful fork in the road.

### Always ask when needed:
- **Content gaps** — you need the user's actual content, topic, or key points. Don't fabricate.
- **Brand context** — if the presentation is for a company or product, ask whether they have brand colors, fonts, or a logo to incorporate. Don't ask for a personal/casual deck.
- **Speaker notes** — for talk-style decks, ask if they want speaker notes embedded.
- **Meaningful style forks** — when 2-3 styles would work equally well, present them in plain language the user can evaluate:
  > "I see two directions for this:\n\n1. **Warm editorial** — cream tones, serif headlines, magazine feel\n2. **Dark and bold** — black background, neon accent, high-impact\n\nWhich feels right, or should I pick?"

### Agent decides, then communicates what it chose:
- **Animation level** — pick what fits the style and content. Mention it in the summary ("I used subtle fade-in animations to match the editorial feel").
- **GSAP vs CSS animations** — use whichever produces the best result. The user doesn't need to know the implementation.
- **Background effects** — add particle fields, shaders, or gradients when the style calls for it. Skip for restrained styles. Don't ask permission.
- **Font trio** — read `reference/font-guide.md`, pick the best match for the style, load via Google Fonts. Mention the fonts in the summary.
- **Charts, tables, data viz** — when content includes data, metrics, or comparisons, add appropriate visualizations. Don't ask "should I add a chart?" — just do it if the data warrants it.
- **Icons, diagrams, code blocks** — include when content benefits. Don't ask.
- **Fragment reveals** — add click-to-reveal for lecture/talk content where sequential builds help. Don't add for pitch decks or simple presentations.

### Never ask about:
- Hex colors, font names, animation easing, CSS values, or technical implementation
- Which of the 37 styles to use — curate for them
- Things you can infer from content (data-heavy → data-appropriate style)
- Things with a clear single best answer
- "Should I add GSAP?" "Should I include a progress bar?" — make the call

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

37 curated design styles live in `reference/styles/`. Read the chosen style file for its Color Palette, Typography, Design Principles, and Slide Application Notes. Apply with taste — they're guides, not rigid templates.

### Interpreting style files — terminology glossary

Style files use inconsistent terminology. Normalize when reading:

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

Always map style file tokens to these CSS custom properties in your output.

### How to choose

Infer from content. Do NOT present all 37 as a menu.

| Content type | Recommended styles |
|---|---|
| Startup pitch / product launch | p-bold-signal, p-minimal-corporate, p-dark-classy, p-swiss-clean |
| Financial / data-heavy | p-editorial-financial, p-editorial-data, p-swiss-elegant |
| Technical / engineering | p-bauhaus-digital, p-swiss-clean-expressive, 08-neo-brutalism, blueprint |
| Creative / portfolio | 05-neo-expressionism, 16-contemporary-collage, p-monochrome-expressive, pop-art |
| Corporate / formal | p-minimal-corporate, p-swiss-clean, p-editorial-calm |
| Academic / research | p-editorial-calm, p-swiss-elegant, 01-minimalist |
| Luxury / premium brand | p-elegant-luxury, p-brutalist-luxury, p-dark-classy, apple-liquid-glass |
| Futuristic / tech-forward | 07-neo-futurism, p-bold-signal, p-bauhaus-digital, glitch-art |
| Editorial / storytelling | p-editorial-warm, p-editorial-calm, p-industrial-humanist |
| Bold / high-impact | p-bold-signal, p-nordic-brutalist-v2, p-brutalist-luxury-v2, 08-neo-brutalism |
| Warm / approachable | p-editorial-warm, p-industrial-humanist, 01-minimalist |
| Elegant / refined | p-swiss-elegant, 12-art-deco, 06-neo-classicism |
| Retro / nostalgic / fun | synthwave, pop-art, risograph |
| Print / analog aesthetic | risograph, 16-contemporary-collage, blueprint |
| Disruptive / edgy | glitch-art, 04-deconstructivist, 08-neo-brutalism |
| Modern / glass / premium tech | apple-liquid-glass, p-dark-classy, 07-neo-futurism |

Strong single match → just use it. Multiple equally good → `AskUserQuestion` with 2-3 visual descriptions.

## Font Selection

49 curated font trios (heading + body + mono) in `reference/font-guide.md`. **Always read the font guide** and cross-reference with the style — do not blindly hardcode fonts from the style file. Pick the trio that best fits the style's mood.

Load fonts via Google Fonts `<link>` tags. To convert a trio name to a Google Fonts URL, take the font family names and build: `https://fonts.googleapis.com/css2?family=Font+Name:wght@400;500;600;700&display=swap`

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
| Retro / expressive | poster, headline, brutalist, creative |

## Reference Quick Lookup

All references live in `reference/`. Template and font guide are loaded in MANDATORY PREPARATION. Load the rest based on content needs:

| Reference | When to load |
|---|---|
| `reference/animations.md` | Entrance animations and transitions for the style |
| `reference/effects.md` | Background effects — particles, shaders, scan lines, halftone, gradient mesh |
| `reference/data-viz.md` | Data, metrics, charts, comparisons, tables |
| `reference/media.md` | Images, video, logos, screenshots |
| `reference/elements.md` | Icons, code blocks, diagrams, decorative SVGs, styled lists |
| `reference/css-techniques.md` | Frosted glass, text blending, outlined type, animated gradients, clip-path reveals |

**Key principle:** Don't just react to what the user explicitly asks for. Consider what would make the deck better. If the outline has data, add charts. If the style calls for entrance animations, add them. The goal is the best possible deck, not the minimum viable one.

## Building the HTML

### Output

Single self-contained `.html` file. Styles in `<style>`, scripts in `<script>`, libraries via CDN only when needed.

**Content sanitization:** When interpolating user-provided text into slides, escape `<script>`, `</style>`, and raw HTML tags in body content to prevent accidental breakage of the document structure.

### Structure

Follow the skeleton in `reference/template.md`:

1. **`<head>`**: Google Fonts `<link>` → optional library CSS → `<style>` with structural CSS + agent-generated styles
2. **`<body>`**: `<div class="slide">` sections → optional progress bar / nav dots → CDN scripts → inline `<script>` with agent-generated JS

The structural CSS (~10 lines) is always present. Everything else — typography, layouts, colors, animations, navigation JS, fragment handling — is generated fresh for each deck based on style + content.

### What to generate per deck

| Feature | When to include | How |
|---|---|---|
| Keyboard navigation | Always | Agent generates JS for arrow keys, space bar |
| Touch/swipe support | Mobile-friendly decks | Agent adds touch event handlers |
| Entrance animations | Most decks (skip for ultra-minimal) | IntersectionObserver + CSS transitions. See `animations.md` for style-specific patterns |
| Fragment reveals | Talks/lectures with sequential builds | `.fragment` + `.visible` class pattern. See `template.md` |
| Progress bar | Longer decks (10+ slides) | Fixed bar at top, updates on scroll |
| Navigation dots | When style suits visible nav | Positioned buttons, highlight active |
| Background effects | When style calls for it | Canvas/WebGL behind slides. See `effects.md` |
| GSAP animations | Staggered reveals, counters, complex sequences | Load GSAP CDN, use with IntersectionObserver |
| Charts | Data slides | Chart.js or D3, render on slide visibility via IntersectionObserver |
| Code highlighting | Code slides | Highlight.js CDN, call `hljs.highlightAll()` after DOM ready |
| Diagrams | Process/flow slides | Mermaid CDN, init with `startOnLoad: false`, call `mermaid.run()` after DOM ready |
| Icons | When content benefits | Lucide CDN, call `lucide.createIcons()` after DOM ready |
| Speaker notes | When user requests | HTML comments inside `.slide` divs |

## Gotchas

These are real issues to watch for:

- **Chart.js canvases need explicit dimensions.** A `<canvas>` inside a slide collapses to 0x0 unless wrapped in a container with explicit dimensions or given `width`/`height` attributes.

- **Charts should render on visibility, not page load.** Use IntersectionObserver to detect when a chart's slide enters the viewport, then create the chart. Otherwise charts render at 0x0 inside off-screen slides.

- **Three.js `importmap` must precede module scripts.** Place `<script type="importmap">` before any `<script type="module">`.

- **Background canvas z-index.** Canvas for effects: `position: fixed; z-index: 0`. Slides need `position: relative; z-index: 1`.

- **Mermaid timing.** Initialize with `startOnLoad: false`, call `mermaid.run()` after DOM is ready. Otherwise diagrams on non-first slides never render.

- **Lucide icons need explicit init.** Call `lucide.createIcons()` after DOM is ready.

- **Fragment + navigation interaction.** When fragments exist on a slide, keyboard navigation should reveal fragments first, then advance to the next slide when all fragments are visible. The agent must wire these together.

- **Google Fonts load order.** Font `<link>` tags must appear before any `<style>` that references them to avoid flash of unstyled text.

- **Content overflow.** Each slide has `overflow: hidden`. If content is too dense, it clips. Respect the "one idea per slide" rule. Use responsive `clamp()` sizing so content scales down on smaller screens.

## On-Brand Customization

When users provide brand assets (logos, brand colors, brand fonts, style guides):

1. **Brand colors override the style's accent palette.** Map the user's primary brand color to `--accent-color`. Map secondary brand colors to `--color-positive` or secondary accent roles. Keep the style's background and text colors unless the brand guide specifies otherwise.
2. **Brand fonts override the style's typography.** If the user provides a brand font, use it for display. Fall back to the style's body font unless the brand specifies a body face too. Load brand fonts via Google Fonts if available, or ask the user for a hosted URL.
3. **Logos** — see `reference/media.md` for placement patterns. Ask the user whether the logo should appear on every slide (persistent bottom-corner) or only on title/closing slides.
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

The `/polish`, `/animate`, and `/delight` skills can elevate the design further — offer them to the user after the initial build.

For advanced GSAP usage beyond what's in `reference/animations.md`, the official GSAP skill provides deeper guidance on timelines, ScrollTrigger, and complex sequences.

## Validation

After writing the HTML file, verify before telling the user it's done:

1. **Read the file back** — scan for:
   - Structural CSS present (scroll-snap, 100dvh, overflow hidden, reduced-motion)
   - All `<div class="slide">` tags properly closed
   - CSS custom properties defined in `:root` and used consistently
   - No unstyled elements (bare `<table>`, `<ul>`, `<canvas>` without dimensions)
   - Font families in CSS match what's loaded in Google Fonts `<link>`
   - Navigation JS present (keyboard at minimum)
   - IntersectionObserver wired up if entrance animations exist

2. **Check for common breaks:**
   - Chart canvases have explicit width/height or a sized container
   - Mermaid uses `startOnLoad: false`
   - Three.js importmap appears before module script
   - Fragment handler integrates with navigation (reveals before advancing)
   - Lucide `createIcons()` called after DOM ready

3. **If issues found** — fix them and re-read. Do not proceed until validation passes.

4. **Design polish pass** (optional — offer to the user):
   - "Want me to run a polish pass to refine the design?"
   - If yes, invoke `/polish`, `/animate`, `/delight` in sequence
   - If the user declines, skip.

5. **Tell the user:**
   - The file path
   - How to open it (`open filename.html` or browser)
   - What style, fonts, and key design choices you made
   - Offer refinements: "Want me to adjust colors, swap the style, add speaker notes, or rework any specific slide?"

## What NOT to do

- Don't ask users to pick hex colors, font names, or animation curves
- Don't present all 37 styles as a menu
- Don't add Three.js or shaders to a simple corporate deck
- Don't ignore the style's do/don't rules
- Don't generate placeholder content — if content is missing, ask for it
- Don't over-animate — restraint is professional
- Don't use default/unstyled charts — always theme to match
- Don't embed large images as base64 — use URLs or file paths
- Don't tell the user the file is ready before running validation
- Don't override brand colors with the style's default accent — brand takes priority
- Don't hardcode fonts from style files without checking the font guide
- Don't skip data visualization when the content has data — charts and styled tables make decks better
- Don't ask the user technical implementation questions they can't answer
