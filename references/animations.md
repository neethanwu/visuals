# Animation & Transition Reference

Self-contained animation primitives for single-file HTML slides. All animations use CSS keyframes or GSAP (when included). Prefer CSS for simple animations, GSAP for sequenced/staggered reveals.

## Slide Transitions (Reveal.js)

Reveal.js supports these built-in transitions. Choose based on style personality.

| Transition | CSS value | Best for styles |
|---|---|---|
| Fade | `fade` | Minimalist, Editorial Calm, Swiss Clean, Elegant Luxury |
| Slide | `slide` | Corporate, Bauhaus Digital, Swiss Clean Expressive |
| Convex | `convex` | Neo-Futurism, Dark Classy |
| Concave | `concave` | Art Deco, Neo-Classicism |
| Zoom | `zoom` | Neo-Brutalism, Nordic Brutalist, Brutalist Luxury |
| None | `none` | Monochrome Expressive, Conceptual Art, Japanese Swiss Mono |

### Reveal.js transition config

```js
Reveal.initialize({
  transition: 'fade',        // default transition
  transitionSpeed: 'default', // 'default', 'fast', 'slow'
  backgroundTransition: 'fade',
});
```

## Element Entrance Animations

### Fade Up (universal — works with any style)

```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to { opacity: 1; transform: translateY(0); }
}
.fade-up {
  animation: fadeUp 0.5s ease-out both;
}
```

### Fade In (minimal — for restrained styles)

```css
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
.fade-in {
  animation: fadeIn 0.4s ease-out both;
}
```

### Slide In Left (editorial / constructivist styles)

```css
@keyframes slideInLeft {
  from { opacity: 0; transform: translateX(-40px); }
  to { opacity: 1; transform: translateX(0); }
}
.slide-in-left {
  animation: slideInLeft 0.5s ease-out both;
}
```

### Scale In (brutalist / bold styles)

```css
@keyframes scaleIn {
  from { opacity: 0; transform: scale(0.92); }
  to { opacity: 1; transform: scale(1); }
}
.scale-in {
  animation: scaleIn 0.4s ease-out both;
}
```

### Type On (monospace / data styles)

```css
@keyframes typeOn {
  from { width: 0; }
  to { width: 100%; }
}
.type-on {
  overflow: hidden;
  white-space: nowrap;
  border-right: 2px solid currentColor;
  animation: typeOn 1.2s steps(30) both, blink 0.8s step-end infinite;
}
@keyframes blink {
  50% { border-color: transparent; }
}
```

### Draw Line (for decorative rules / dividers)

```css
@keyframes drawLine {
  from { transform: scaleX(0); }
  to { transform: scaleX(1); }
}
.draw-line {
  transform-origin: left;
  animation: drawLine 0.6s ease-out both;
}
```

### Counter / Number Roll (for metrics / KPIs)

```js
// GSAP approach (include GSAP)
function animateCounter(el, target) {
  gsap.to(el, {
    innerText: target,
    duration: 1.5,
    ease: "power2.out",
    snap: { innerText: 1 },
    onUpdate: function() {
      el.innerText = Math.round(parseFloat(el.innerText)).toLocaleString();
    }
  });
}
```

### Stagger Children (GSAP — for lists, grids, cards)

```js
// Stagger list items on slide entry
Reveal.on('slidechanged', event => {
  const items = event.currentSlide.querySelectorAll('.stagger-item');
  if (items.length) {
    gsap.fromTo(items,
      { opacity: 0, y: 20 },
      { opacity: 1, y: 0, duration: 0.4, stagger: 0.1, ease: "power2.out" }
    );
  }
});
```

## Style-to-Animation Mapping

### Restrained styles (minimal animation)
**Styles:** Minimalist, Editorial Calm, Japanese Swiss Mono, Swiss Clean, Conceptual Art
- Slide transition: `fade` or `none`
- Entrance: `fade-in` only (no movement)
- Duration: 300-400ms
- No stagger effects
- No background animations
- No GSAP needed

### Editorial styles (purposeful, print-inspired)
**Styles:** Editorial Financial, Editorial Data, Editorial Warm, Swiss Elegant, Industrial Humanist
- Slide transition: `fade`
- Entrance: `fade-up` for headings, `fade-in` for body
- Duration: 400-500ms
- Draw-line for decorative rules
- Mild stagger (0.08s) for list items
- GSAP optional

### Bold styles (dramatic, high-energy)
**Styles:** Neo-Brutalism, Nordic Brutalist v1/v2, Brutalist Luxury v1/v2, Bauhaus Digital
- Slide transition: `zoom` or `slide`
- Entrance: `scale-in` for headings, `fade-up` for content
- Duration: 300-400ms (fast and punchy)
- Aggressive stagger (0.06s) for grids
- Counter animation for metrics
- GSAP recommended

### Dark/luxury styles (smooth, cinematic)
**Styles:** Elegant Luxury, Dark Classy, Brutalist Luxury, Minimal Corporate (dark slides)
- Slide transition: `fade` (slow, 800ms)
- Entrance: `fade-up` with longer duration (600ms)
- Easing: `cubic-bezier(0.25, 0.1, 0.25, 1)` — smooth deceleration
- Subtle stagger (0.12s)
- Counter animation for KPIs
- GSAP recommended for polish

### Expressive styles (playful, unconventional)
**Styles:** Neo-Expressionism, Contemporary Collage, Color Field, Op Art, Deconstructivist
- Slide transition: `convex` or custom
- Entrance: mix of `slide-in-left`, `scale-in`, `fade-up` — variety is intentional
- Duration: 400-600ms
- Rotation animations for decorative elements
- Stagger with slight randomness
- GSAP recommended

### Futuristic styles (technical, animated)
**Styles:** Neo-Futurism, Bauhaus Digital (dark variant)
- Slide transition: `convex` or `fade`
- Entrance: `fade-up` + `type-on` for labels
- Duration: 300-500ms
- Continuous background animations (grid pulse, particle drift)
- Counter animation for data
- GSAP + optional Three.js/shaders

## Timing Reference

| Token | Value | Use case |
|---|---|---|
| `--duration-fast` | 200ms | Hover states, micro-interactions |
| `--duration-normal` | 400ms | Standard entrance animations |
| `--duration-slow` | 600ms | Hero/title entrances, luxury styles |
| `--duration-cinematic` | 800ms | Dark/luxury slide transitions |
| `--ease-out` | `cubic-bezier(0.0, 0.0, 0.2, 1)` | Standard deceleration |
| `--ease-smooth` | `cubic-bezier(0.25, 0.1, 0.25, 1)` | Luxury/cinematic feel |
| `--ease-bounce` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | Playful/bold styles |
| `--ease-sharp` | `cubic-bezier(0.4, 0.0, 0.6, 1)` | Brutalist/punchy |

## Reveal.js Fragment Animations

Use Reveal.js fragments for within-slide reveals:

```html
<p class="fragment fade-up">Appears on next click</p>
<p class="fragment fade-up" data-fragment-index="1">Numbered order</p>
```

Built-in fragment styles: `fade-up`, `fade-down`, `fade-left`, `fade-right`, `fade-in`, `fade-out`, `grow`, `shrink`, `strike`, `highlight-red`, `highlight-blue`, `highlight-green`.

Custom fragment animations:

```css
.fragment.custom-fade-up {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.4s ease-out;
}
.fragment.custom-fade-up.visible {
  opacity: 1;
  transform: translateY(0);
}
```
