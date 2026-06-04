# Retail CPG Analytics Portfolio

**Nelly — CPG / Retail Analytics | SQL · Power BI · DAX**

Seven page Power BI dashboard built on a synthetic Walmart Scintilla style database — covering sales drivers, inventory health, promo analytics, and a three page supply chain module with OTIF, fine exposure, and carrier level analysis.

---

## Database Schema

```
Dim_Date ────┐
Dim_Store ───┤                     ┌── Fact_WeeklySales   (26,000 rows)
Dim_Item ────┼──── Fact Tables ───┤── Fact_Inventory      (26,000 rows)
Dim_Category ┤                     ├── Fact_PromoCalendar  (520 rows)
Dim_Fineline ┤                     └── Fact_SupplyChain    (520 rows)
Dim_Supplier ┘
Dim_PromoMechanism
```

Star schema · 4 fact tables · 7 dimension tables · 77 DAX measures · 6 display folders

---
 
## [Dashboard-PDF](documentation/Retail_CPG_Analytics.pdf) — 7 Pages

| Page | Title | Primary KPIs |
|---|---|---|
| 1 | Sales Overview | $32.23M Sales TY · 6.8% YoY · 28.5% GM Rate · Category scorecard |
| 2 | Weekly Performance | 52-week TY vs LY · Item detail · 26.8% Promo Mix · ASP by item |
| 3 | Inventory Health | 88.9% In-Stock Rate · $4.14M Lost Sales · 1.4 Avg WOS · 87.3% Fill Rate |
| 4 | Promo Analytics | 19.9% Avg Lift · $496K Trade Spend · 2.56 Avg ROI · 150K Incremental Units |
| 5 | Supply Chain — OTIF & Supplier Scorecard | 54.2% OTIF · $304K Fine Exposure · -1.0 Avg Days vs MABD · 6.9% WM Fault Rate |
| 6 | Supply Chain — Fine Exposure & Root Cause | 41% Fine Eligible Rate · 213 PO Lines · Root cause 43/47/51 breakdown |
| 7 | Supply Chain — Carrier & Freight | Carrier scorecard by SCAC · Collect vs Prepaid · MABD timing by carrier |

---

## Suppliers & Carriers in Model

**Suppliers:** FreshCo · Hydra Beauty · Peak Snacks · PetJoy · Scintilla Brands

**Carriers (SCAC):** BYLR (Baylor) · CRCR (Crete) · CTII (Central Transport) · HJBT (J.B. Hunt) · JBR (J.B. Hunt) · PRIJ (Prime Inc) · SCDS (Schneider) · SWFT (Swift) · WENP (Werner) · WM (Private Fleet)

---

## So Whats

| Page | Deliverable Decks | 
|---|---|
| 1 | [Executive Summary](https://nellynwhite.github.io/Retail-CPG-Analytics-Portfolio/portfolio-pages/layer1_README.html) |
| 2 | [Sales Performance](https://nellynwhite.github.io/Retail-CPG-Analytics-Portfolio/portfolio-pages/layer2_executive_briefing.html) |
| 3 | [Technical Reference](https://nellynwhite.github.io/Retail-CPG-Analytics-Portfolio/portfolio-pages/layer3_technical_reference.html) | 
| 4 | [CPG Domain](https://nellynwhite.github.io/Retail-CPG-Analytics-Portfolio/portfolio-pages/layer4_cpg_domain.html) |
| 5 | [Process Judgment](https://nellynwhite.github.io/Retail-CPG-Analytics-Portfolio/portfolio-pages/layer5_process_judgment.html) |

---

## Tech Stack

- **Data Generation** — Python (pandas, numpy)
- **Storage** — CSV → MySQL (MySQL Workbench)
- **Analytics** — SQL (views, window functions, CTEs)
- **Visualization** — Power BI Desktop (DAX measures, star schema, 7-page dashboard)

---

## Key Technical Notes

- **Fiscal calendar** — Walmart 52-week calendar (Q1 starts February; FY ends last Friday of January). All cumulative measures use `FILTER(ALL(Dim_Date), ...)` patterns with `date_key` (format `YYYYWW`) — standard DAX time intelligence is incompatible with this structure.
- **date_key fix** — `week_id` 1–52 is non-unique across fiscal years. A `date_key` column (`202400 + [week_id]`) added in Power Query resolved this.
- **Boolean filters** — All `CALCULATE()` filters on flag columns use `= TRUE()` syntax.
- **OTIF model** — Includes MABD (Must Arrive By Date) tracking, freight type split (Collect vs Prepaid), carrier-level SCAC scoring, PO edit reason codes (43/47/51), fine exposure quantification, and Walmart Fault Rate isolation — mirroring Walmart's One Touch supplier portal.
- **Relationship design** — `Dim_Fineline → Dim_Category` deactivated to resolve ambiguous filter path. Use `USERELATIONSHIP()` when needed.
