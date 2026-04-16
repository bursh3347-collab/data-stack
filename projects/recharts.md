# Recharts

> The most popular React charting library — composable, declarative, beautiful

| Metric | Value |
|--------|-------|
| GitHub | [recharts/recharts](https://github.com/recharts/recharts) |
| Stars | ~25,000 |
| License | MIT ✅ |
| Language | TypeScript |
| Last Update | Active (daily commits) |
| Bundle Size | ~200KB (treeshakeable) |

## TEMC Scores

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 75 | TypeScript, D3 under the hood, declarative React API, Storybook docs. Solid but not cutting-edge |
| E (Eco) | 82 | 25k stars, 5M+ npm weekly downloads, very active. Standard React charting choice |
| M (Market) | 75 | Most popular React chart lib. Competition from Nivo, Victory, Tremor, but Recharts has mindshare |
| C (Combo) | 90 | React + TypeScript = **perfect** Next.js fit. `npm install recharts` and go. Smallest learning curve |
| **Composite** | **80** | T×0.25 + E×0.20 + M×0.30 + C×0.25 |

## Core Value

Recharts is the **path of least resistance** for charts in React/Next.js. Declarative JSX API: `<LineChart><Line dataKey="value" /></LineChart>`. TypeScript types included. D3 does the math, React does the rendering. No config objects, no imperative drawing.

## Architecture Highlights

- **Declarative JSX** — compose charts from React components
- **D3 under the hood** — scales, shapes, math from D3
- **SVG rendering** — clean, inspectable, CSS-stylable
- **Responsive** — `<ResponsiveContainer>` handles resizing
- **Animation** — built-in transitions via react-smooth
- **TypeScript** — full type definitions

## Chart Types

- Line / Area / Bar / Composed (mixed)
- Pie / Radar / Radial Bar
- Scatter / Funnel / Treemap
- Brush (zoom/pan) / Reference lines

## Solo Dev Verdict

**🔴 MUST-HAVE** — If you're building any SaaS with Next.js that shows data, Recharts is your first choice. `npm install recharts`, import components, pass data. 5 minutes to first chart. MIT license, tiny bundle (~200KB), perfect TypeScript support.

## Why It Might NOT Be Worth It

- Limited customization compared to D3.js or Plotly
- SVG can be slow with 10,000+ data points (use canvas-based libs instead)
- Animation can be janky with frequent updates
- Not as pretty out-of-box as Tremor (which wraps Recharts with Tailwind)

## Quick Start (Next.js)

```tsx
import { LineChart, Line, XAxis, YAxis, Tooltip } from 'recharts';

const data = [{name: 'Jan', value: 400}, {name: 'Feb', value: 300}];

export default function Chart() {
  return (
    <LineChart width={600} height={300} data={data}>
      <XAxis dataKey="name" />
      <YAxis />
      <Tooltip />
      <Line type="monotone" dataKey="value" stroke="#8884d8" />
    </LineChart>
  );
}
```
