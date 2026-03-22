# Library Reference

CDN links, initialization, and Reveal.js integration for single-file HTML slides. No npm, no build step.

For usage patterns and theming, see the domain-specific reference files:
- Charts → [data-viz.md](data-viz.md)
- Icons, code blocks, diagrams → [elements.md](elements.md)
- Animations → [animations.md](animations.md)
- Shaders & backgrounds → [effects.md](effects.md)
- Images & video → [media.md](media.md)

---

## Core: Reveal.js

**Always included.** Slide framework with navigation, keyboard controls, transitions, speaker notes, and PDF export.

### CDN

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/theme/white.css" id="theme">
<script src="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.js"></script>
```

We override the Reveal theme entirely with custom CSS. The theme import provides base resets only — use `white.css` for light styles, `black.css` for dark.

### Initialization

```js
Reveal.initialize({
  hash: true,
  transition: 'fade',           // see animations.md for per-style mapping
  transitionSpeed: 'default',   // 'default', 'fast', 'slow'
  backgroundTransition: 'fade',
  center: true,
  width: 1920,
  height: 1080,                 // 16:9
  margin: 0.04,
  controls: true,
  progress: true,
  slideNumber: 'c/t',
  keyboard: true,
  overview: true,               // ESC to see all slides
  plugins: []
});
```

### Speaker Notes

```html
<section>
  <h2>Title</h2>
  <aside class="notes">Press 'S' to open speaker view.</aside>
</section>
```

### Slide Backgrounds

```html
<section data-background-color="#0A0A0A">
<section data-background-gradient="linear-gradient(to bottom, #0A0A0A, #1A1A1A)">
<section data-background-image="url" data-background-size="cover">
```

### Auto-Animate

Automatically animate between slides with matching elements:

```html
<section data-auto-animate>
  <h1>Title</h1>
</section>
<section data-auto-animate>
  <h1 style="color: red;">Title</h1>
  <p>New content appears</p>
</section>
```

### Fragments (within-slide reveals)

```html
<p class="fragment fade-up">Appears on next click</p>
<p class="fragment fade-up" data-fragment-index="1">Numbered order</p>
```

Built-in: `fade-up`, `fade-down`, `fade-left`, `fade-right`, `fade-in`, `fade-out`, `grow`, `shrink`, `strike`, `highlight-red`, `highlight-blue`, `highlight-green`.

---

## Core: Google Fonts

**Always included.** Load only the weights you use.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```

Tips:
- `display=swap` for fast rendering
- Preconnect to both domains
- For italic: `ital,wght@0,400;1,400` syntax

---

## Conditional: GSAP

For sequenced entrance animations, staggered reveals, counter animations, and background effects. Cross-cutting — used by animations.md, effects.md, and data-viz.md.

### CDN

```html
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
```

### Reveal.js Integration

```js
// Master animation hook — fires on every slide change
Reveal.on('slidechanged', event => {
  const slide = event.currentSlide;
  const items = slide.querySelectorAll('[data-animate]');
  if (items.length) {
    gsap.fromTo(items,
      { opacity: 0, y: 20 },
      { opacity: 1, y: 0, duration: 0.5, stagger: 0.1, ease: "power2.out" }
    );
  }
});

// Also handle the initial slide on load
Reveal.on('ready', event => {
  const slide = event.currentSlide;
  const items = slide.querySelectorAll('[data-animate]');
  if (items.length) {
    gsap.fromTo(items,
      { opacity: 0, y: 20 },
      { opacity: 1, y: 0, duration: 0.5, stagger: 0.1, ease: "power2.out" }
    );
  }
});
```

---

## Conditional: Three.js

For 3D backgrounds, particle systems, WebGL scenes, and shader-driven effects. Heavy — only include when the style calls for it.

### CDN

```html
<script type="importmap">
  { "imports": { "three": "https://cdn.jsdelivr.net/npm/three@0.170/build/three.module.js" } }
</script>
```

### Canvas + Reveal.js Setup

```html
<canvas id="bg-canvas" style="position:fixed;inset:0;z-index:0;pointer-events:none;"></canvas>
<div class="reveal" style="position:relative;z-index:1;">
  <!-- slides -->
</div>
```

```js
import * as THREE from 'three';

const canvas = document.getElementById('bg-canvas');
const renderer = new THREE.WebGLRenderer({ canvas, alpha: true, antialias: true });
renderer.setSize(window.innerWidth, window.innerHeight);
renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
camera.position.z = 5;

function animate() {
  requestAnimationFrame(animate);
  renderer.render(scene, camera);
}
animate();

window.addEventListener('resize', () => {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});
```

---

## Conditional: Chart.js

For bar, line, pie, doughnut, scatter charts. See [data-viz.md](data-viz.md) for theming and usage patterns.

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4/dist/chart.umd.min.js"></script>
```

---

## Conditional: D3.js

For custom editorial-quality data visualizations. See [data-viz.md](data-viz.md) for patterns.

```html
<script src="https://cdn.jsdelivr.net/npm/d3@7/dist/d3.min.js"></script>
```

---

## Conditional: Lucide Icons

For clean, consistent iconography. See [elements.md](elements.md) for styling and patterns.

```html
<script src="https://unpkg.com/lucide@latest"></script>
```

---

## Conditional: Highlight.js

For syntax-highlighted code blocks. See [elements.md](elements.md) for theme mapping and usage.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/highlight.js@11/styles/github.min.css">
<script src="https://cdn.jsdelivr.net/npm/highlight.js@11/highlight.min.js"></script>
```

Or as a Reveal.js plugin:

```html
<script src="https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/highlight/highlight.esm.js"></script>
```

```js
Reveal.initialize({ plugins: [RevealHighlight] });
```

---

## Conditional: Mermaid.js

For flowcharts, sequence diagrams, and other structured diagrams. See [elements.md](elements.md) for theming and usage.

```html
<script src="https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.min.js"></script>
```
