# Example Output

A minimal but complete working slide deck showing the correct structure, load order, theming, and patterns. The agent should use this as a pattern to follow — not copy verbatim, but match the architecture.

This example uses the Swiss Elegant style with the `editorial` font trio.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Q4 Revenue Analysis</title>

  <!-- 1. Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,500;0,700;1,500&family=Source+Serif+4:wght@400;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">

  <!-- 2. Reveal.js CSS -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/theme/white.css">

  <!-- 3. Custom styles (after Reveal.js CSS) -->
  <style>
    :root {
      --display-font: 'Playfair Display', serif;
      --body-font: 'Source Serif 4', serif;
      --mono-font: 'JetBrains Mono', monospace;
      --text-primary: #0F0F0F;
      --text-secondary: #6B6B6B;
      --bg-color: #FAFAF7;
      --surface-color: #FFFFFF;
      --accent-color: #C41E3A;
      --border-color: #E0E0E0;
      --color-positive: #2D7A4F;
      --color-negative: #C41E3A;
    }

    /* Override Reveal.js defaults */
    .reveal {
      font-family: var(--body-font);
      color: var(--text-primary);
      background: var(--bg-color);
    }
    .reveal h1, .reveal h2, .reveal h3 {
      font-family: var(--display-font);
      font-weight: 500;
      letter-spacing: -0.02em;
      color: var(--text-primary);
    }
    .reveal h1 { font-size: 72px; line-height: 1.1; }
    .reveal h2 { font-size: 48px; line-height: 1.2; }
    .reveal h3 { font-size: 28px; line-height: 1.3; }
    .reveal p, .reveal li {
      font-size: 22px;
      line-height: 1.6;
      color: var(--text-primary);
    }
    .reveal .text-secondary { color: var(--text-secondary); }

    /* Accent rule beneath headings */
    .accent-rule {
      width: 40%;
      height: 2px;
      background: var(--accent-color);
      border: none;
      margin: 16px 0 32px 0;
    }

    /* Section label */
    .section-label {
      font-family: var(--body-font);
      font-size: 13px;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 2px;
      color: var(--text-secondary);
      margin-bottom: 12px;
    }

    /* Metrics row */
    .metrics-row {
      display: flex;
      gap: 60px;
      justify-content: center;
      margin-top: 40px;
    }
    .metric-card {
      display: flex;
      flex-direction: column;
      gap: 4px;
      text-align: center;
    }
    .metric-label {
      font-family: var(--mono-font);
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      color: var(--text-secondary);
    }
    .metric-value {
      font-family: var(--display-font);
      font-size: 56px;
      font-weight: 700;
      line-height: 1;
      color: var(--text-primary);
    }
    .metric-delta {
      font-family: var(--mono-font);
      font-size: 14px;
      font-weight: 500;
    }
    .metric-delta.positive { color: var(--color-positive); }
    .metric-delta.negative { color: var(--color-negative); }

    /* Two-column layout */
    .split {
      display: grid;
      grid-template-columns: 1.3fr 1fr;
      gap: 60px;
      text-align: left;
      align-items: center;
      height: 100%;
      padding: 40px 0;
    }
    .split-wide { grid-template-columns: 1fr 1fr; }

    /* Styled list */
    .reveal .styled-list {
      list-style: none;
      padding: 0;
    }
    .reveal .styled-list li {
      position: relative;
      padding-left: 20px;
      padding-bottom: 12px;
      border-bottom: 1px solid var(--border-color);
      margin-bottom: 12px;
    }
    .reveal .styled-list li::before {
      content: '\2014';
      position: absolute;
      left: 0;
      color: var(--text-secondary);
    }

    /* Chart container */
    .chart-container {
      width: 700px;
      height: 400px;
      margin: 24px auto 0;
    }

    /* Quote */
    .reveal blockquote {
      font-family: var(--display-font);
      font-style: italic;
      font-size: 32px;
      line-height: 1.5;
      border-left: 2px solid var(--accent-color);
      padding-left: 32px;
      margin: 0;
      max-width: 75%;
      text-align: left;
    }
    .reveal cite {
      font-family: var(--body-font);
      font-style: normal;
      font-size: 16px;
      color: var(--text-secondary);
      display: block;
      margin-top: 16px;
    }

    /* Closing slide */
    .closing-content {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 16px;
    }
    .closing-content .contact {
      font-family: var(--mono-font);
      font-size: 16px;
      color: var(--text-secondary);
    }

    /* Entrance animation */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to { opacity: 1; transform: translateY(0); }
    }
    [data-animate] { opacity: 0; }
    .reveal section.present [data-animate] {
      animation: fadeUp 0.5s ease-out both;
    }
    .reveal section.present [data-animate]:nth-child(2) { animation-delay: 0.1s; }
    .reveal section.present [data-animate]:nth-child(3) { animation-delay: 0.2s; }
    .reveal section.present [data-animate]:nth-child(4) { animation-delay: 0.3s; }
  </style>
