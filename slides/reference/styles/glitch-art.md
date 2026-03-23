---
name: Glitch Art
category: aesthetica
suitable_for: slides
---

# Glitch Art

## Visual Direction
Digital corruption as aesthetic: RGB color channel separation, horizontal scan lines, pixel displacement, and the visual language of broken data. The base is dark — near-black or very dark grey — with content that appears to be malfunctioning. Headlines are duplicated in offset cyan and red (mimicking RGB split), scan lines stripe across the viewport at low opacity, and key elements occasionally shift or fragment. The effect is controlled chaos — enough to feel intentional and artistic, not actually broken. Typography is monospaced or geometric sans-serif, often with the RGB split applied via CSS `text-shadow`. This works for tech talks about disruption, AI/ML presentations, cybersecurity topics, creative technology, and anything that benefits from an edgy, digital-native aesthetic.

## Color Palette

| Role | Hex | Description |
|------|-----|-------------|
| Background | #0a0a0a | Near-black — the void behind the glitch |
| Surface | #141414 | Slightly lighter — for elevated panels |
| Text Primary | #e0e0e0 | Off-white — the clean signal |
| Text Secondary | #666666 | Mid-grey — for metadata and captions |
| Glitch Red | #ff0040 | The red channel — offset right |
| Glitch Cyan | #00ffff | The cyan/green channel — offset left |
| Glitch Blue | #0040ff | Blue channel — for tertiary effects |
| Scan Line | #ffffff | White at 3-5% opacity — horizontal stripes |
| Accent | #ff0040 | Red serves as the primary accent when not glitching |

## Typography

### Display Font
- **Family:** Space Mono or IBM Plex Mono
- **Weights:** 700
- **Size Range:** 56–120px; clamp(56px, 8vw, 120px)
- **Letter Spacing:** 0.02em
- **Style Notes:** The RGB split is the defining typographic effect. Apply via CSS `text-shadow`: `2px 0 #ff0040, -2px 0 #00ffff`. On key slides, increase the offset to 4-6px for more dramatic effect. Headlines in mono or bold sans-serif. All-caps optional.

### Body Font
- **Family:** IBM Plex Mono or Space Grotesk
- **Weights:** 400
- **Size Range:** 14-18px
- **Line Height:** 1.6
- **Style Notes:** Mono preferred for consistency with the digital-corruption theme. Body text does NOT get the RGB split — keep it clean and readable.

## Design Principles
1. **RGB split is the signature.** The offset red and cyan `text-shadow` on headlines is the most recognizable glitch element. It's applied to display text and key accent elements, never to body text.
2. **Scan lines create atmosphere.** A full-viewport CSS overlay of thin horizontal lines (1px lines every 3-4px) at 3-5% opacity creates the CRT/screen texture. Use `repeating-linear-gradient(0deg, rgba(255,255,255,0.03) 0px, rgba(255,255,255,0.03) 1px, transparent 1px, transparent 4px)`.
3. **Controlled corruption, not chaos.** One or two glitch effects per slide. The content must be readable. The glitch is aesthetic frosting, not actual dysfunction. Body text, data, and charts are always clean.
4. **Dark backgrounds only.** The glitch effects depend on dark backgrounds for the RGB channels to read. Light backgrounds kill the aesthetic.
5. **Horizontal displacement.** Key decorative elements can use `clip-path` or `transform: translateX()` to create horizontal slice displacement — sections of an element shifted left or right by 4-8px.

## Slide Application Notes
- **Title Slides:** Large headline with RGB split text-shadow (4-6px offset). Scan line overlay across the full slide. A horizontal displacement effect on one decorative element (a line, a shape, or part of the headline). Subtitle in clean body font below.
- **Content Slides:** Clean, readable content on dark background. RGB split applied to the heading only. Scan lines at reduced opacity (2-3%). A thin glitch-red horizontal line as a section divider.
- **Data/Chart Slides:** Charts rendered cleanly — data integrity matters. Chart accent colors use Glitch Red and Glitch Cyan. The chart container can have a subtle scan line overlay. Axis labels in mono font.
- **Code Slides:** Code blocks on dark surface (#141414) with red and cyan syntax highlighting. No RGB split on code — readability first. A subtle scan line overlay on the code block.
- **Section Dividers:** Large section number or title with aggressive RGB split (6-8px). A horizontal displacement stripe across the middle of the slide. Dark background with scan lines.
- **Closing Slides:** Headline with RGB split. Clean contact info in mono below. Scan line overlay. Minimal — let the glitch effect be the statement.
- **Do:** Apply RGB split to headlines consistently; use scan lines as atmospheric texture; keep body text and data clean; maintain dark backgrounds.
- **Don't:** Glitch body text (unreadable); use light backgrounds; overdo the displacement (looks actually broken); apply every effect to every slide (restraint within chaos).
