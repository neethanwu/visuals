# SVGs, Icons & Slide Elements Reference

Icons, code blocks, diagrams, inline SVGs, decorative dividers, and visual elements for slides. All elements must match the chosen style's visual personality.

## Lucide Icons

Clean, consistent, open-source icon set. 1500+ icons available via CDN.

### Init

CDN tag is in `libraries.md`. After loading, initialize:

```js
lucide.createIcons();
Reveal.on('slidechanged', () => lucide.createIcons());
```

### Usage

```html
<i data-lucide="arrow-right"></i>
<i data-lucide="bar-chart-2"></i>
<i data-lucide="check-circle"></i>
```

### Styling

Lucide icons render as inline SVGs, styled via CSS:

```css
[data-lucide] {
  width: 24px;
  height: 24px;
  stroke: currentColor;
  stroke-width: 1.5;
}
.icon-sm [data-lucide] { width: 16px; height: 16px; }
.icon-lg [data-lucide] { width: 32px; height: 32px; }
.icon-xl [data-lucide] { width: 48px; height: 48px; }
```

### Style-specific icon treatment

| Style category | Icon approach |
|---|---|
| Editorial / Swiss | Thin stroke (1.5), small size (16-20px), monochrome |
| Brutalist | Heavier stroke (2-2.5), medium size (24px), high contrast |
| Minimal | Hairline stroke (1), muted color, used sparingly |
| Luxury / Dark | Thin stroke, accent color (gold), elegant sizing |
| Warm / Humanist | Standard stroke (1.5-2), warm palette, friendly |
| Expressive | Mix sizes freely, use as layout elements |

### Common icon patterns

**Feature list with icons:**
```html
<div class="feature-list">
  <div class="feature-item">
    <i data-lucide="zap" class="feature-icon"></i>
    <div>
      <strong>Fast Performance</strong>
      <p>Lightning-fast load times under 200ms.</p>
    </div>
  </div>
</div>
```

**Metric with icon:**
```html
<div class="metric">
  <i data-lucide="trending-up"></i>
  <span class="metric-value">+42%</span>
  <span class="metric-label">Growth</span>
</div>
```

**Navigation / progress indicator:**
```html
<div class="step-indicator">
  <div class="step active"><i data-lucide="check"></i> Research</div>
  <div class="step active"><i data-lucide="check"></i> Design</div>
  <div class="step current"><i data-lucide="circle"></i> Build</div>
  <div class="step"><i data-lucide="circle"></i> Launch</div>
</div>
```

---

## Code Blocks (Highlight.js)

Syntax-highlighted code for technical slides.

### Setup

CDN tags are in `libraries.md`. Add the Highlight.js plugin to Reveal.js init:

```js
Reveal.initialize({ plugins: [RevealHighlight] });
```

### Theme mapping per style

| Style mood | Highlight.js theme | CDN path |
|---|---|---|
| Light / editorial | `github` | `highlight.js@11/styles/github.min.css` |
| Dark / luxury | `github-dark` | `highlight.js@11/styles/github-dark.min.css` |
| Minimal / Swiss | `default` | `highlight.js@11/styles/default.min.css` |
| Brutalist | `monokai` | `highlight.js@11/styles/monokai.min.css` |
| Futuristic / dark | `tokyo-night-dark` | `highlight.js@11/styles/tokyo-night-dark.min.css` |

### Usage in slides

```html
<section>
  <pre><code class="language-javascript" data-trim data-line-numbers>
function greet(name) {
  return `Hello, ${name}!`;
}
  </code></pre>
</section>
```

### Styling code blocks to match the deck

```css
.reveal pre {
  width: 90%;
  margin: 0 auto;
  box-shadow: none;
  border: 1px solid var(--border-color);
  border-radius: 0; /* match style — 0 for brutalist/swiss, 4-8px for warm */
}
.reveal code {
  font-family: var(--mono-font);
  font-size: 16px;
  line-height: 1.6;
  padding: 24px;
}
/* Line numbers */
.reveal pre code .hljs-ln-numbers {
  color: var(--text-secondary);
  opacity: 0.5;
  padding-right: 16px;
}
```

