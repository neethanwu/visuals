# HTML Template

The structural foundation for every slide deck. The agent reads this before building its first deck in a session, then generates everything custom on top.

## Architecture

Zero dependencies. Each presentation is a single self-contained `.html` file:
- CSS in `<style>`, scripts in `<script>`, libraries via CDN only when needed
- Slides are `100dvh` sections with CSS scroll-snap — the browser handles snapping
- No framework. The agent generates all CSS and JS inline, tailored to the deck's style and content
- Navigation, entrance animations, fragments — generated per deck, not a fixed engine

## HTML Skeleton

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Presentation Title</title>

  <!-- 1. Google Fonts (before any CSS that references them) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=...&display=swap" rel="stylesheet">

  <!-- 2. Optional: Highlight.js theme CSS (if code slides exist) -->

  <style>
    /* ============================================
       STRUCTURAL — always present, never changes
       ============================================ */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-snap-type: y mandatory; scroll-behavior: smooth; }
    html, body { height: 100%; overflow-x: hidden; }
    .slide {
      width: 100vw;
      height: 100vh;
      height: 100dvh;
      overflow: hidden;
      scroll-snap-align: start;
      display: flex;
      position: relative;
    }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        animation-duration: 0.01ms !important;
        transition-duration: 0.2s !important;
      }
      html { scroll-behavior: auto; }
    }

    /* ============================================
       STYLE — agent-generated, unique per deck
       ============================================ */

    /* Design tokens from the chosen style */
    :root {
      --display-font: 'Font Name', sans-serif;
      --body-font: 'Font Name', sans-serif;
      --mono-font: 'Font Name', monospace;
      --text-primary: #0F0F0F;
      --text-secondary: #6B6B6B;
      --bg-color: #FAFAF7;
      --surface-color: #FFFFFF;
      --accent-color: #C41E3A;
      --border-color: #E0E0E0;
      --color-positive: #2D7A4F;
      --color-negative: #C41E3A;
    }

    /* Typography — use clamp() for responsive scaling */
    body { font-family: var(--body-font); color: var(--text-primary); background: var(--bg-color); }
    h1, h2, h3 { font-family: var(--display-font); }
    h1 { font-size: clamp(2rem, 6vw, 4.5rem); }
    h2 { font-size: clamp(1.5rem, 4vw, 3rem); }
    h3 { font-size: clamp(1.1rem, 2.5vw, 1.75rem); }
    p, li { font-size: clamp(0.85rem, 1.5vw, 1.25rem); line-height: 1.6; }

    /* Slide content container */
    .slide-content {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: clamp(1.5rem, 5vw, 5rem);
      max-height: 100%;
      overflow: hidden;
    }

    /* Responsive breakpoints — agent adjusts clamp values per style */
    @media (max-height: 600px) {
      .slide-content { padding: clamp(0.75rem, 3vw, 2rem); }
    }
    @media (max-width: 600px) {
      .grid, .split { grid-template-columns: 1fr; }
    }

    /* Layouts, components, animations — all agent-generated below */
  </style>
</head>
<body>

  <!-- Slides -->
  <div class="slide" id="slide-1">
    <div class="slide-content">
      <!-- slide content here -->
    </div>
  </div>

  <div class="slide" id="slide-2">
    <div class="slide-content">
      <!-- slide content here -->
    </div>
  </div>

  <!-- Optional: progress bar -->
  <div class="progress-bar"></div>

  <!-- Optional: navigation dots -->
  <nav class="nav-dots"></nav>

  <!-- Optional: CDN libraries (Chart.js, D3, GSAP, Highlight.js, Mermaid, Lucide, Three.js) -->

  <script>
    // Agent-generated JS — only what this deck needs
  </script>
</body>
</html>
```

## Structural CSS Explained

These rules are always present. They make it a presentation:

| Rule | Why |
|---|---|
| `scroll-snap-type: y mandatory` | Browser snaps to each slide on scroll/swipe/keyboard |
| `height: 100dvh` | Each slide fills exactly one screen (`dvh` handles mobile browser chrome) |
| `overflow: hidden` on `.slide` | Prevents content bleeding between slides |
| `scroll-snap-align: start` | Snap point is the top edge of each slide |
| `prefers-reduced-motion` | Accessibility — disables animations for users who request it |
| `box-sizing: border-box` | Sane box model for all elements |

Everything else — typography, spacing, colors, layouts, animations, navigation — is agent-generated per deck.

## Agent-Generated Patterns

The following patterns are NOT fixed code. The agent generates the appropriate version based on the deck's style and content needs. These are reference patterns to draw from.

### Navigation + Entrance Animations + Fragments (Unified)

These three features share one IntersectionObserver and one keydown handler. The agent generates them as a single integrated block — never as separate pieces.

**CSS for entrance animations and fragments:**

```css
/* Entrance animations — fire when slide becomes visible */
.reveal { opacity: 0; transform: translateY(24px); transition: opacity 0.5s ease, transform 0.5s ease; }
.slide.visible .reveal { opacity: 1; transform: translateY(0); }

