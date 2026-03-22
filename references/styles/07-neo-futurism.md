---
name: Neo-Futurism
category: aesthetica
suitable_for: slides
---

# Neo-Futurism

## Visual Direction
The design language of parametric architecture and computational space: a near-black void (#06060e) activated by electric blue light. Concentric arcs bleed in from the right edge, suggesting orbital trajectories or the rings of a computational model. A parametric grid of 60px squares in rgba(0,160,255,0.03) covers the entire field — barely visible, but establishing a system. Typography is set in Orbitron, the quintessential geometric display font for interfaces that imagine futures. Headlines are gradient-mapped from white to electric blue (#00a0ff), creating the impression of text illuminated from within. The palette is a strict triad: void black, pure white, and a single electric blue. This is a presentation that belongs in a mission control room.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #06060e | Deep void — near-black with a barely perceptible blue cast |
| Text Primary | #ffffff | Pure white for primary text |
| Text Secondary | rgba(255,255,255,0.4) | Ghosted white for body copy |
| Text Tertiary | rgba(255,255,255,0.35) | Further ghosted for supporting card text |
| Electric Blue | #00a0ff | The single accent hue — used for glows, borders, labels |
| Blue Accent (muted) | rgba(0,160,255,0.4) | Orbitron labels, data labels, at 40% opacity |
| Grid Lines | rgba(0,160,255,0.03) | Near-invisible parametric grid — present but felt |
| Data Cell Border | rgba(0,160,255,0.08) | Hairline borders on data cells and cards |

## Typography

### Display Font
- **Family:** Orbitron
- **Weights:** 800 (headlines), 400–500 (labels and section numbers)
- **Size Range:** 36–64px; clamp(36px, 4.5vw, 64px)
- **Letter Spacing:** 0.06em on headlines; 0.25–0.5em on labels and tags
- **Style Notes:** Headlines use a CSS gradient text effect: linear-gradient(135deg, #fff 40%, rgba(0,160,255,0.7)) — white transitioning to electric blue. This cannot be achieved with a flat color; the gradient is load-bearing. All labels and tags in Orbitron are uppercase.

### Body Font
- **Family:** Exo 2
- **Weights:** 300 (body and card text)
- **Size Range:** 12–13px
- **Line Height:** 1.8–2.0
- **Style Notes:** Exo 2 at weight 300 creates a technical but readable body copy. Never use weights above 400 for body. Data labels within cells use Orbitron 8px at 0.25em tracking.

## Design Principles
1. All light in this system comes from one source: the electric blue (#00a0ff) — every glow, border highlight, and gradient traces back to it.
2. Layering creates depth: the parametric grid is the base, arcs sit above it, content above that. Each layer is at a lower opacity than the last.
3. Typography grades from white (highest importance) through progressively ghosted values down to rgba(255,255,255,0.35) — importance is communicated through luminosity.
4. Data is the hero: use the data-cell grid system for any statistics or specifications, with Orbitron labels and Exo 2 values.
5. Motion potential is always implied: concentric arcs suggest orbit, grid suggests computation, gradient text suggests illumination — even in static slides.

## Slide Application Notes
- **Title Slides:** Orbitron 800 headline with gradient text treatment, centered or left-aligned. Orbitron 9px section tag in electric blue at 45% opacity above. Body paragraph in Exo 2 300 at rgba(255,255,255,0.4). Arcs bleeding from the right edge for visual depth.
- **Content Slides:** Two-column asymmetric grid (1.3fr : 1fr). Left: headline + body + 2×2 data-cell grid. Right: two or three "fut-cards" — bordered cards with Orbitron labels and Exo 2 body text. All card borders at rgba(0,160,255,0.06).
- **Data/Chart Slides:** 2×2 or 2×3 data-cell grid. Each cell: Orbitron label at 8px uppercase above the value. Values in Exo 2 300. Cell background rgba(0,160,255,0.02), border rgba(0,160,255,0.08). For line charts: single #00a0ff stroke on a dark field, no fill under the line.
- **Closing Slides:** Full-bleed background with arc elements. Single large Orbitron headline with gradient treatment. One Exo 2 body line below. No data elements.
- **Do:** Maintain the void black background as absolute — no other background colors; use rgba opacity steps to create hierarchy without introducing new hues; keep the concentric arc motif on every slide as a system identifier.
- **Don't:** Add warm colors or earth tones; use font weights above 800 or below 300; fill the data cells with solid backgrounds; use more than one accent hue.
