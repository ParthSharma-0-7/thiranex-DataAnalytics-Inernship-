# Global Trade Ledger — Sales Dashboard

A single-file, interactive React dashboard built from `1000_Sales_Records.csv` — 1,000 international sales orders spanning 2010–2017, 7 regions, and 12 commodity types.

## Files

| File | Description |
|---|---|
| `global_trade_dashboard.jsx` | The dashboard — a self-contained React component with the full dataset embedded (no backend, no API calls). |
| `README.md` | This file. |

## What's inside

**KPI strip**
- Total Revenue
- Total Profit (with margin %)
- Units Sold
- Shipment Count (with average revenue per order)

All four recalculate live based on whatever filters are active.

**Filters / slicers**
- Region (multi-select chips)
- Commodity / Item Type (multi-select chips)
- Sales Channel — Online / Offline / All
- Order Priority — Critical / High / Medium / Low
- Year range (two dropdowns, min–max)
- "Clear all" link appears once any filter is active

**Charts**
- Revenue & Profit by Year — combined area + line chart
- Revenue by Commodity — horizontal bar, toggle between sorting by revenue or profit
- Revenue by Region — horizontal bar
- Channel Split — donut chart (Online vs Offline revenue)
- Revenue by Order Priority — column chart

**Table**
- Top 10 shipments by revenue, with real Order IDs, region, commodity, channel, units, revenue, and profit

Every chart, KPI, and table row responds to the same filter state — e.g. selecting "Asia" + "Cosmetics" + years 2014–2016 updates everything at once.

## How to use it

**In Claude.ai**
The dashboard was shared as an Artifact in the conversation — it's already interactive there. Just click filters and watch the charts update.

**In your own React project**
1. Copy `global_trade_dashboard.jsx` into your project (e.g. `src/Dashboard.jsx`).
2. Install dependencies if you don't already have them:
   ```bash
   npm install react react-dom recharts
   ```
3. Import and render it:
   ```jsx
   import Dashboard from "./Dashboard";
   export default function App() {
     return <Dashboard />;
   }
   ```
4. The Google Fonts import (Fraunces, IBM Plex Mono, Inter) is pulled in via a `<style>` tag inside the component — no extra setup needed as long as the environment can reach `fonts.googleapis.com`.

## Data notes

- Source: `1000_Sales_Records.csv` (uploaded), columns mapped as: Region, Country, Item Type, Sales Channel, Order Priority, Order Date, Order ID, Ship Date, Units Sold, Unit Price, Unit Cost, Total Revenue, Total Cost, Total Profit.
- The dataset is embedded directly in the JSX file as a JS array (~1,000 rows), so the dashboard has no external data dependency and works offline.
- To swap in your own data: replace the `RAW` array near the top of the file with your own array of objects using the same field names (`region`, `country`, `item`, `channel`, `priority`, `orderDate`, `orderId`, `shipDate`, `units`, `unitPrice`, `unitCost`, `revenue`, `cost`, `profit`).

## Design

Styled as a "trade manifest / ledger" — deep navy background with a faint grid (like a nautical chart), amber and teal accents, serif display type (Fraunces) for headers and numbers, monospace (IBM Plex Mono) for data labels and figures.