/* Stagger children */
.reveal:nth-child(2) { transition-delay: 0.1s; }
.reveal:nth-child(3) { transition-delay: 0.2s; }
.reveal:nth-child(4) { transition-delay: 0.3s; }

/* Fragments — hidden until revealed by user interaction */
.fragment { opacity: 0; transform: translateY(12px); transition: opacity 0.4s ease, transform 0.4s ease; }
.fragment.visible { opacity: 1; transform: translateY(0); }
```

The agent varies animation type per style — see `animations.md` for fade-up, scale-in, slide-left, blur-in, etc.

**JS — one observer, one keydown handler:**

```js
const slides = document.querySelectorAll('.slide');
let currentIndex = 0;

// Single observer: tracks current slide + triggers entrance animations
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      currentIndex = [...slides].indexOf(entry.target);
    }
  });
}, { threshold: 0.5 });
slides.forEach(slide => observer.observe(slide));

// Single keydown handler: fragments first, then navigation
document.addEventListener('keydown', (e) => {
  if (e.key === 'ArrowDown' || e.key === 'ArrowRight' || e.key === ' ') {
    e.preventDefault();
    // Check for unrevealed fragments on current slide first
    const currentSlide = slides[currentIndex];
    const nextFragment = currentSlide?.querySelector('.fragment:not(.visible)');
    if (nextFragment) {
      nextFragment.classList.add('visible');
      return; // reveal fragment, don't advance slide
    }
    // No more fragments — advance to next slide
    slides[Math.min(currentIndex + 1, slides.length - 1)]?.scrollIntoView({ behavior: 'smooth' });
  }
  if (e.key === 'ArrowUp' || e.key === 'ArrowLeft') {
    e.preventDefault();
    slides[Math.max(currentIndex - 1, 0)]?.scrollIntoView({ behavior: 'smooth' });
  }
});
```

**Important:** Do NOT calculate the current slide from `scrollY / innerHeight` — this is unreliable with scroll-snap. Always track via IntersectionObserver.

The agent adapts this per deck — add touch/swipe for mobile, Home/End for longer decks, skip fragment logic if no fragments exist.

**Fragment HTML pattern:**

```html
<div class="slide" id="slide-3">
  <div class="slide-content">
    <h2>Key Findings</h2>
    <p class="fragment">First point appears on click</p>
    <p class="fragment">Second point appears next</p>
    <p class="fragment">Third point appears last</p>
  </div>
</div>
```

### Progress Bar

Generate when: longer decks (10+ slides) or when the style suits it.

```html
<div class="progress-bar"></div>
```

```css
.progress-bar {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  background: var(--accent-color);
  z-index: 100;
  transition: width 0.3s ease;
}
```

```js
window.addEventListener('scroll', () => {
  const scrollPercent = window.scrollY / (document.body.scrollHeight - window.innerHeight);
  document.querySelector('.progress-bar').style.width = `${scrollPercent * 100}%`;
});
```

### Navigation Dots

Generate when: style benefits from visible navigation (most styles). Skip for immersive/fullscreen/minimal styles.

```js
const dots = document.querySelector('.nav-dots');
document.querySelectorAll('.slide').forEach((slide, i) => {
  const dot = document.createElement('button');
  dot.addEventListener('click', () => slide.scrollIntoView({ behavior: 'smooth' }));
  dots.appendChild(dot);
});

// Highlight active dot on scroll
const dotObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const index = [...document.querySelectorAll('.slide')].indexOf(entry.target);
      dots.querySelectorAll('button').forEach((d, i) => d.classList.toggle('active', i === index));
    }
  });
}, { threshold: 0.5 });
document.querySelectorAll('.slide').forEach(s => dotObserver.observe(s));
```

The agent styles the dots to match the deck — position, size, shape, colors, visibility.

### Speaker Notes

Speaker notes are HTML comments inside slides. They are invisible in the presentation but accessible in the source:

```html
<div class="slide">
  <div class="slide-content">
    <h2>Revenue Growth</h2>
    <p>Q4 revenue grew 23% year-over-year.</p>
  </div>
  <!-- NOTES: Mention the APAC expansion contributed $340K net new. Compare to Q3 which was flat. -->