---

## Diagrams (Mermaid.js)

Flowcharts, sequence diagrams, Gantt charts, and other structured diagrams.

### Init

CDN tag is in `libraries.md`. After loading, initialize:

```js
mermaid.initialize({
  startOnLoad: false,
  theme: 'neutral',  // or 'dark' for dark styles
  themeVariables: {
    primaryColor: 'var(--accent-color, #4A9FD8)',
    primaryTextColor: 'var(--text-primary, #1A1A1A)',
    primaryBorderColor: 'var(--border-color, #E0E0E0)',
    lineColor: 'var(--text-secondary, #777)',
    secondaryColor: 'var(--surface-color, #F5F5F5)',
    tertiaryColor: 'var(--bg-color, #FFFFFF)',
    fontFamily: 'var(--body-font, Inter)',
    fontSize: '14px',
  }
});

Reveal.on('ready', () => mermaid.run());
Reveal.on('slidechanged', () => mermaid.run());
```

### Usage in slides

```html
<section>
  <div class="mermaid">
    graph LR
      A[Research] --> B[Design]
      B --> C[Build]
      C --> D[Ship]
  </div>
</section>
```

### Theme mapping per style

| Style mood | Mermaid theme | Notes |
|---|---|---|
| Light / editorial / swiss | `neutral` | Clean, minimal chrome |
| Dark / luxury | `dark` | Adjust themeVariables for your palette |
| Futuristic | `dark` | Use accent colors for nodes |
| Warm / humanist | `neutral` | Warm border and node colors |

### Styling Mermaid diagrams

```css
/* Override Mermaid's default sizing */
.reveal .mermaid {
  max-width: 80%;
  margin: 0 auto;
}
.reveal .mermaid svg {
  max-height: 60vh;
}
/* Match node text to deck typography */
.mermaid .nodeLabel {
  font-family: var(--body-font) !important;
}
```

### Common diagram types

```
# Flowchart
graph TD
  A[Start] --> B{Decision}
  B -->|Yes| C[Action A]
  B -->|No| D[Action B]

# Sequence diagram
sequenceDiagram
  User->>API: Request
  API->>DB: Query
  DB-->>API: Result
  API-->>User: Response

# Gantt chart
gantt
  title Project Timeline
  section Phase 1
  Research: a1, 2024-01-01, 30d
  Design: a2, after a1, 20d
  section Phase 2
  Build: a3, after a2, 45d
```

---

## Inline SVG Patterns

For custom graphics that don't need an icon library.

### Decorative dividers

**Hairline rule (editorial/minimal):**
```html
<svg class="divider" viewBox="0 0 200 1" xmlns="http://www.w3.org/2000/svg">
  <line x1="0" y1="0.5" x2="200" y2="0.5" stroke="currentColor" stroke-width="1"/>
</svg>
```

**Accent rule (40% width, colored):**
```html
<svg class="divider-accent" viewBox="0 0 100 2" xmlns="http://www.w3.org/2000/svg">
  <line x1="0" y1="1" x2="40" y2="1" stroke="var(--accent-color)" stroke-width="2"/>
</svg>
```

**Ornamental divider (art deco / classical):**
```html
<svg class="ornament" viewBox="0 0 120 12" xmlns="http://www.w3.org/2000/svg">
  <line x1="0" y1="6" x2="50" y2="6" stroke="currentColor" stroke-width="0.5"/>
  <circle cx="60" cy="6" r="3" fill="none" stroke="currentColor" stroke-width="0.5"/>
  <line x1="70" y1="6" x2="120" y2="6" stroke="currentColor" stroke-width="0.5"/>
</svg>
```

**Gold bars (brutalist luxury):**
```html
<div class="gold-bars">
  <span></span><span></span><span></span>
</div>
```
```css
.gold-bars { display: flex; gap: 4px; }
.gold-bars span { width: 14px; height: 3px; background: var(--accent-color); }
```

### Geometric shapes (Bauhaus / Constructivist)

