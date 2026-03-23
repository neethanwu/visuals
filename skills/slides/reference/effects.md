# Visual Effects Reference

Self-contained visual effects for slide backgrounds. All effects run in a `<canvas>` element positioned behind slide content, or as pure CSS overlays. No build step required — pure inline JavaScript/GLSL.

## When to Use Effects

| Effect level | When | Styles |
|---|---|---|
| **None** | Restrained styles, content-focused decks | Minimalist, Editorial Calm, Swiss Clean, Conceptual Art, Blueprint |
| **CSS only** | Subtle texture or gradient | Editorial styles, Corporate, Warm styles, Risograph, Pop Art |
| **Canvas/WebGL** | Immersive, atmospheric, futuristic | Neo-Futurism, Dark Classy, Color Field, Synthwave, Glitch Art, Apple Liquid Glass |

**Rule: If the style's design principles say "no decoration" or "typography only," do not add effects.**

## CSS-Only Effects (No JavaScript)

### Subtle Grain Texture

```css
.slide-bg-grain::before {
  content: '';
  position: fixed;
  inset: 0;
  opacity: 0.03;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 0;
}
```
**Good for:** Elegant Luxury, Dark Classy, Brutalist Luxury, Editorial Financial

### Soft Gradient Wash

```css
.slide-bg-gradient {
  background:
    radial-gradient(ellipse at 20% 50%, rgba(var(--accent-rgb), 0.06) 0%, transparent 60%),
    radial-gradient(ellipse at 80% 20%, rgba(var(--accent-rgb), 0.04) 0%, transparent 50%),
    var(--bg-color);
}
```
**Good for:** Editorial Warm, Color Field, Art Deco

### Animated Gradient Mesh (CSS only)

```css
@keyframes meshDrift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}
.slide-bg-mesh {
  background: linear-gradient(-45deg, var(--color-1), var(--color-2), var(--color-3), var(--color-4));
  background-size: 400% 400%;
  animation: meshDrift 20s ease infinite;
}
```
**Good for:** Color Field, Neo-Expressionism (use muted palette)

### Grid Overlay

```css
.slide-bg-grid::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image:
    linear-gradient(rgba(var(--grid-rgb), 0.05) 1px, transparent 1px),
    linear-gradient(90deg, rgba(var(--grid-rgb), 0.05) 1px, transparent 1px);
  background-size: 60px 60px;
  pointer-events: none;
  z-index: 0;
}
```
**Good for:** Neo-Futurism, Bauhaus Digital, Swiss Clean Expressive

## Canvas/WebGL Effects

### Setup Pattern

All canvas effects follow this pattern. Place the canvas behind the slides:

```html
<canvas id="bg-effect" style="position:fixed;inset:0;z-index:0;pointer-events:none;"></canvas>
<!-- Slides need position:relative;z-index:1 -->

<script>
  const canvas = document.getElementById('bg-effect');
  const ctx = canvas.getContext('2d'); // or 'webgl2'
  function resize() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  }
  window.addEventListener('resize', resize);
  resize();

  function animate() {
    // drawing logic here
    requestAnimationFrame(animate);
  }
  animate();
</script>
```

### Particle Drift (Canvas 2D)

Gentle floating particles. Works without WebGL.

```js
// After canvas setup
const particles = Array.from({length: 60}, () => ({
  x: Math.random() * canvas.width,
  y: Math.random() * canvas.height,
  r: Math.random() * 2 + 0.5,
  vx: (Math.random() - 0.5) * 0.3,
  vy: (Math.random() - 0.5) * 0.3,
  alpha: Math.random() * 0.3 + 0.1
}));

function animate() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  particles.forEach(p => {
    p.x += p.vx; p.y += p.vy;
    if (p.x < 0) p.x = canvas.width;
    if (p.x > canvas.width) p.x = 0;
    if (p.y < 0) p.y = canvas.height;
    if (p.y > canvas.height) p.y = 0;
    ctx.beginPath();
    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(255,255,255,${p.alpha})`;
    ctx.fill();
  });
  requestAnimationFrame(animate);
}
animate();
```
**Good for:** Neo-Futurism (blue-tinted), Dark Classy (warm orange), Elegant Luxury (gold)

### Noise Field (WebGL Shader)

Organic, slow-moving noise texture as background.

```js
// WebGL setup
const gl = canvas.getContext('webgl2');
const vsSource = `#version 300 es
  in vec4 a_position;
  void main() { gl_Position = a_position; }`;

