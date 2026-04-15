# Data Visualization Design Patterns

> Patterns extracted from D3.js, Grafana, Superset, and modern visualization practices.

## Pattern 1: Choose the Right Chart Type

```
Comparison       → Bar chart, Grouped bar
Trend over time  → Line chart, Area chart
Part-of-whole    → Pie/Donut (≤5 slices), Treemap (many categories)
Distribution     → Histogram, Box plot, Violin
Correlation      → Scatter plot, Bubble chart
Geographic       → Choropleth map, Point map
Hierarchy        → Treemap, Sunburst
Network          → Force-directed graph, Sankey diagram
Flow             → Sankey, Alluvial
```

## Pattern 2: Dashboard Layout Architecture (from Grafana)

```
┌─────────────────────────────────────────┐
│  KPI Row (4 number cards)               │
├────────────────────┬────────────────────┤
│  Primary Chart     │  Secondary Chart   │
│  (line/area)       │  (bar/pie)         │
├────────────────────┴────────────────────┤
│  Detail Table (sortable, filterable)    │
└─────────────────────────────────────────┘
```

**Principles**:
- KPIs at top (most important numbers visible immediately)
- Big charts in the middle (trends and comparisons)
- Detail tables at bottom (drill-down)
- Global filters at top or sidebar (affect all panels)

## Pattern 3: Responsive Chart Rendering

```typescript
function useChartResize(containerRef: RefObject<HTMLDivElement>) {
  const [dimensions, setDimensions] = useState({ width: 0, height: 0 });
  
  useEffect(() => {
    const observer = new ResizeObserver(entries => {
      const { width, height } = entries[0].contentRect;
      setDimensions({ width, height });
    });
    if (containerRef.current) observer.observe(containerRef.current);
    return () => observer.disconnect();
  }, []);
  
  return dimensions;
}
```

## Pattern 4: Data-Driven Color Scales (from D3)

```typescript
// Sequential (low → high)
const heatScale = d3.scaleSequential(d3.interpolateViridis).domain([0, 100]);

// Diverging (negative ← zero → positive)
const changeScale = d3.scaleDiverging(d3.interpolateRdYlGn).domain([-50, 0, 50]);

// Categorical (distinct groups)
const categoryScale = d3.scaleOrdinal(d3.schemeTableau10);
```

## Pattern 5: Embeddable Charts (from Metabase)

For SaaS products that need analytics:

```typescript
// 1. Generate signed JWT for embedding
const token = jwt.sign(
  { resource: { dashboard: dashboardId }, params: { client_id: clientId } },
  EMBEDDING_SECRET,
  { expiresIn: '1h' }
);

// 2. Render iframe
<iframe
  src={`/embed/dashboard/${token}`}
  width="100%"
  height="600px"
  frameBorder="0"
/>
```

## Anti-Patterns

1. **3D charts** — Almost always misleading, use 2D
2. **Too many colors** — Max 7-8 distinct colors, group the rest as "Other"
3. **Pie charts with many slices** — Use bar chart if > 5 categories
4. **Dual Y-axes** — Misleading correlations, use separate charts
5. **No axis labels** — Always label axes and include units
6. **Rainbow color scales** — Use perceptually uniform scales (Viridis)
