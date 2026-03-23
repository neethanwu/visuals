# Animation & Transition Reference

Self-contained animation primitives for single-file HTML slides. All animations use CSS keyframes/transitions or GSAP (when included). The agent generates appropriate animations per deck based on style and content.

## Entrance Animation Trigger

All entrance animations use `IntersectionObserver` to detect when a slide enters the viewport. The agent generates a small JS block and the corresponding CSS:

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) entry.target.classList.add('visible');
  });
}, { threshold: 0.3 });

document.querySelectorAll('.slide').forEach(slide => observer.observe(slide));
```

Elements with `.reveal` (or a style-specific class) start hidden and animate when their parent `.slide` gets `.visible`.

## Element Entrance Animations

### Fade Up (universal — works with any style)

```css
.reveal { opacity: 0; transform: translateY(24px); transition: opacity 0.5s ease-out, transform 0.5s ease-out; }
.slide.visible .reveal { opacity: 1; transform: translateY(0); }
```

### Fade In (minimal — for restrained styles)

```css
.reveal { opacity: 0; transition: opacity 0.4s ease-out; }
.slide.visible .reveal { opacity: 1; }
```

### Slide In Left (editorial / constructivist styles)

```css
.reveal { opacity: 0; transform: translateX(-40px); transition: opacity 0.5s ease-out, transform 0.5s ease-out; }
.slide.visible .reveal { opacity: 1; transform: translateX(0); }
```

### Scale In (brutalist / bold styles)

```css
.reveal { opacity: 0; transform: scale(0.92); transition: opacity 0.4s ease-out, transform 0.4s ease-out; }
.slide.visible .reveal { opacity: 1; transform: scale(1); }
```

### Blur In (glass / luxury styles)

```css
.reveal { opacity: 0; filter: blur(10px); transition: opacity 0.6s ease-out, filter 0.6s ease-out; }
.slide.visible .reveal { opacity: 1; filter: blur(0); }
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
.draw-line { transform: scaleX(0); transform-origin: left; transition: transform 0.6s ease-out; }
.slide.visible .draw-line { transform: scaleX(1); }
```

### Counter / Number Roll (for metrics — requires GSAP)

```js
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

// Trigger on slide visibility
const counterObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.querySelectorAll('[data-counter]').forEach(el => {
        animateCounter(el, parseInt(el.dataset.counter));
      });
    }
  });
}, { threshold: 0.5 });
```

### Stagger Children (GSAP — for lists, grids, cards)

```js
// Stagger items when slide becomes visible
const staggerObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      const items = entry.target.querySelectorAll('.stagger-item');
      if (items.length) {
        gsap.fromTo(items,
          { opacity: 0, y: 20 },
          { opacity: 1, y: 0, duration: 0.4, stagger: 0.1, ease: "power2.out" }
        );
      }
    }
  });
}, { threshold: 0.3 });
```

## Stagger Timing (CSS — no GSAP needed)

For simple stagger without GSAP, use `transition-delay` on nth-child:

```css
.reveal:nth-child(1) { transition-delay: 0s; }
.reveal:nth-child(2) { transition-delay: 0.1s; }
.reveal:nth-child(3) { transition-delay: 0.2s; }
.reveal:nth-child(4) { transition-delay: 0.3s; }
.reveal:nth-child(5) { transition-delay: 0.4s; }
```

## Style-to-Animation Mapping

### Restrained styles (minimal animation)
**Styles:** Minimalist, Editorial Calm, Japanese Swiss Mono, Swiss Clean, Conceptual Art
- Entrance: `fade-in` only (no movement)
- Duration: 300-400ms
- No stagger effects
- No background animations
- No GSAP needed

### Editorial styles (purposeful, print-inspired)
**Styles:** Editorial Financial, Editorial Data, Editorial Warm, Swiss Elegant, Industrial Humanist
- Entrance: `fade-up` for headings, `fade-in` for body
- Duration: 400-500ms
- Draw-line for decorative rules
- Mild stagger (0.08s) for list items
- GSAP optional

### Bold styles (dramatic, high-energy)
**Styles:** Neo-Brutalism, Nordic Brutalist v1/v2, Brutalist Luxury v1/v2, Bauhaus Digital, Pop Art
- Entrance: `scale-in` for headings, `fade-up` for content
- Duration: 300-400ms (fast and punchy)
- Aggressive stagger (0.06s) for grids
- Counter animation for metrics
- GSAP recommended

### Dark/luxury styles (smooth, cinematic)
**Styles:** Elegant Luxury, Dark Classy, Brutalist Luxury, Minimal Corporate (dark slides), Apple Liquid Glass
- Entrance: `fade-up` or `blur-in` with longer duration (600ms)
- Easing: `cubic-bezier(0.25, 0.1, 0.25, 1)` — smooth deceleration
- Subtle stagger (0.12s)
- Counter animation for KPIs
- GSAP recommended for polish

### Expressive styles (playful, unconventional)
**Styles:** Neo-Expressionism, Contemporary Collage, Color Field, Op Art, Deconstructivist, Risograph
- Entrance: mix of `slide-in-left`, `scale-in`, `fade-up` — variety is intentional
- Duration: 400-600ms
- Rotation animations for decorative elements
- Stagger with slight randomness
- GSAP recommended

### Futuristic / digital styles (technical, animated)
**Styles:** Neo-Futurism, Bauhaus Digital (dark variant), Glitch Art, Synthwave
- Entrance: `fade-up` + `type-on` for labels
- Duration: 300-500ms
- Continuous background animations (grid pulse, particle drift, scan lines)
- Counter animation for data
- GSAP + optional Three.js/shaders

### Print / analog styles
**Styles:** Risograph, Blueprint
- Entrance: `fade-in` or `slide-in-left`
- Duration: 400-500ms
- Draw-line for dimension lines (Blueprint)
- Minimal animation — let the visual texture carry the style
- No GSAP needed

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

## Fragment Animations

Fragments (within-slide reveals) use the same CSS patterns as entrance animations but are triggered by user interaction (click/keypress) instead of IntersectionObserver:

```css
.fragment { opacity: 0; transform: translateY(12px); transition: opacity 0.4s ease-out, transform 0.4s ease-out; }
.fragment.visible { opacity: 1; transform: translateY(0); }
```

The agent generates the fragment handler JS inline — see `template.md` for the pattern.