const fsSource = `#version 300 es
  precision highp float;
  uniform float u_time;
  uniform vec2 u_resolution;
  out vec4 fragColor;

  // Simplex noise
  vec3 mod289(vec3 x) { return x - floor(x * (1.0/289.0)) * 289.0; }
  vec2 mod289(vec2 x) { return x - floor(x * (1.0/289.0)) * 289.0; }
  vec3 permute(vec3 x) { return mod289(((x*34.0)+1.0)*x); }
  float snoise(vec2 v) {
    const vec4 C = vec4(0.211324865405187, 0.366025403784439,
                        -0.577350269189626, 0.024390243902439);
    vec2 i = floor(v + dot(v, C.yy));
    vec2 x0 = v - i + dot(i, C.xx);
    vec2 i1 = (x0.x > x0.y) ? vec2(1.0, 0.0) : vec2(0.0, 1.0);
    vec4 x12 = x0.xyxy + C.xxzz;
    x12.xy -= i1;
    i = mod289(i);
    vec3 p = permute(permute(i.y + vec3(0.0, i1.y, 1.0)) + i.x + vec3(0.0, i1.x, 1.0));
    vec3 m = max(0.5 - vec3(dot(x0,x0), dot(x12.xy,x12.xy), dot(x12.zw,x12.zw)), 0.0);
    m = m*m; m = m*m;
    vec3 x = 2.0 * fract(p * C.www) - 1.0;
    vec3 h = abs(x) - 0.5;
    vec3 ox = floor(x + 0.5);
    vec3 a0 = x - ox;
    m *= 1.79284291400159 - 0.85373472095314 * (a0*a0 + h*h);
    vec3 g;
    g.x = a0.x * x0.x + h.x * x0.y;
    g.yz = a0.yz * x12.xz + h.yz * x12.yw;
    return 130.0 * dot(m, g);
  }

  void main() {
    vec2 uv = gl_FragCoord.xy / u_resolution;
    float n = snoise(uv * 3.0 + u_time * 0.05);
    n = n * 0.5 + 0.5;
    // Adjust base color to match your style palette
    vec3 color = mix(vec3(0.04), vec3(0.08), n);
    fragColor = vec4(color, 1.0);
  }`;

// Compile, link, draw fullscreen quad — standard WebGL boilerplate
function createShader(gl, type, source) {
  const s = gl.createShader(type);
  gl.shaderSource(s, source);
  gl.compileShader(s);
  return s;
}
const vs = createShader(gl, gl.VERTEX_SHADER, vsSource);
const fs = createShader(gl, gl.FRAGMENT_SHADER, fsSource);
const program = gl.createProgram();
gl.attachShader(program, vs); gl.attachShader(program, fs);
gl.linkProgram(program); gl.useProgram(program);

const buf = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, buf);
gl.bufferData(gl.ARRAY_BUFFER, new Float32Array([-1,-1, 1,-1, -1,1, 1,1]), gl.STATIC_DRAW);
const loc = gl.getAttribLocation(program, 'a_position');
gl.enableVertexAttribArray(loc);
gl.vertexAttribPointer(loc, 2, gl.FLOAT, false, 0, 0);

const uTime = gl.getUniformLocation(program, 'u_time');
const uRes = gl.getUniformLocation(program, 'u_resolution');

