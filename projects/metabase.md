# Metabase

> The easy-to-use open-source BI tool that lets everyone work with data.

| Metric | Data |
|--------|------|
| GitHub | [metabase/metabase](https://github.com/metabase/metabase) |
| Stars | 46,863 |
| Forks | 6,376 |
| License | AGPL-3.0 ⚠️ (copyleft) |
| Language | Clojure (backend) + JavaScript/TypeScript (frontend) |
| Last Update | 2026-04-15 (today!) |
| Open Issues | 4,094 |
| Backed by | Metabase Inc. (commercial company) |

## TEMC Score

| Dimension | Score | Rationale |
|-----------|-------|-----------|
| T (Tech) | 75 | Clean UX design, visual query builder is excellent. Clojure backend is niche. React frontend. Embedding API well-designed. |
| E (Ecosystem) | 80 | 47k⭐, strong community, 20+ database drivers. Commercial company ensures longevity. |
| M (Market) | 72 | "BI for everyone" — low-code analytics growing fast. SMB market underserved. |
| C (Combo) | 45 | ⚠️ AGPL + Clojure backend = cannot reuse code. UX patterns are the main learning value. |
| **Composite** | **68** | 75×0.25 + 80×0.20 + 72×0.30 + 45×0.25 |

## ⚠️ License Warning

**AGPL-3.0** — same restriction as Grafana. Study UX patterns and product design only.

## Core Value

Metabase's **visual query builder** is the best open-source implementation of "let non-technical users explore data." The UX design patterns for making SQL accessible are world-class.

## Architecture Highlights

- **Visual Query Builder**: Drag-and-drop interface that generates SQL
- **Question → Dashboard flow**: Natural progression from ad-hoc query to saved dashboard
- **Embedding**: iframe + JWT token for white-label analytics
- **Driver System**: Pluggable database drivers for 20+ backends

## What to Learn (not copy)

| Pattern | Value |
|---------|-------|
| Visual query builder UX | 🔥 Study for any data product |
| Progressive disclosure in data tools | 🔥 UX pattern reference |
| Embedding via JWT tokens | Medium — common pattern |

## Commercial Value

- **Pain point**: SMBs need analytics without hiring data engineers → 重要级
- **Metabase pricing**: Free (open-source) → Pro $85/user/mo → Enterprise custom
- **For天子**: Study the "make data accessible" UX philosophy. The visual query builder pattern could inspire SaaS features.

## Why It Might NOT Be Worth It

- AGPL-3.0 = no code reuse
- Clojure backend = completely outside base stack
- 4,094 open issues = maintenance concerns
- Metabase Inc. controls the roadmap
- Better to study the UX and build from scratch in TypeScript
