# Advanced CSS Techniques

Pure CSS techniques to elevate slide visual quality. Zero dependencies — these work in any modern browser alongside Reveal.js.

## Frosted Glass / Glassmorphism

Translucent cards with blur over backgrounds or images.

```css
.glass-card {
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255, 255, 255, 0.1);
}
/* Light variant */
.glass-card-light {
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.3);
}
```
**Best for:** Dark Classy, Neo-Futurism, Bold Signal (over background effects or images)
**Avoid on:** Brutalist styles (conflicts with hard-edge philosophy), Editorial styles (too decorative)

## Text Stroke / Outlined Type

Hollow display text — extremely impactful at large sizes.

```css
.text-outline {
  -webkit-text-stroke: 2px var(--text-primary);
  color: transparent;
}
/* Filled on hover or active state */
.text-outline-fill {
  -webkit-text-stroke: 2px var(--accent-color);
  color: transparent;
  transition: color 0.3s ease;
}
.text-outline-fill:hover,
.text-outline-fill.active {
  color: var(--accent-color);
}
```
**Best for:** Bold Signal (neon outline on dark), Neo-Brutalism, Monochrome Expressive, Constructivist
**Use at:** 72px+ display sizes only — too thin to read at body sizes

## Mix Blend Modes

Text or elements that blend with their background for visual depth.

```css
/* Text that reveals background through blending */
.blend-text {
  mix-blend-mode: difference;
  color: white;
}
/* Overlay element that tints the background */
.blend-overlay {
  mix-blend-mode: multiply;
  background: var(--accent-color);
  opacity: 0.6;
}
/* Screen blend for light-on-dark glow */
.blend-glow {
  mix-blend-mode: screen;
}
```
**Best for:** Neo-Expressionism, Contemporary Collage, Color Field, Bold Signal
**Avoid on:** Editorial and Swiss styles (too experimental)

## Animated CSS Custom Properties

Smooth transitions on custom properties using `@property` registration.

```css
@property --gradient-angle {
  syntax: '<angle>';
  initial-value: 0deg;
  inherits: false;
}
@keyframes rotateGradient {
  to { --gradient-angle: 360deg; }
}
.animated-border {
  border: 2px solid transparent;
  background:
    linear-gradient(var(--bg-color), var(--bg-color)) padding-box,
    conic-gradient(from var(--gradient-angle), var(--accent-color), transparent, var(--accent-color)) border-box;
  animation: rotateGradient 4s linear infinite;
}
```
**Best for:** Neo-Futurism, Bold Signal (animated neon border), Dark Classy

### Animated gradient text

```css
@property --text-gradient-pos {
  syntax: '<percentage>';
  initial-value: 0%;
  inherits: false;
}
@keyframes shiftGradient {
  to { --text-gradient-pos: 100%; }
}
.gradient-text {
  background: linear-gradient(
    90deg,
    var(--accent-color) var(--text-gradient-pos),
    var(--text-primary) calc(var(--text-gradient-pos) + 50%)
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shiftGradient 3s ease infinite alternate;
}
```

## Clip-Path Reveals

Animated shape reveals for slide entrances or element unveiling.

```css
/* Circle expand reveal */
@keyframes circleReveal {
  from { clip-path: circle(0% at 50% 50%); }
  to { clip-path: circle(75% at 50% 50%); }
}
.circle-reveal {
  animation: circleReveal 0.8s ease-out both;
}

/* Diagonal wipe */
@keyframes diagonalWipe {
  from { clip-path: polygon(0 0, 0 0, 0 100%, 0 100%); }
  to { clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%); }
}
.diagonal-wipe {
  animation: diagonalWipe 0.6s ease-out both;
}

/* Inset reveal (box shrinks to reveal content) */
@keyframes insetReveal {
  from { clip-path: inset(50%); }
  to { clip-path: inset(0%); }
}
.inset-reveal {
  animation: insetReveal 0.5s ease-out both;
}
```
**Best for:** Bold slides, expressive styles, title slide entrances
**Avoid on:** Minimalist, Editorial Calm (too theatrical)