</head>
<body>
  <div class="reveal">
    <div class="slides">

      <!-- SLIDE 1: Title -->
      <section>
        <div class="section-label" data-animate>Quarterly Report</div>
        <h1 data-animate>Q4 Revenue<br>Analysis</h1>
        <hr class="accent-rule" data-animate>
        <p class="text-secondary" data-animate>Finance Team — January 2025</p>
      </section>

      <!-- SLIDE 2: Key Metrics -->
      <section>
        <div class="section-label" data-animate>01 &mdash; Overview</div>
        <h2 data-animate>Key Metrics</h2>
        <hr class="accent-rule" data-animate>
        <div class="metrics-row" data-animate>
          <div class="metric-card">
            <span class="metric-label">Revenue</span>
            <span class="metric-value">$2.4M</span>
            <span class="metric-delta positive">+12.3%</span>
          </div>
          <div class="metric-card">
            <span class="metric-label">Customers</span>
            <span class="metric-value">1,847</span>
            <span class="metric-delta positive">+8.1%</span>
          </div>
          <div class="metric-card">
            <span class="metric-label">Churn</span>
            <span class="metric-value">3.2%</span>
            <span class="metric-delta negative">+0.4%</span>
          </div>
        </div>
      </section>

      <!-- SLIDE 3: Two-Column Content -->
      <section>
        <div class="split">
          <div>
            <div class="section-label" data-animate>02 &mdash; Growth</div>
            <h2 data-animate>Revenue Drivers</h2>
            <hr class="accent-rule" data-animate>
            <ul class="styled-list" data-animate>
              <li>Enterprise segment grew 23% QoQ</li>
              <li>APAC expansion contributed $340K net new</li>
              <li>Product-led growth reduced CAC by 18%</li>
              <li>Annual contracts now 62% of bookings</li>
            </ul>
          </div>
          <div>
            <div class="chart-container">
              <canvas id="revenueChart" width="700" height="400"></canvas>
            </div>
          </div>
        </div>
      </section>

      <!-- SLIDE 4: Quote -->
      <section>
        <blockquote data-animate>
          The shift to annual contracts fundamentally changed our unit economics.
          We're now operating with 14 months of runway visibility.
        </blockquote>
        <cite data-animate>&mdash; Sarah Chen, CFO</cite>
      </section>

      <!-- SLIDE 5: Closing -->
      <section>
        <div class="closing-content">
          <h1 data-animate>Thank You</h1>
          <hr class="accent-rule" data-animate>
          <p class="contact" data-animate>finance@company.com</p>
        </div>
      </section>

    </div>
  </div>

  <!-- 5. Reveal.js JS -->
  <script src="https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.js"></script>

  <!-- 6. Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4/dist/chart.umd.min.js"></script>

  <script>
    // Reveal.js init
    Reveal.initialize({
      hash: true,
      transition: 'fade',
      transitionSpeed: 'default',
      backgroundTransition: 'fade',
      center: true,
      width: 1920,
      height: 1080,
      margin: 0.04,
      controls: true,
      progress: true,
      slideNumber: 'c/t',
    });

    // Chart.js — theme defaults
    const root = getComputedStyle(document.documentElement);
    Chart.defaults.font.family = root.getPropertyValue('--body-font').trim();
    Chart.defaults.font.size = 14;
    Chart.defaults.color = root.getPropertyValue('--text-secondary').trim();

    // Render charts on slide entry
    const chartInstances = {};

    Reveal.on('slidechanged', event => {
      const canvas = event.currentSlide.querySelector('canvas');
      if (canvas && !chartInstances[canvas.id]) {
        chartInstances[canvas.id] = createRevenueChart(canvas);
      }
    });

    // Also check initial slide
    Reveal.on('ready', event => {
      const canvas = event.currentSlide.querySelector('canvas');
      if (canvas && !chartInstances[canvas.id]) {
        chartInstances[canvas.id] = createRevenueChart(canvas);
      }
    });

    function createRevenueChart(canvas) {
      return new Chart(canvas, {
        type: 'bar',
        data: {
          labels: ['Q1', 'Q2', 'Q3', 'Q4'],
          datasets: [{
            data: [1.8, 2.0, 2.1, 2.4],
            backgroundColor: '#C41E3A',
            borderRadius: 0,
            barPercentage: 0.65,
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: {
            legend: { display: false },
            tooltip: {
              callbacks: {
                label: ctx => `$${ctx.parsed.y}M`
              }
            }
          },
          scales: {
            x: {
              grid: { display: false },
              border: { color: '#E0E0E0' },
              ticks: { font: { family: "'JetBrains Mono', monospace", size: 12 } },
            },
            y: {
              grid: { color: '#E0E0E0' },
              border: { display: false },
              ticks: {
                font: { family: "'JetBrains Mono', monospace", size: 11 },
                callback: v => `$${v}M`,
              },
              beginAtZero: true,
            }
          }
        }
      });
    }
  </script>
</body>
</html>
```

## What this example demonstrates

- **Correct CDN load order:** Fonts → Reveal CSS → Custom `<style>` → Reveal JS → Chart.js → init script
- **CSS custom properties from style file**, mapped through the glossary
- **Selectors scoped under `.reveal`** to override Reveal.js defaults
- **Chart.js rendered on `slidechanged`**, not on page load, with explicit canvas dimensions
- **Entrance animations via CSS** (no GSAP needed for simple fades)
- **Varied slide layouts:** title, metrics, two-column with chart, quote, closing
- **Typography hierarchy:** display (72px) > heading (48px) > body (22px) > label (13px) > mono (11px)
- **Style-consistent elements:** accent rules, section labels, em-dash list markers, mono metric labels
- **Minimal dependencies:** only Reveal.js + Chart.js — no GSAP, no Three.js, no extras
