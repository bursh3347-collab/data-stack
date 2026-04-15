[English](README.md) | [中文](README_CN.md)

# 📊 data-stack

![Stars](https://img.shields.io/github/stars/bursh3347-collab/data-stack?style=flat-square)
![License](https://img.shields.io/github/license/bursh3347-collab/data-stack?style=flat-square)
![Last Commit](https://img.shields.io/github/last-commit/bursh3347-collab/data-stack?style=flat-square)

> ⭐ 成熟度: **L1 成长期** — 8个项目已分析，含TEMC实际评分、横向对比表和最佳实践提炼。

从全球顶尖 **8个数据分析与可视化开源项目** 中拆解精华、提炼最佳实践、深度分析。每个项目使用 [TEMC评分体系](#temc评分) 量化评估。

## 📈 排行榜（按TEMC评分）

| 排名 | 项目 | Stars | TEMC | License | 趋势 |
|------|------|-------|------|---------|------|
| 1 | [DuckDB](projects/duckdb.md) | 37.5k | **86** 🔴 | MIT ✅ | 🚀 |
| 2 | [Polars](projects/polars.md) | 38.2k | **83** | MIT ✅ | 🚀 |
| 3 | [Superset](projects/apache-superset.md) | 72.4k | **77** | Apache ✅ | ↑ |
| 4 | [Grafana](projects/grafana.md) | 73.2k | **73** | AGPL ⚠️ | → |
| 5 | [Pandas](projects/pandas.md) | 48.5k | **73** | BSD ✅ | → |
| 6 | [D3.js](projects/d3js.md) | 112.7k | **71** | ISC ✅ | → |
| 7 | [Plotly.js](projects/plotly.md) | 18.2k | **69** | MIT ✅ | → |
| 8 | [Metabase](projects/metabase.md) | 46.9k | **68** | AGPL ⚠️ | → |

> TEMC = **T**技术×0.25 + **E**生态×0.20 + **M**时机×0.30 + **C**组合×0.25

## 📋 仓库内容

### 对比与最佳实践

- [📊 全面横向对比表](comparison.md) — 8个项目并排对比
- [🔄 数据管道模式](best-practices/data-pipeline.md) — 惰性求值、SQL-over-files、向量化执行
- [📈 可视化模式](best-practices/visualization-patterns.md) — 插件架构、声明式配置、图形语法

## 🔥 Micro SaaS开发者快速选型

| 需求 | 首选 | 理由 |
|------|------|------|
| API内嵌分析 | **DuckDB** (86) | 文件上跑SQL，零基础设施，MIT |
| 高性能数据处理 | **Polars** (83) | 100倍Pandas性能，MIT，Rust引擎 |
| Next.js加图表 | **Plotly.js** (69) | `npm install react-plotly.js`，MIT |
| 学习仪表盘模式 | **Grafana** (73) | 最佳插件架构（仅学习，AGPL） |
| 学习嵌入式分析 | **Superset** (77) | 嵌入SDK模式（Apache） |
| Python数据脚本 | **Pandas** (73) | 事实标准，BSD |

## 🏗️ 提炼的最佳实践

### 数据处理（DuckDB + Polars + Pandas）
- **惰性求值** — 构建计算图→优化→执行（10-100倍提速）
- **SQL-Over-Files** — 直接查询Parquet/CSV，无需ETL
- **向量化执行** — 每批处理1024+值，利用CPU缓存效率
- **Apache Arrow** — 系统间零拷贝数据共享

### 可视化（D3 + Plotly + Grafana + Superset）
- **图表插件架构** — 每种图表类型是独立可注册模块
- **声明式配置** — JSON可序列化的图表配置，便于存储/共享
- **图形语法** — 将可视化分解为标度+形状+轴+交互
- **仪表盘网格布局** — 12列网格+拖拽面板

## ⚠️ License指南

| SaaS安全 ✅ | 仅供学习 ⚠️ |
|---|---|
| DuckDB (MIT) | Grafana (AGPL) |
| Polars (MIT) | Metabase (AGPL) |
| Plotly.js (MIT) | |
| Superset (Apache) | |
| Pandas (BSD) | |
| D3.js (ISC) | |

## 🏗️ 仓库结构

```
data-stack/
├── README.md              ← 英文版
├── README_CN.md           ← 你在这里
├── projects/              ← 单项目分析（TEMC评分）
├── best-practices/        ← 跨项目提炼的模式
├── code/                  ← 精华代码提取（L2阶段）
├── comparison.md          ← 横向对比表
└── SOURCES.md             ← 所有来源项目+链接+License
```

## <a id="temc评分"></a>📊 TEMC评分体系

**综合评分** = T×0.25 + E×0.20 + M×0.30 + C×0.25

- **T（技术分）**: 代码质量、架构设计、技术栈匹配度、文档质量
- **E（生态分）**: Stars/Forks、社区活跃度、生态集成度、维护者信誉
- **M（时机分）**: 市场时机、竞品稀缺度、趋势匹配度、可商用性
- **C（组合分）**: 技术栈兼容性、模块可拆解性、商业组合价值、学习成本

## ⚔️ 天子点评

**DuckDB是这里最被低估的工具。** 零基础设施，MIT许可，你可以直接在API路由中对Parquet文件跑SQL。对有分析功能的独立SaaS来说，DuckDB + Plotly.js是最高ROI组合——完全跳过Grafana/Superset的复杂性。

**Polars是数据处理的未来。** 如果你在做Python数据工作，现在就从Pandas切换到Polars。仅惰性求值就能给你10-100倍提速，零代码复杂度增加。

---

*由 [天工系统·代码猎手](https://github.com/bursh3347-collab) 自动化产出 | TEMC评分体系 | 更新于 2026-04-15*