## Neon Glow Effect

Soft glow behind accent text or elements. Use sparingly.

```css
.neon-glow {
  text-shadow:
    0 0 10px rgba(var(--accent-rgb), 0.5),
    0 0 30px rgba(var(--accent-rgb), 0.3),
    0 0 60px rgba(var(--accent-rgb), 0.15);
}
/* Subtle version (recommended for most cases) */
.soft-glow {
  text-shadow: 0 0 20px rgba(var(--accent-rgb), 0.25);
}
/* Element glow */
.box-glow {
  box-shadow: 0 0 30px rgba(var(--accent-rgb), 0.2);
}
```
**Best for:** Bold Signal (neon lime/orange glow), Neo-Futurism, Dark Classy
**Rule:** Max 10% opacity on the outer glow — it should feel atmospheric, not radioactive

## Gradient Borders

Borders that transition between colors.

```css
.gradient-border {
  border: 2px solid transparent;
  background:
    linear-gradient(var(--surface-color), var(--surface-color)) padding-box,
    linear-gradient(135deg, var(--accent-color), transparent) border-box;
}
```

## Perspective / 3D Transforms

Tilt cards or images for depth without Three.js.

```css
.perspective-card {
  transform: perspective(1000px) rotateY(-5deg) rotateX(2deg);
  transition: transform 0.4s ease;
}
/* Hover to flatten */
.perspective-card:hover {
  transform: perspective(1000px) rotateY(0) rotateX(0);
}
```
**Best for:** Product screenshots, app mockup slides, Dark Classy, Neo-Futurism

## Staggered Grid with `animation-delay`

Pure CSS stagger without GSAP.

```css
.stagger-grid > * {
  opacity: 0;
  transform: translateY(16px);
  animation: fadeUp 0.4s ease-out forwards;
}
.stagger-grid > *:nth-child(1) { animation-delay: 0s; }
.stagger-grid > *:nth-child(2) { animation-delay: 0.06s; }
.stagger-grid > *:nth-child(3) { animation-delay: 0.12s; }
.stagger-grid > *:nth-child(4) { animation-delay: 0.18s; }
.stagger-grid > *:nth-child(5) { animation-delay: 0.24s; }
.stagger-grid > *:nth-child(6) { animation-delay: 0.3s; }
```

## Counter Animation (CSS only)

Animate a number using `@property` — no JS needed.

```css
@property --num {
  syntax: '<integer>';
  initial-value: 0;
  inherits: false;
}
.css-counter {
  animation: count 2s ease-out forwards;
  counter-reset: num var(--num);
  font-variant-numeric: tabular-nums;
}
.css-counter::after {
  content: counter(num);
}
@keyframes count {
  to { --num: 2400; } /* target number */
}
```

## Scroll-Driven Reveal (Progressive Enhancement)

For non-Reveal.js slides or scrollable sections within a slide:

```css
@keyframes slideUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}
.scroll-reveal {
  animation: slideUp linear both;
  animation-timeline: view();
  animation-range: entry 0% entry 30%;
}
```
**Note:** This uses the Scroll-Driven Animations API. Works in Chrome/Edge, progressive enhancement for others.

## Style-to-Technique Mapping

| Style | Recommended techniques |
|---|---|
| Bold Signal | Text stroke, neon glow, clip-path reveals, animated borders |
| Neo-Futurism | Animated custom properties, glass cards, neon glow, perspective |
| Dark Classy | Glass cards, soft glow, gradient borders, perspective |
| Neo-Expressionism | Mix blend modes, clip-path, stagger grid |
| Color Field | Animated gradients, mix blend modes |
| Contemporary Collage | Clip-path, mix blend modes, perspective |
| Op Art | Animated custom properties (stripe animation) |
| Monochrome Expressive | Text stroke, clip-path reveals |
| Brutalist (all) | Text stroke, stagger grid, CSS counters |
| Minimalist | None — restraint is the technique |
| Editorial (all) | CSS counters for metrics, subtle stagger |
| Swiss (all) | CSS counters, stagger grid |
