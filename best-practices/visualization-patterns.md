# Visualization Patterns & Best Practices

> Extracted from D3.js, Plotly.js, Grafana, and Superset — the world's top visualization tools.

## 1. Plugin Architecture for Charts (from Grafana & Superset)

Both Grafana and Superset use a plugin system where each chart type is an independent module.

**Pattern**:
```typescript
// Chart Plugin Interface
interface ChartPlugin {
  // Metadata
  id: string;
  name: string;
  thumbnail: string;
  
  // Schema
  controlPanel: ControlPanelConfig;  // What settings the user can configure
  transformProps: (data: QueryData) => ChartProps;  // Data transformation
  
  // Rendering
  Chart: React.ComponentType<ChartProps>;  // The actual chart component
}

// Register plugins
const chartRegistry = new Map<string, ChartPlugin>();
chartRegistry.set('bar', BarChartPlugin);
chartRegistry.set('line', LineChartPlugin);
chartRegistry.set('pie', PieChartPlugin);

// Usage
const plugin = chartRegistry.get(chartType);
const props = plugin.transformProps(rawData);
return <plugin.Chart {...props} />;
```

**Why it matters**: Decouples chart rendering from the dashboard framework. New chart types can be added without modifying core code.

**Applicable to**: Any SaaS with dashboards or reporting features.

## 2. Declarative Chart Configuration (from Plotly.js)

Describe WHAT you want, not HOW to draw it.

```javascript
// Plotly's declarative approach
const data = [{
  type: 'bar',
  x: ['Q1', 'Q2', 'Q3', 'Q4'],
  y: [100, 200, 150, 300],
  marker: { color: '#6366f1' }
}];

const layout = {
  title: 'Revenue by Quarter',
  xaxis: { title: 'Quarter' },
  yaxis: { title: 'Revenue ($K)' }
};

Plotly.newPlot('chart', data, layout);
```

**Design principle**: Chart configs are JSON-serializable → can be stored in DB, shared via API, versioned.

**Applicable to**: Any product where users create/save/share charts.

## 3. Grammar of Graphics (inspired by D3.js)

D3's approach decomposes visualization into primitives:

```
Data → Scales → Shapes → Axes → Interactions
```

| Primitive | D3 Module | Purpose |
|-----------|-----------|--------|
| Scales | d3-scale | Map data values → visual values |
| Shapes | d3-shape | Generate SVG paths (line, area, arc) |
| Axes | d3-axis | Render axis ticks and labels |
| Layouts | d3-hierarchy | Compute positions (treemap, pack) |
| Forces | d3-force | Physics simulation for graph layouts |

**Key Insight**: Scales are the most reusable pattern. A scale that maps `[0, 1000]` → `[0, 500px]` is needed everywhere.

```javascript
// Scale pattern — universally applicable
const xScale = d3.scaleLinear()
  .domain([0, maxValue])    // data space
  .range([0, chartWidth]);  // pixel space

// Time scale
const timeScale = d3.scaleTime()
  .domain([startDate, endDate])
  .range([0, chartWidth]);

// Color scale
const colorScale = d3.scaleOrdinal(d3.schemeCategory10);
```

## 4. Dashboard Layout System (from Grafana)

Grafana uses a grid-based layout with drag-and-drop panels.

**Pattern**:
```typescript
interface Panel {
  id: string;
  type: string;  // chart plugin id
  gridPos: { x: number; y: number; w: number; h: number };
  datasource: DataSourceRef;
  targets: Query[];  // queries to execute
  options: PanelOptions;  // chart-specific config
}

interface Dashboard {
  panels: Panel[];
  time: { from: string; to: string };  // global time range
  variables: Variable[];  // template variables
  refresh: string;  // auto-refresh interval
}
```

**Key Design Decisions**:
- Grid positions are absolute (12-column grid)
- Each panel independently fetches its data
- Global time range propagates to all panels
- Variables enable dynamic filtering across all panels

## 5. Responsive Chart Sizing

All major libraries handle responsive sizing differently:

| Library | Approach |
|---------|----------|
| D3.js | Manual: listen to resize events, re-render |
| Plotly.js | `Plotly.Plots.resize()` or `responsive: true` config |
| Grafana | Panel container handles sizing, chart fills container |

**Best practice**: Use a ResizeObserver wrapper:

```typescript
function useChartSize(ref: RefObject<HTMLDivElement>) {
  const [size, setSize] = useState({ width: 0, height: 0 });
  
  useEffect(() => {
    const observer = new ResizeObserver(entries => {
      const { width, height } = entries[0].contentRect;
      setSize({ width, height });
    });
    if (ref.current) observer.observe(ref.current);
    return () => observer.disconnect();
  }, [ref]);
  
  return size;
}
```

## 6. Data-to-Visual Mapping Checklist

Before building any chart, answer these questions:

1. **What data type?** → Determines chart type
   - Categorical → Bar, Pie
   - Time series → Line, Area
   - Correlation → Scatter
   - Distribution → Histogram, Box
   - Hierarchy → Treemap, Sunburst
   - Network → Force graph, Sankey

2. **How much data?** → Determines rendering approach
   - <1K points → SVG (D3, Recharts)
   - 1K-100K → Canvas or WebGL (Plotly scattergl)
   - >100K → Aggregation first, then render

3. **Interactive?** → Determines library choice
   - Static report → Any library
   - Hover/click → Plotly, D3, ECharts
   - Brush/zoom → D3, Plotly, Grafana
   - Real-time → Grafana, custom D3