function render(t) {
  gl.uniform1f(uTime, t * 0.001);
  gl.uniform2f(uRes, canvas.width, canvas.height);
  gl.drawArrays(gl.TRIANGLE_STRIP, 0, 4);
  requestAnimationFrame(render);
}
requestAnimationFrame(render);
```
**Good for:** Neo-Futurism, Dark Classy, Color Field (adjust colors in shader)

### Aurora / Color Bands (WebGL Shader)

Flowing color bands for Color Field or expressive styles. Replace the fragment shader above with:

```glsl
void main() {
  vec2 uv = gl_FragCoord.xy / u_resolution;
  float t = u_time * 0.08;

  // Three color bands with sine-wave boundaries
  float band1 = smoothstep(0.0, 0.05, sin(uv.y * 3.14159 + t) * 0.15 + 0.33 - uv.y);
  float band2 = smoothstep(0.0, 0.05, sin(uv.y * 3.14159 + t + 1.0) * 0.15 + 0.66 - uv.y);

  // Adjust these colors to match your style
  vec3 c1 = vec3(0.85, 0.31, 0.0);  // warm orange
  vec3 c2 = vec3(0.55, 0.23, 0.1);  // deep brown
  vec3 c3 = vec3(0.1, 0.23, 0.42);  // deep blue

  vec3 color = mix(c3, mix(c2, c1, band2), band1);
  fragColor = vec4(color, 1.0);
}
```
**Good for:** Color Field (use the style's three-band palette), Art Deco (gold/bronze tones)

### Geometric Grid Pulse (Canvas 2D)

Animated grid that subtly pulses. No WebGL required.

```js
function animate(t) {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  const gridSize = 60;
  const cols = Math.ceil(canvas.width / gridSize) + 1;
  const rows = Math.ceil(canvas.height / gridSize) + 1;

  ctx.strokeStyle = 'rgba(0, 160, 255, 0.04)';
  ctx.lineWidth = 1;

  for (let i = 0; i < cols; i++) {
    for (let j = 0; j < rows; j++) {
      const x = i * gridSize;
      const y = j * gridSize;
      const pulse = Math.sin(t * 0.001 + i * 0.3 + j * 0.3) * 0.02 + 0.04;
      ctx.strokeStyle = `rgba(0, 160, 255, ${pulse})`;
      ctx.strokeRect(x, y, gridSize, gridSize);
    }
  }
  requestAnimationFrame(animate);
}
requestAnimationFrame(animate);
```
**Good for:** Neo-Futurism, Bauhaus Digital

### Scan Line Overlay (CSS — for Glitch Art, Synthwave)

```css
.slide-bg-scanlines::after {
  content: '';
  position: fixed;
  inset: 0;
  background: repeating-linear-gradient(
    0deg,
    rgba(255, 255, 255, 0.03) 0px,
    rgba(255, 255, 255, 0.03) 1px,
    transparent 1px,
    transparent 4px
  );
  pointer-events: none;
  z-index: 2;
}
```
**Good for:** Glitch Art (mandatory), Synthwave (optional, low opacity)

### Halftone Dot Texture (CSS — for Risograph, Pop Art)

```css
.slide-bg-halftone::before {
  content: '';
  position: fixed;
  inset: 0;
  background: radial-gradient(circle, var(--halftone-color, rgba(227,52,47,0.12)) 1px, transparent 1px);
  background-size: 6px 6px;
  pointer-events: none;
  z-index: 0;
}
```
**Good for:** Risograph (mandatory), Pop Art (on color blocks)

### Perspective Grid (CSS — for Synthwave)

```css
.perspective-grid {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  height: 50vh;
  background:
    repeating-linear-gradient(90deg, rgba(255,42,109,0.15) 0px, transparent 1px, transparent 60px),
    repeating-linear-gradient(0deg, rgba(255,42,109,0.1) 0px, transparent 1px, transparent 40px);
  transform: perspective(400px) rotateX(60deg);
  transform-origin: bottom;
  z-index: 0;
}
```
**Good for:** Synthwave (title and closing slides)

### Animated Gradient Mesh (CSS — for Apple Liquid Glass)

```css
@keyframes meshShift {
  0%, 100% { background-position: 0% 50%, 100% 50%, 50% 0%; }
  33% { background-position: 100% 0%, 0% 100%, 50% 100%; }
  66% { background-position: 50% 100%, 50% 0%, 0% 50%; }
}
.glass-bg {
  background:
    radial-gradient(ellipse at 20% 50%, rgba(100, 100, 255, 0.3) 0%, transparent 50%),
    radial-gradient(ellipse at 80% 20%, rgba(200, 100, 255, 0.2) 0%, transparent 40%),
    radial-gradient(ellipse at 50% 80%, rgba(100, 200, 255, 0.2) 0%, transparent 50%),
    linear-gradient(135deg, #1a1a2e, #2d1b4e, #0d2137);
  background-size: 200% 200%, 200% 200%, 200% 200%, 100% 100%;
  animation: meshShift 20s ease infinite;
}
```
**Good for:** Apple Liquid Glass (mandatory — glass panels need a rich background)

## Style-to-Effect Mapping

| Style | Recommended effect | Level |
|---|---|---|
| 01-minimalist | None | — |
| 03-constructivist | None | — |
| 04-deconstructivist | Subtle grain | CSS |
| 05-neo-expressionism | Animated gradient mesh (muted) | CSS |
| 06-neo-classicism | None | — |
| 07-neo-futurism | Grid pulse + particle drift | Canvas |
| 08-neo-brutalism | None or grain | CSS |
| 10-bauhaus | None | — |
| 12-art-deco | Soft gradient wash (gold) | CSS |
| 16-contemporary-collage | Subtle grain | CSS |
| 17-op-art | None (patterns are the content) | — |
| 18-conceptual-art | None | — |
| 20-color-field | Aurora bands or gradient mesh | WebGL/CSS |
| p-japanese-swiss-mono | None | — |
| p-elegant-luxury | Grain texture | CSS |
| p-brutalist-luxury | Grain texture | CSS |
| p-swiss-elegant | None | — |
| p-bauhaus-digital | Grid overlay | CSS |
| p-editorial-financial | None | — |
| p-nordic-brutalist | None | — |
| p-nordic-brutalist-v2 | None | — |
| p-dark-classy | Noise field or particle drift | WebGL/Canvas |
| p-swiss-clean-expressive | None | — |
| p-editorial-warm | None | — |
| p-industrial-humanist | None | — |
| p-editorial-calm | None | — |
| p-monochrome-expressive | None | — |
| p-editorial-data | None | — |
| p-swiss-clean | None | — |
| p-minimal-corporate | Subtle grain (dark slides only) | CSS |
| p-brutalist-luxury-v2 | Grain texture | CSS |
| risograph | Halftone dot texture | CSS |
| synthwave | Perspective grid + scan lines (optional) | CSS |
| apple-liquid-glass | Animated gradient mesh (mandatory) | CSS |
| pop-art | Halftone dots on color blocks | CSS |
| glitch-art | Scan lines + RGB split (on text via text-shadow) | CSS |
| blueprint | Grid overlay (always present) | CSS |

## Performance Notes

- All canvas effects should check `requestAnimationFrame` availability
- Pause canvas animations when slides are not visible using IntersectionObserver
- WebGL shaders run on GPU — they don't block the main thread
- Keep particle counts under 100 for smooth 60fps
- Use `will-change: transform` on animated CSS elements
- Test on low-end devices — reduce effect complexity if needed