</div>
```

### Background Canvas (Effects)

Generate when: style calls for particle fields, shaders, or animated backgrounds. See `effects.md`.

```html
<canvas id="bg-effect" style="position:fixed;inset:0;z-index:0;pointer-events:none;"></canvas>
<!-- Slides go after, with position:relative;z-index:1 on each .slide -->
```

## Slide Layouts

The agent generates layouts inline. Common patterns:

### Centered Content (default)
```css
.slide-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center; /* or flex-start for left-aligned styles */
  text-align: center; /* or left */
}
```

### Two-Column Split
```css
.split {
  display: grid;
  grid-template-columns: 1.3fr 1fr;
  gap: clamp(1rem, 3vw, 4rem);
  align-items: center;
  height: 100%;
}
```

### Metrics Row
```css
.metrics-row {
  display: flex;
  gap: clamp(1rem, 4vw, 4rem);
  justify-content: center;
  flex-wrap: wrap;
}
```

### Bento Grid
```css
.bento {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 280px), 1fr));
  gap: clamp(0.5rem, 1.5vw, 1.25rem);
}
```

### Full-Bleed Image Background
```css
.slide-bg-image {
  background-image: url('...');
  background-size: cover;
  background-position: center;
}
.slide-bg-image .slide-content {
  background: linear-gradient(to top, rgba(0,0,0,0.7) 0%, transparent 60%);
}
```

## Library Integration (CDN)

Only include libraries the deck actually needs. Load via CDN, no build step.

### Google Fonts (always)
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=...&display=swap" rel="stylesheet">
```

### Chart.js (when data slides exist)
```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4/dist/chart.umd.min.js"></script>
```
Render charts when their slide becomes visible using IntersectionObserver — not on page load. See `data-viz.md` for theming and chart patterns.

### D3.js (when editorial-quality custom viz is needed)
```html
<script src="https://cdn.jsdelivr.net/npm/d3@7/dist/d3.min.js"></script>
```

### GSAP (when sequenced/staggered animations are needed)
```html
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
```
Use for counter animations, complex staggered reveals, timeline sequences. See `animations.md`.

### Highlight.js (when code slides exist)
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/highlight.js@11/styles/github.min.css">
<script src="https://cdn.jsdelivr.net/npm/highlight.js@11/highlight.min.js"></script>
```
Initialize after DOM is ready: `hljs.highlightAll();`
See `elements.md` for theme mapping per style.

### Lucide Icons (when icons are used)
```html
<script src="https://unpkg.com/lucide@latest"></script>
```
Initialize: `lucide.createIcons();`

### Mermaid.js (when diagrams are needed)
```html
<script src="https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.min.js"></script>
```
Initialize with `startOnLoad: false`, then call `mermaid.run()` after DOM is ready. See `elements.md`.

### Three.js (when 3D/WebGL effects are needed)
```html
<script type="importmap">
  { "imports": { "three": "https://cdn.jsdelivr.net/npm/three@0.170/build/three.module.js" } }
</script>
```
Place importmap before any `<script type="module">`. See `effects.md`.

## Responsive Sizing Guide

All sizing uses `clamp()` so slides scale naturally from mobile to desktop:

| Element | Pattern | Example |
|---|---|---|
| Display title | `clamp(min, preferred, max)` | `clamp(2rem, 6vw, 4.5rem)` |
| Heading | `clamp()` | `clamp(1.5rem, 4vw, 3rem)` |
| Body text | `clamp()` | `clamp(0.85rem, 1.5vw, 1.25rem)` |
| Slide padding | `clamp()` | `clamp(1.5rem, 5vw, 5rem)` |
| Gaps | `clamp()` | `clamp(0.5rem, 2vw, 2rem)` |
| Cards max-width | `min()` | `min(90vw, 1000px)` |
| Images max-height | `min()` | `min(50vh, 400px)` |
| Grids | `minmax()` with `auto-fit` | `repeat(auto-fit, minmax(min(100%, 250px), 1fr))` |

The agent should adjust these clamp values per style — a Brutalist style wants larger, bolder type scales; a Minimalist style wants more restrained sizes with more whitespace.

## What This Replaces

This template replaces the Reveal.js-based architecture. Key differences:
- No `<div class="reveal"><div class="slides">` wrapper — slides are direct `<div class="slide">` children of `<body>`
- No Reveal.js CSS/JS CDN — zero framework dependency
- No `.reveal` selector scoping — style elements directly
- No `Reveal.initialize()` — navigation is agent-generated JS
- No `Reveal.on('slidechanged')` — use `IntersectionObserver` instead
- No fixed 1920x1080 viewport scaling — native responsive via `clamp()`/`dvh`
- No Reveal.js fragments — use `.fragment` + `.visible` class pattern
- No Reveal.js speaker notes plugin — use HTML comments
- Full creative freedom — no framework CSS to override
