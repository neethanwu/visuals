# Library Reference

CDN links and initialization for single-file HTML slides. No npm, no build step. Only include libraries the deck actually needs.

For usage patterns and theming, see the domain-specific reference files:
- Charts → [data-viz.md](data-viz.md)
- Icons, code blocks, diagrams → [elements.md](elements.md)
- Animations → [animations.md](animations.md)
- Shaders & backgrounds → [effects.md](effects.md)
- Images & video → [media.md](media.md)

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
- Font `<link>` tags must appear before any `<style>` that references them

---

## Conditional: GSAP

For sequenced entrance animations, staggered reveals, counter animations, and complex timeline effects.

### CDN

```html
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
```

### Integration with IntersectionObserver

```js
// Animate elements when their slide enters the viewport
const gsapObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const items = entry.target.querySelectorAll('[data-animate]');
      if (items.length) {
        gsap.fromTo(items,
          { opacity: 0, y: 20 },
          { opacity: 1, y: 0, duration: 0.5, stagger: 0.1, ease: "power2.out" }
        );
      }
    }
  });
}, { threshold: 0.3 });

document.querySelectorAll('.slide').forEach(s => gsapObserver.observe(s));
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

**The importmap must appear before any `<script type="module">` that uses the imports.**

### Canvas Setup

```html
<canvas id="bg-canvas" style="position:fixed;inset:0;z-index:0;pointer-events:none;"></canvas>
<!-- Slides need position:relative;z-index:1 -->
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

Render charts when their slide becomes visible via IntersectionObserver — not on page load.

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

Initialize after DOM is ready: `lucide.createIcons();`

---

## Conditional: Highlight.js

For syntax-highlighted code blocks. See [elements.md](elements.md) for theme mapping and usage.

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/highlight.js@11/styles/github.min.css">
<script src="https://cdn.jsdelivr.net/npm/highlight.js@11/highlight.min.js"></script>
```

Initialize after DOM is ready: `hljs.highlightAll();`

---

## Conditional: Mermaid.js

For flowcharts, sequence diagrams, and other structured diagrams. See [elements.md](elements.md) for theming and usage.

```html
<script src="https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.min.js"></script>
```

Initialize with `startOnLoad: false`, then call `mermaid.run()` after DOM is ready.
