---
name: excel-procurement-dashboard
description: Use this skill when the user's request involves excel procurement dashboard. Trigger phrases include: "dashboard", "html dashboard", "interactive dashboard", "interaktivní dashboard", "vizualizace dat", "spend dashboard", "savings tracker dashboard", "rfq dashboard", "supplier scorecard dashboard", "contract coverage dashboard", "procurement kpi", "management dashboard". Produces a self-contained HTML dashboard with drag-and-drop Excel/CSV upload and client-side visualizations.
---

# Skill: Excel Procurement Dashboard

## Purpose
This skill helps the procurement agent generate an interactive HTML dashboard from Excel-based procurement data.
The dashboard runs fully in the browser, allows the user to upload an Excel or CSV file and visualizes the data without sending it anywhere.
The goal is to provide a reusable, self-contained dashboard for spend data, RFQ comparison, supplier scorecards, savings trackers, price lists, contract coverage and other procurement use cases.

## When to use
Use this skill when the user asks for:
- HTML dashboard,
- interactive dashboard,
- spend dashboard,
- savings tracker,
- RFQ comparison dashboard,
- supplier scorecard dashboard,
- procurement KPI report,
- vendor analysis dashboard,
- category spend visualization,
- contract coverage dashboard,
- management dashboard from Excel,
- a tool to upload Excel and see charts.

Do not use this skill if the user only wants a written analysis or a static report — for that use the **Excel Procurement Analysis** skill.

## Required inputs
If available, collect:
- purpose of the dashboard (spend, savings, RFQ, scorecard, contracts, KPI),
- expected data structure (columns, units, currency),
- reporting period,
- category or business unit,
- baseline definition (if savings tracker),
- required KPIs,
- required dimensions for break-down (supplier, category, item, region, month),
- required metric (spend, quantity, savings, OTIF, complaints),
- branding requirements (logo, color, company name),
- language of the UI (Czech by default).

## Process
1. Clarify the use case and the Excel structure before generating the dashboard.
2. Decide whether to use the generic template or to tailor it for a specific data shape.
3. Start from `dashboard_template.html` as the base.
4. Adjust column mapping, KPI definitions, presets and labels to match the use case.
5. Keep all processing client-side (SheetJS, Chart.js, Grid.js loaded from CDN).
6. Ensure the dashboard works with an empty state and shows a friendly message when no file is loaded.
7. Validate column auto-detection (number, text, date) with the user's expected data.
8. Provide procurement-ready presets relevant to the use case.
9. Save the final HTML as a single file the user can open locally.
10. Brief the user on how to use the dashboard and what data shape it expects.

## Output format
Deliver one self-contained `.html` file.
UI in Czech by default.
The file must:
- open in any modern browser without a server,
- not send data anywhere,
- load SheetJS, Chart.js and Grid.js from CDN,
- contain drag&drop and a file picker for `.xlsx`, `.xls` and `.csv`,
- show a sheet selector when the workbook has multiple sheets,
- auto-detect column types,
- render KPI cards, at least one chart and a sortable / filterable data table,
- be readable on a laptop screen (min 1280 px width) and degrade gracefully on smaller screens.

After delivering the file, return a short summary in this structure:
1. Shrnutí dashboardu
2. Očekávaná struktura Excelu
3. Jak dashboard použít
4. Co dashboard zobrazuje
5. Omezení a předpoklady
6. Další kroky / možnosti rozšíření

## Dashboard building blocks
Always include:

| Block | What it shows |
|---|---|
| Upload area | Drag&drop + file picker for `.xlsx` / `.xls` / `.csv` |
| Sheet picker | Drop-down when the workbook has multiple sheets |
| Column inspector | Detected columns with type (number, text, date) and sample values |
| KPI cards | 3–6 top-line metrics (sum, count, avg, min, max) on chosen numeric columns |
| Dimension picker | Drop-down to choose break-down (supplier, category, item, month) |
| Metric picker | Drop-down to choose metric (spend, quantity, savings, count) |
| Bar chart | Top N values for the chosen dimension and metric |
| Pie / donut chart | Share of total for the chosen dimension |
| Trend chart | Time-series when a date column is detected |
| Data table | Sortable, filterable table with all rows (Grid.js) |
| Filters | At least one text filter and one date range filter |
| Empty state | Friendly message and short usage hint when no file is loaded |

## Common dashboard use cases

### Spend dashboard
Show:
- total spend,
- supplier count,
- item count,
- spend by supplier (top N),
- spend by category,
- spend by month,
- tail spend share,
- top items.

### RFQ comparison dashboard
Show:
- supplier prices per item,
- price index vs. lowest bidder,
- total TCO per supplier,
- coverage of scope (items quoted vs. total),
- commercial deviations (Incoterms, payment terms, lead time),
- missing data flags.

### Savings tracker
Show:
- realized savings YTD,
- pipeline savings,
- savings by category,
- savings by initiative,
- baseline vs. actual,
- realization rate.

### Supplier scorecard dashboard
Show:
- OTIF per supplier,
- complaints count and value,
- average lead time,
- claim value,
- compliance status,
- overall scorecard ranking.

### Contract coverage dashboard
Show:
- spend under contract vs. off-contract,
- contracts expiring in the next 90 / 180 / 365 days,
- spend by contract owner,
- compliance per category.

### Management KPI dashboard
Show:
- spend YTD,
- realized savings YTD,
- working capital impact (DPO),
- supplier consolidation,
- contract coverage,
- top risks.

## Procurement checks before generating
Before generating the dashboard, confirm:

| Area | What to confirm |
|---|---|
| Data scope | Period, category, site, supplier, business unit |
| Headers | Column names match the expected mapping |
| Currency | Single currency or FX assumption |
| Unit of measure | Consistent units for compared items |
| Baseline | Defined baseline if the dashboard shows savings |
| Mixed sheets | Whether multiple sheets need to be combined |
| Sensitive data | Whether the file contains personal or commercially sensitive data |

## Rules
- Do not embed the user's data in the HTML — the dashboard must accept upload at runtime.
- Do not send data to any server; all processing must stay in the browser.
- Do not display savings without a defined baseline.
- Do not compare prices without checking unit, currency, Incoterms and technical scope.
- Do not assume column names — let the user map them or auto-detect.
- Do not use heavy frameworks; keep the file self-contained with CDN dependencies only.
- Do not modify source data; the dashboard reads the file in memory.
- Do not auto-download or auto-submit anything.
- Always handle empty / malformed files with a clear error message.
- Default UI language is Czech; switch to English only when explicitly requested.
