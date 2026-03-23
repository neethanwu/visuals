---
name: Apple Liquid Glass
category: aesthetica
suitable_for: slides
---

# Apple Liquid Glass

## Visual Direction
Multi-layered translucent panels floating over a rich background — the design language of iOS 26 and macOS 26. Every surface is semi-transparent with `backdrop-filter: blur()`, creating depth through layered glass rather than solid cards. Panels have a subtle 1px border in white at 15-20% opacity and a faint inner light along the top edge. The background beneath the glass is always colorful and alive — a soft gradient mesh, a blurred image, or a gentle animated gradient — so the translucency has something to reveal. Typography is clean, lightweight, and modern — SF Pro or equivalent sans-serif. Colors are restrained on the glass surfaces (white/near-white text and icons) while the background carries the color personality. The overall feel is premium, modern, and spatially deep.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background Gradient Start | #1a1a2e | Deep midnight blue — gradient mesh base |
| Background Gradient Mid | #2d1b4e | Deep purple — gradient mesh middle |
| Background Gradient End | #0d2137 | Dark teal-navy — gradient mesh edge |
| Glass Fill | rgba(255,255,255,0.08) | White at 8% — the glass panel surface |
| Glass Border | rgba(255,255,255,0.18) | White at 18% — the panel edge |
| Glass Highlight | rgba(255,255,255,0.12) | White at 12% — top-edge inner glow |
| Text Primary | #ffffff | Pure white — on glass panels |
| Text Secondary | rgba(255,255,255,0.65) | White at 65% — for body and metadata |
| Accent | #64d2ff | Light blue — system accent, used sparingly |
| Surface Elevated | rgba(255,255,255,0.12) | Brighter glass — for hovered/active states |

## Typography

### Display Font
- **Family:** Inter or Geist Sans
- **Weights:** 500, 600
- **Size Range:** 48–96px; clamp(48px, 6vw, 96px)
- **Letter Spacing:** -0.02em (slightly tight)
- **Style Notes:** Medium weight preferred — not bold. The lightweight feel is essential. Headlines are white on glass, never colored. Line height 1.1.

### Body Font
- **Family:** Inter or Geist Sans
- **Weights:** 400
- **Size Range:** 14-18px
- **Line Height:** 1.5
- **Style Notes:** Regular weight only. Text Secondary (65% white) for body text. Generous line-height for readability against the translucent background.

## Design Principles
1. **Glass is the medium.** Every card, panel, and container uses `backdrop-filter: blur(20px)` with a semi-transparent white fill. The blur radius (16-24px) controls how much of the background bleeds through — more blur = more frosted, less = more transparent.
2. **The background must be rich.** Plain solid backgrounds kill the glass effect. Always use a gradient mesh (2-3 radial gradients overlapping), a blurred image, or an animated gradient. The background is what gives the glass its character.
3. **Layered depth, not flat.** Stack glass panels at different opacity levels to create spatial depth. A higher panel (closer to viewer) gets slightly more opaque glass. Use `z-index` and subtle `box-shadow: 0 8px 32px rgba(0,0,0,0.2)` for depth.
4. **Restraint in color.** The glass surfaces are near-colorless (white-tinted). Color lives in the background gradient and in one system accent (light blue). Don't tint the glass panels in bright colors.
5. **1px border is essential.** Without the subtle white border, glass panels merge into the background. The border at 15-20% opacity defines the panel edge.

## Slide Application Notes
- **Title Slides:** Full-bleed animated gradient mesh background. Title in large white type floating over the gradient — no glass panel behind the title itself. A glass pill or card below with subtitle/metadata. The gradient should have gentle movement (CSS animation).
- **Content Slides:** Background gradient (static or animated). Content inside one or two glass panels. Glass panels have 20-24px border-radius, 1px white border, 20px backdrop-blur. Generous padding (32-48px).
- **Data/Chart Slides:** Chart sits inside a glass panel. Chart colors use the accent blue + white. Axis labels in Text Secondary. The glass panel gives the chart a contained, premium feel.
- **Metrics/KPI Slides:** Individual metric cards as small glass panels arranged in a row. Each panel: icon or label at top, large number, delta below. The glass cards float over the gradient.
- **Closing Slides:** Minimal — large white title floating over the gradient mesh. Glass pill with contact info below. Clean and spatial.
- **Do:** Always have a colorful background behind the glass; maintain consistent blur radius across panels; use the 1px border on every glass surface; keep text white/near-white on glass.
- **Don't:** Use glass on solid flat backgrounds (it looks broken); tint glass panels in bright colors; use heavy bold weights (kills the lightweight feel); stack too many glass layers (gets muddy).
