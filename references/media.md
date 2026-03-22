# Media & Assets Reference

Handling images, video, and user-provided assets in single-file HTML slides.

## Images

### User-provided images

When users provide images, they may give:
- **File paths** — reference directly with relative/absolute paths
- **URLs** — use directly in `src`
- **Base64** — only for small images (logos, icons < 50KB). Never base64-encode large photos.

### Image slide patterns

**Full-bleed background image:**
```html
<section data-background-image="path/to/image.jpg" data-background-size="cover" data-background-position="center">
  <div class="image-overlay">
    <h2>Headline Over Image</h2>
  </div>
</section>
```

```css
.image-overlay {
  background: linear-gradient(to top, rgba(0,0,0,0.7) 0%, transparent 60%);
  padding: 60px;
  display: flex;
  align-items: flex-end;
  height: 100%;
  width: 100%;
}
.image-overlay h2 {
  color: #fff;
  text-shadow: 0 2px 8px rgba(0,0,0,0.3);
}
```

**Image + text side-by-side:**
```html
<section>
  <div class="split-layout">
    <div class="split-image">
      <img src="path/to/image.jpg" alt="Description">
    </div>
    <div class="split-content">
      <h2>Heading</h2>
      <p>Body text alongside the image.</p>
    </div>
  </div>
</section>
```

```css
.split-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  height: 100%;
  align-items: center;
}
.split-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

**Framed image with caption (editorial styles):**
```html
<section>
  <figure class="framed-image">
    <img src="path/to/image.jpg" alt="Description">
    <figcaption>Caption text — Source attribution</figcaption>
  </figure>
</section>
```

```css
.framed-image {
  max-width: 80%;
  margin: 0 auto;
}
.framed-image img {
  width: 100%;
  display: block;
}
.framed-image figcaption {
  font-family: var(--body-font);
  font-size: 12px;
  color: var(--text-secondary);
  margin-top: 12px;
  padding-top: 8px;
  border-top: 1px solid var(--border-color);
}
```

**Image grid (portfolio / gallery):**
```html
<section>
  <div class="image-grid">
    <img src="image1.jpg" alt="">
    <img src="image2.jpg" alt="">
    <img src="image3.jpg" alt="">
    <img src="image4.jpg" alt="">
  </div>
</section>
```

```css
.image-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  max-width: 85%;
  margin: 0 auto;
}
.image-grid img {
  width: 100%;
  aspect-ratio: 4/3;
  object-fit: cover;
}
```

### Image styling per style category

| Style category | Image treatment |
|---|---|
| Editorial | Framed with caption, 1px border optional, restrained sizing |
| Swiss / Minimal | No frame, flush edges, generous whitespace around |
| Brutalist | Hard edges, 2-4px border, no rounded corners |
| Luxury / Dark | Full-bleed with dark overlay, or inset with generous padding |
| Warm / Humanist | Soft treatment, generous caption space, rounded corners if style permits |
| Expressive | Overlapping, rotated, or collage-style placement |

### Responsive images

```css
/* Always constrain images within slides */
.reveal img {
  max-width: 100%;
  height: auto;
}

/* Prevent images from overflowing slide bounds */
.reveal section img {
  max-height: 70vh;
  object-fit: contain;
}
```

## Video

### Embedding video in slides

**Local/hosted video:**
```html
<section>
  <video class="slide-video" autoplay muted loop playsinline>
    <source src="video.mp4" type="video/mp4">
  </video>
</section>
```

**Video as slide background:**
```html
<section data-background-video="video.mp4"
         data-background-video-loop
         data-background-video-muted
         data-background-size="cover">
  <h2>Content over video</h2>
</section>
```

**YouTube/Vimeo embed:**
```html
<section>
  <div class="video-embed">
    <iframe src="https://www.youtube.com/embed/VIDEO_ID"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope"
            allowfullscreen></iframe>
  </div>
</section>
```

```css
.video-embed {
  position: relative;
  width: 80%;
  margin: 0 auto;
  aspect-ratio: 16/9;
}
.video-embed iframe {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
}
```

### Video controls with Reveal.js

```js
// Auto-play video when slide is shown, pause when navigated away
Reveal.on('slidechanged', event => {
  // Pause all videos on previous slide
  if (event.previousSlide) {
    event.previousSlide.querySelectorAll('video').forEach(v => v.pause());
  }
  // Play videos on current slide
  event.currentSlide.querySelectorAll('video[autoplay]').forEach(v => v.play());
});
```

## Logos & Brand Assets

### Logo placement

```html
<!-- Persistent logo across all slides (bottom-right) -->
<div class="slide-logo">
  <img src="logo.svg" alt="Company">
</div>
```

```css
.slide-logo {
  position: fixed;
  bottom: 24px;
  right: 32px;
  z-index: 10;
  opacity: 0.6;
}
.slide-logo img {
  height: 28px;
  width: auto;
}
```

### Logo on title/closing slides

```css
/* Larger logo treatment on title slides */
.title-slide .logo {
  height: 48px;
  margin-bottom: 24px;
  opacity: 1;
}
```

## Screenshots & App UI

For product screenshots or UI captures:

```css
/* Browser-style frame */
.screenshot-frame {
  background: var(--surface-color, #f5f5f5);
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 24px rgba(0,0,0,0.12);
}
.screenshot-frame::before {
  content: '';
  display: block;
  height: 32px;
  background: var(--border-color, #e5e5e5);
  background-image:
    radial-gradient(circle at 20px 16px, #ff5f57 5px, transparent 5px),
    radial-gradient(circle at 40px 16px, #febc2e 5px, transparent 5px),
    radial-gradient(circle at 60px 16px, #28c840 5px, transparent 5px);
}
.screenshot-frame img {
  width: 100%;
  display: block;
}
```

## Accessibility Notes

- Always provide meaningful `alt` text for content images
- Decorative images: `alt=""`
- Video: provide captions if possible
- Ensure sufficient contrast when placing text over images (use overlays)
- Don't rely on images alone to convey critical information
