# Data Visualization Reference

Charts, tables, metrics, and data displays for slides. All visualizations must be themed to match the chosen style's palette and typography.

## Library Choice

| Need | Use | Why |
|---|---|---|
| Bar, line, pie, doughnut, scatter | **Chart.js** | Clean defaults, easy to theme, lightweight |
| Custom editorial viz, treemaps, complex layouts | **D3.js** | Full pixel control, NYT/Bloomberg quality |
| Simple metrics / KPIs | **HTML + CSS** | No library needed, just styled numbers |
| Tables | **HTML + CSS** | Style to match the deck, no library needed |

**Default to Chart.js** unless the visualization needs something custom. Use D3 when you need editorial-quality output that Chart.js can't handle.

## Chart.js

CDN tag is in `libraries.md`.

### Theming to Match Slide Style

Set global defaults before creating any chart. Pull values from your CSS custom properties:

```js
// Get computed style values from the document
const root = getComputedStyle(document.documentElement);

Chart.defaults.font.family = root.getPropertyValue('--body-font').trim();
Chart.defaults.font.size = 14;
Chart.defaults.font.weight = '400';
Chart.defaults.color = root.getPropertyValue('--text-secondary').trim();
Chart.defaults.borderColor = root.getPropertyValue('--border-color').trim();
Chart.defaults.backgroundColor = 'transparent';

// Disable default legend box styling
Chart.defaults.plugins.legend.labels.usePointStyle = true;
Chart.defaults.plugins.legend.labels.pointStyle = 'circle';

// Cleaner grid lines
Chart.defaults.scales.linear = Chart.defaults.scales.linear || {};
```

### Style-Specific Chart Palettes

When creating datasets, use colors from the style's palette:

```js
// Example: Editorial Financial style
const chartColors = {
  primary: '#384F84',    // navy
  secondary: '#C8B496',  // gold
  tertiary: '#7A8BA8',   // muted navy
  positive: '#4A7C59',   // green
  negative: '#C45A3B',   // terracotta
  grid: '#E5E0D8',       // warm parchment border
};
```

### Clean Bar Chart

```js
new Chart(canvas, {
  type: 'bar',
  data: {
    labels: ['Q1', 'Q2', 'Q3', 'Q4'],
    datasets: [{
      data: [42, 58, 35, 71],
      backgroundColor: chartColors.primary,
      borderRadius: 0,  // match style (0 for brutalist/swiss, 4 for warm/editorial)
      barPercentage: 0.7,
      categoryPercentage: 0.8,
    }]
  },
  options: {
    responsive: true,
    maintainAspectRatio: false,
    plugins: {
      legend: { display: false },
      tooltip: {
        backgroundColor: '#1A1A1A',
        titleFont: { family: root.getPropertyValue('--display-font').trim(), weight: '600' },
        bodyFont: { family: root.getPropertyValue('--body-font').trim() },
        cornerRadius: 0,
        padding: 12,
      }
    },
    scales: {
      x: {
        grid: { display: false },
        ticks: {
          font: { family: root.getPropertyValue('--body-font').trim(), size: 12, weight: '500' },
        },
        border: { color: chartColors.grid },
      },
      y: {
        grid: { color: chartColors.grid, lineWidth: 1 },
        ticks: {
          font: { family: root.getPropertyValue('--mono-font').trim(), size: 11 },
        },
        border: { display: false },
      }
    }
  }
});
```

### Clean Line Chart

```js
new Chart(canvas, {
  type: 'line',
  data: {
    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
    datasets: [{
      data: [30, 45, 28, 60, 52, 75],
      borderColor: chartColors.primary,
      borderWidth: 2,
      pointRadius: 0,
      pointHoverRadius: 5,
      pointHoverBackgroundColor: chartColors.primary,
      tension: 0.3,
      fill: {
        target: 'origin',
        above: chartColors.primary + '10',  // 6% opacity fill
      },
    }]
  },
  options: {
    responsive: true,
    maintainAspectRatio: false,
    plugins: { legend: { display: false } },
    scales: {
      x: { grid: { display: false } },
      y: { grid: { color: chartColors.grid } },
    }
  }
});
```

### Doughnut / Pie

```js
new Chart(canvas, {
  type: 'doughnut',
  data: {
    labels: ['Product A', 'Product B', 'Product C'],
    datasets: [{
      data: [45, 30, 25],
      backgroundColor: [chartColors.primary, chartColors.secondary, chartColors.tertiary],
      borderWidth: 0,
      spacing: 2,
    }]
  },
  options: {
    responsive: true,
    cutout: '65%',
    plugins: {
      legend: {
        position: 'right',
        labels: { padding: 16, usePointStyle: true, pointStyle: 'circle' },
      }
    }
  }
});
```

### Rendering Charts on Slide Entry

Charts should render when their slide becomes visible, not on page load:

