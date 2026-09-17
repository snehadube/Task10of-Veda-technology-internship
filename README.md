# Simple KPI Tracking Sheet — Sample Superstore

## Objective
Practice translating raw transactional order data into a small set of business-ready
KPIs — a one-page summary that updates automatically as new orders are added, with
no manual recalculation needed.

## Tool used
**Microsoft Excel** (`.xlsx`) — works the same way if opened/edited in Google Sheets.

## What's inside (`KPI_Tracking_Sheet.xlsx`)
| Sheet | Purpose |
|---|---|
| **KPI Summary** | The one-page deliverable: 4 KPI cards + a short "how this works" note |
| **Product Summary** | Helper sheet — one row per product (1,850 rows) with live `SUMIF` totals, used to look up the Top Product |
| **Orders** | Raw order data (9,994 rows, 21 columns) — the single source of truth |

## KPIs (4, per the "no more than 4-5" guidance)
1. **Revenue** — `SUM` of all Sales
2. **Units Sold** — `SUM` of all Quantity
3. **Average Order Value** — Revenue ÷ number of *unique* orders (5,009 orders), not per line item
4. **Top Product (by Revenue)** — looked up live via `INDEX/MATCH` against the Product Summary sheet

Current values: **Revenue $2,297,201** · **Units Sold 37,873** · **AOV $458.61** ·
**Top Product: Canon imageCLASS 2200 Advanced Copier**

## Auto-recalculation (the core requirement)
All formulas use `SUMIF`/`SUMIFS`/`COUNTIF` over a buffered range (`Orders!2:10500`) —
9,994 rows wider than the current data — so pasting new order rows anywhere in that
range updates every KPI instantly. No formulas need to be edited or dragged down.

## Dataset
Sample Superstore Dataset (cleaned version, duplicates removed on `order_id`).
See `Samplesuperstore_analysis.sql` for the MySQL cleaning/EDA queries behind it.

## How to open
1. Download `KPI_Tracking_Sheet.xlsx`
2. Open in Excel or Google Sheets (upload as .xlsx, or File → Import)
3. KPI Summary tab is the main view — no setup needed, formulas are already live

## Repo contents
- `KPI_Tracking_Sheet.xlsx` — the KPI tracking deliverable
- `KPI_Summary_Screenshot.png` — screenshot of the KPI Summary tab (for quick preview / LinkedIn)
- `Sample_Superstore_Cleaned_UTF8.csv` — source data
- `Samplesuperstore_analysis.sql` — SQL cleaning/analysis behind the dataset
- `Project_Report.docx` — one-page write-up of approach and outcome
