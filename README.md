# Support Dashboard

A fully static, single-file HTML dashboard for customer support operations. Built with vanilla HTML, CSS, and Chart.js — no frameworks, no build step, no dependencies beyond a CDN script tag.

Inspired by the visual language of Intercom and Efferd's Shadcn dashboard blocks, adapted into a light-theme design system modeled after Mixpanel.

---

## Stack

- **HTML/CSS** — layout, components, design tokens via CSS custom properties
- **Chart.js 4.4** — all charts loaded from CDN
- **No JavaScript frameworks** — zero build tooling required

---

## Design System

All visual decisions are driven by a small set of CSS tokens defined in `:root`:

| Token | Value | Role |
|---|---|---|
| `--bg` | `#f5f5f5` | Page background |
| `--card` | `#ffffff` | Card surface |
| `--border` | `#e5e5e5` | All borders |
| `--text` | `#1a1a1a` | Primary text |
| `--muted` | `#888888` | Labels, subtitles |
| `--accent` | `#7856ff` | Purple accent, charts |
| `--up` | `#16a34a` | Positive delta |
| `--down` | `#dc2626` | Negative delta |

---

## Layout

`.main` uses a single **12-column CSS grid** with a 16px gap. No row wrapper divs — every card carries its own span class directly.

| Class | Columns spanned |
|---|---|
| `.col-8` | 8 / 12 |
| `.col-6` | 6 / 12 |
| `.col-4` | 4 / 12 |
| `.col-3` | 3 / 12 |
| `.spark-card` | 3 / 12 (via rule) |

### Breakpoints

| Viewport | Grid | Notes |
|---|---|---|
| `> 1100px` | 12 columns | Full layout |
| `≤ 1100px` | 8 columns | Donut and bottom panels reflow |
| `≤ 768px` | 4 columns | Sidebar hidden, most cards go full width |
| `≤ 480px` | 1 column | Everything stacks |

---

## Dashboard Rows

### 1 — KPI Strip
Four joined metric cards in a single bordered row: **Open queue**, **Active conversations**, **Median first reply**, and **CSAT (30d)**. Each card shows a current value and a delta badge (green for improvement, red for regression) with a comparison label (vs yesterday / vs last week / vs prior 30d).

### 2 — Volume + Traffic
Two cards spanning 8 and 4 columns respectively.

- **Conversation volume** (col-8) — area chart showing new threads per day over the last 30 days. Includes a time range dropdown (decorative in this version). Gradient fill under the line using the purple accent.
- **Traffic by channel** (col-4) — donut chart breaking down conversation share across Direct, Email, and Social channels over the last 7 days. Custom legend below the chart.

### 3 — CSAT + First Reply
Two equal-width chart cards (col-6 each).

- **CSAT responses** — stacked bar chart showing post-resolution survey submissions per day, split by channel (Direct / Email / Social) over the last 10 days.
- **Median first reply** — line chart with visible data points showing median minutes to first agent response over the last 7 days.

### 4 — Sparkline KPIs
Four compact metric cards (col-3 each), each showing a headline number and a small sparkline trend chart below it. Metrics: **Resolved today**, **Avg handle time**, **Reopened tickets**, **Escalations**. Sparkline colors reflect direction — purple for neutral, green for good, red for concerning, amber for warning.

### 5 — Activity Feed + Tickets Table
Two equal-width cards (col-6 each).

- **Recent activity** — chronological feed of support events: assignments, resolutions, SLA breaches, and new conversations. Each item has a color-coded dot (purple = active, green = resolved, grey = system).
- **Open tickets** — tabular view of the current queue with columns for ID, customer, subject, status pill, and wait time. Status pills use three states: Open (amber), Pending (purple), Resolved (green).

---

## File Structure

```
/
├── index.html     # Entire dashboard — single self-contained file
└── README.md      # This file
```

---