```js
const chartInstances = {};

Reveal.on('slidechanged', event => {
  const canvases = event.currentSlide.querySelectorAll('canvas[data-chart]');
  canvases.forEach(canvas => {
    const id = canvas.id;
    if (chartInstances[id]) return; // already rendered
    chartInstances[id] = new Chart(canvas, JSON.parse(canvas.dataset.chart));
  });
});
```

## D3.js

CDN tag is in `libraries.md`.

### When to use D3 over Chart.js

- Custom axis treatments (e.g., editorial-style axes with no gridlines, just ticks)
- Bespoke chart types (slope charts, bump charts, lollipop charts)
- Annotated visualizations with callouts and labels positioned precisely
- Animated data transitions synced to Reveal.js slide changes
- Treemaps, force-directed graphs, geographic maps

### Simple D3 Bar Chart (styled)

```js
function drawBarChart(container, data, colors) {
  const margin = { top: 20, right: 20, bottom: 40, left: 50 };
  const width = 600 - margin.left - margin.right;
  const height = 350 - margin.top - margin.bottom;

  const svg = d3.select(container)
    .append('svg')
    .attr('viewBox', `0 0 ${width + margin.left + margin.right} ${height + margin.top + margin.bottom}`)
    .append('g')
    .attr('transform', `translate(${margin.left},${margin.top})`);

  const x = d3.scaleBand().domain(data.map(d => d.label)).range([0, width]).padding(0.3);
  const y = d3.scaleLinear().domain([0, d3.max(data, d => d.value)]).nice().range([height, 0]);

  // Bars
  svg.selectAll('rect')
    .data(data)
    .join('rect')
    .attr('x', d => x(d.label))
    .attr('y', d => y(d.value))
    .attr('width', x.bandwidth())
    .attr('height', d => height - y(d.value))
    .attr('fill', colors.primary);

  // X axis
  svg.append('g')
    .attr('transform', `translate(0,${height})`)
    .call(d3.axisBottom(x).tickSize(0))
    .select('.domain').attr('stroke', colors.grid);

  // Y axis
  svg.append('g')
    .call(d3.axisLeft(y).ticks(5).tickSize(-width))
    .select('.domain').remove();

  svg.selectAll('.tick line').attr('stroke', colors.grid).attr('stroke-dasharray', '2,2');
}
```

## KPI / Metric Cards (HTML + CSS)

No library needed. Use styled HTML:

```html
<div class="metrics-row">
  <div class="metric-card">
    <span class="metric-label">Revenue</span>
    <span class="metric-value" data-animate-counter="2400000">$2.4M</span>
    <span class="metric-delta positive">+12.3%</span>
  </div>
  <div class="metric-card">
    <span class="metric-label">Users</span>
    <span class="metric-value" data-animate-counter="84000">84K</span>
    <span class="metric-delta positive">+8.1%</span>
  </div>
</div>
```

```css
.metrics-row {
  display: flex;
  gap: var(--gap);
}
.metric-card {
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.metric-label {
  font-family: var(--body-font);
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: var(--text-secondary);
}
.metric-value {
  font-family: var(--display-font);
  font-size: 48px;
  font-weight: 600;
  color: var(--text-primary);
  line-height: 1;
}
.metric-delta {
  font-family: var(--mono-font);
  font-size: 14px;
}
.metric-delta.positive { color: var(--color-positive); }
.metric-delta.negative { color: var(--color-negative); }
```

## Tables

Style tables to match the deck. Never use browser-default table styling.

```css
.styled-table {
  width: 100%;
  border-collapse: collapse;
  font-family: var(--body-font);
  font-size: 14px;
}
.styled-table thead {
  /* Dark-inverted header for bold styles, border-bottom for editorial styles */
  background: var(--text-primary);
  color: var(--bg-color);
}
.styled-table th {
  font-family: var(--body-font);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  font-size: 11px;
  padding: 12px 16px;
  text-align: left;
}
.styled-table td {
  padding: 10px 16px;
  border-bottom: 1px solid var(--border-color);
  color: var(--text-primary);
}
.styled-table tbody tr:hover {
  background: var(--surface-color, rgba(0,0,0,0.02));
}
/* Monospace for numbers */
.styled-table td.numeric {
  font-family: var(--mono-font);
  text-align: right;
}
```

## Style-to-Chart Mapping

| Style category | Chart approach | Notes |
|---|---|---|
| Editorial (Financial, Data, Calm) | Chart.js with minimal grid, serif labels | Newspaper-quality, restrained color |
| Swiss (Clean, Elegant, Expressive) | Chart.js with no grid, geometric precision | Flush-left labels, accent color for primary series |
| Brutalist (Nordic, Luxury) | Chart.js with bold borders, inverted headers | 2px borders on chart container, dark table headers |
| Minimalist | Chart.js with bare minimum — no grid, no borders | Let the data breathe |
| Dark / Luxury | Chart.js on dark background, light grid lines | Adjust text colors for dark bg |
| Expressive (Collage, Color Field) | D3 for custom treatments | More freedom for unconventional layouts |
| Futuristic (Neo-Futurism) | D3 or Chart.js with glow effects | Neon accent colors, dark bg |