```html
<svg width="24" height="24" viewBox="0 0 24 24">
  <circle cx="12" cy="12" r="10" fill="var(--accent-red)"/>
</svg>
<svg width="24" height="24" viewBox="0 0 24 24">
  <polygon points="12,2 22,22 2,22" fill="var(--accent-yellow)"/>
</svg>
<svg width="24" height="24" viewBox="0 0 24 24">
  <rect x="2" y="2" width="20" height="20" fill="var(--accent-blue)"/>
</svg>
```

### Arrow / pointer elements

```html
<svg class="arrow-right" viewBox="0 0 40 20" xmlns="http://www.w3.org/2000/svg">
  <line x1="0" y1="10" x2="32" y2="10" stroke="currentColor" stroke-width="1.5"/>
  <polyline points="28,5 35,10 28,15" fill="none" stroke="currentColor" stroke-width="1.5"/>
</svg>
```

---

## Number Indicators

For section numbering, step indicators, or ordered content:

```html
<span class="number-indicator">01</span>
```

```css
.number-indicator {
  font-family: var(--display-font);
  font-size: 14px;
  font-weight: 600;
  letter-spacing: 1px;
  color: var(--accent-color);
}
```

## Dot / Bullet Markers

```css
.custom-list {
  list-style: none;
  padding: 0;
}
.custom-list li {
  position: relative;
  padding-left: 20px;
}
.custom-list li::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0.6em;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--accent-color);
}
/* Editorial styles — em-dash instead */
.editorial-list li::before {
  content: '\2014';
  position: absolute;
  left: 0;
  color: var(--text-secondary);
  background: none;
  width: auto; height: auto; border-radius: 0;
}
```

## Quote Marks

```html
<div class="quote-block">
  <svg class="quote-mark" viewBox="0 0 32 32" width="48" height="48">
    <path d="M6 18h6l-4 8h6l4-8V6H6v12zm16 0h6l-4 8h6l4-8V6H22v12z" fill="var(--accent-color)" opacity="0.2"/>
  </svg>
  <blockquote>The quote text goes here.</blockquote>
  <cite>— Attribution Name</cite>
</div>
```

## Progress / Timeline Elements

```html
<div class="timeline">
  <div class="timeline-item">
    <div class="timeline-marker"></div>
    <div class="timeline-content">
      <strong>2023</strong>
      <p>Founded the company</p>
    </div>
  </div>
  <div class="timeline-item">
    <div class="timeline-marker active"></div>
    <div class="timeline-content">
      <strong>2024</strong>
      <p>Series A funding</p>
    </div>
  </div>
</div>
```

```css
.timeline {
  position: relative;
  padding-left: 32px;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 7px;
  top: 0; bottom: 0;
  width: 1px;
  background: var(--border-color);
}
.timeline-marker {
  position: absolute;
  left: -32px;
  top: 4px;
  width: 14px; height: 14px;
  border-radius: 50%;
  border: 2px solid var(--border-color);
  background: var(--bg-color);
}
.timeline-marker.active {
  border-color: var(--accent-color);
  background: var(--accent-color);
}
```

---

## Style-to-Element Mapping

| Style | Dividers | Icons | Markers | Code theme | Diagram theme |
|---|---|---|---|---|---|
| Minimalist | Hairline 1px | None or minimal | None | `default` | `neutral` |
| Editorial | Hairline + accent rule | Rare, small | Em-dash bullets | `github` | `neutral` |
| Swiss | 2px accent rule | None | Number indicators | `default` | `neutral` |
| Brutalist | 2-4px borders | Bold stroke | Gold bars / geometric | `monokai` | `dark` |
| Luxury | Gold hairline | Thin, accent color | Dot markers | `github-dark` | `dark` |
| Bauhaus | Geometric shapes | Circle/square/triangle | Shape markers | `default` | `neutral` |
| Warm | Soft dividers | Friendly, standard | Dot bullets | `github` | `neutral` |
| Expressive | Mixed, playful | Varies | Creative | `monokai` | `neutral` |
| Futuristic | Grid lines | Tech-themed | Number indicators | `tokyo-night-dark` | `dark` |
