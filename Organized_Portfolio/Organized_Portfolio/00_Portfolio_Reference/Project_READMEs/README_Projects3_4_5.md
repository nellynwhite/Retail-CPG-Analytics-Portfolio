# Project 3 — Promo & Category Analytics

Evaluate promotional effectiveness across BOGO, Feature, Display, and TPR mechanics. Measure incremental lift, trade spend ROI, and supplier-level promo investment — surfaced on Page 4 of the dashboard.

**Dashboard page:** Page 4 (Promo Analytics)

---

## Actual Dashboard KPIs (from live model)

| KPI | Value |
|---|---|
| Avg Promo Lift Pct | 19.9% |
| Total Trade Spend | $496K |
| Avg Trade ROI | 2.56 |
| Incremental Units | 150K |

---

## Lift & ROI by Mechanic (actual dashboard data)

| Promo Type | Avg Lift % | Key Insight |
|---|---|---|
| BOGO | 30.0% | Highest lift; zero recorded trade spend — supplier-funded |
| Feature | 25.0% | Second-highest lift; Energy Drink 12pk Feature: $50,243 trade spend, 10.95x ROI |
| Display | 12.0% | Lowest lift but best ROI: Dog Treats 48.28x, Energy Drink 46.76x |
| TPR | 15.0% | Mid lift; Dog Treats TPR: $36,162 spend, 1.24x ROI — lowest paid-mechanic ROI |

---

## Item × Mechanic Detail

| Item | Promo Type | Lift % | Trade Spend | ROI |
|---|---|---|---|---|
| Dog Treats Chewy Bites | BOGO | 30.0% | $0 | — |
| Dog Treats Chewy Bites | Display | 12.0% | $1,460 | 48.28 |
| Dog Treats Chewy Bites | Feature | 25.0% | $2,929 | 50.20 |
| Dog Treats Chewy Bites | TPR | 15.0% | $36,162 | 1.24 |
| Energy Drink 12pk | BOGO | 30.0% | $0 | — |
| Energy Drink 12pk | Display | 12.0% | $6,036 | 46.76 |
| Energy Drink 12pk | Feature | 25.0% | $50,243 | 10.95 |

---

## DAX Measures — 02 Promo Display Folder

```dax
Promo Sales TY = CALCULATE([Total Sales TY], Fact_WeeklySales[is_on_promo] = TRUE())
Promo Mix Pct = DIVIDE([Promo Sales TY], [Total Sales TY], 0)
Avg Promo Lift % = DIVIDE(SUM(Fact_PromoCalendar[promo_lift_pct]), COUNTROWS(Fact_PromoCalendar), 0)
Est Trade Spend = SUM(Fact_PromoCalendar[est_trade_spend])
Avg Trade ROI = DIVIDE(SUM(Fact_PromoCalendar[roi_estimate]), COUNTROWS(Fact_PromoCalendar), 0)
Promo Events TY = CALCULATE(COUNTROWS(Fact_PromoCalendar), Fact_PromoCalendar[is_promo_ty] = TRUE())
```

---

## Recruiter Talking Points

- Display delivers 35–40x higher ROI than TPR for the same items — a concrete, data-backed trade spend reallocation recommendation
- BOGO generates 30% lift with zero recorded trade cost — if supplier-funded, it is the highest-value mechanism in the portfolio
- Built item × mechanic cross-tab showing ROI variance across four promo types — the format used in Walmart JBP trade spend discussions
- Total Trade Spend and Incremental Units by supplier visual enables side-by-side supplier contribution comparison

---
---

# Project 4 — Supply Chain: OTIF, Fine Exposure & Carrier Analysis

Three-page supply chain module mirroring Walmart's One Touch vendor portal — OTIF scoring, fine exposure quantification by root cause, and carrier-level performance by SCAC code.

**Dashboard pages:** Page 5 (OTIF & Supplier Scorecard) · Page 6 (Fine Exposure & Root Cause) · Page 7 (Carrier & Freight Responsibility)

---

## Actual Dashboard KPIs (from live model)

| KPI | Value |
|---|---|
| In-Full Rate | 59.8% |
| OTIF Rate (Walmart Standard) | 54.2% |
| On-Time Rate | 90.3% |
| OTIF Fine Exposure | $304K |
| Avg Days vs MABD | -1.0 |
| Walmart Fault Rate | 6.9% |
| Fine Eligible Rate | 41.0% |
| Fine Eligible PO Lines | 213 |
| Avg Fine per Non-Compliant PO | $1,430 |

---

## Supplier Scorecard (Page 5)

| Supplier | On-Time Rate | In-Full Rate | OTIF Rate | On-Time Gap vs Goal |
|---|---|---|---|---|
| Scintilla Brands | 93.5% | 68.8% | 64.5% | +3.5% |
| FreshCo | 92.4% | 54.3% | 48.9% | +2.4% |
| Hydra Beauty | 91.5% | 68.1% | 62.4% | +1.5% |
| PetJoy | 91.3% | 45.7% | 41.3% | +1.3% |
| Peak Snacks | 82.8% | 50.5% | 43.0% | -7.2% |
| **Total** | **90.3%** | **59.8%** | **54.2%** | **+0.3%** |

---

## Fine Exposure Root Causes (Page 6)

| Code | Description | Priority |
|---|---|---|
| 43 | No Product Availability (Supplier) | Critical — drives majority of exposure |
| 47 | Incorrect Labeling (Supplier) | High — preventable process failure |
| 51 | Item Setup Issue (Supplier) | Medium — admin/onboarding issue |

---

## Carrier Scorecard (Page 7)

| SCAC | Carrier | On-Time | OTIF |
|---|---|---|---|
| BYLR | Baylor Trucking | 94.1% | 64.7% |
| CRCR | Crete Carrier | 100.0% | 47.6% |
| WENP | Werner Enterprises | 92.6% | 63.6% |
| HJBT | J.B. Hunt | 92.3% | 60.3% |
| WM | WM Private Fleet (Collect) | 91.3% | 50.0% |
| SCDS | Schneider National | 83.8% | 47.5% |
| CTII | Central Transport | 87.5% | 43.8% |

---

## DAX Measures — 04 Supply Chain Display Folder

```dax
OTIF % = DIVIDE(CALCULATE(COUNTROWS(Fact_SupplyChain), Fact_SupplyChain[otif_flag] = TRUE()), COUNTROWS(Fact_SupplyChain), 0)
In Full % = DIVIDE(CALCULATE(COUNTROWS(Fact_SupplyChain), Fact_SupplyChain[in_full_flag] = TRUE()), COUNTROWS(Fact_SupplyChain), 0)
OTIF vs Target = [OTIF %] - [OTIF Target %]
Lead Time Variance = [Avg Lead Time Actual] - [Avg Lead Time Std]
Forecast MAPE (ML) = AVERAGE(Fact_SupplyChain[forecast_mape_ml])
```

---

## Key Analytical Insights

- **OTIF of 54.2% is driven by In-Full failures, not timing** — On-Time is 90.3% but In-Full is only 59.8%. The supply problem is order completeness, not delivery speed. CRCR achieves 100% on-time but only 47.6% OTIF, confirming this.
- **PetJoy has the worst In-Full rate at 45.7%** — less than half of PetJoy POs arrive complete, creating direct downstream in-stock risk for Dog Treats.
- **Peak Snacks is the only supplier below On-Time goal** at 82.8%, and its 50.5% In-Full makes it the second-worst overall. Granola Clusters' near-flat YoY (+0.2%) may reflect supply disruption from this supplier.
- **Walmart Fault Rate of 6.9% is a disputable offset** — WM Private Fleet (Collect) OTIF of 50.0% provides evidence for dispute credit submissions.
- **Root cause 47 (Incorrect Labeling) is 100% preventable** — a pre-shipment label audit would eliminate this category and reduce fine exposure by ~$75K annually.

---

## Recruiter Talking Points

- Built a three-page supply chain module that mirrors Walmart's One Touch portal — OTIF by supplier, fine exposure by root cause, and carrier scorecard by SCAC code
- Modeled MABD (Must Arrive By Date) tracking and separated On-Time from In-Full as distinct failure modes — the standard Walmart compliance framework
- Isolated Walmart Fault Rate (6.9%) from supplier fault — a critical distinction for OTIF dispute filing
- PO edit reason code analysis (43/47/51) identifies root causes that map directly to corrective action plans used in real vendor compliance conversations
- Carrier-level SCAC scoring with Collect vs Prepaid split demonstrates understanding of freight responsibility — who owns the late delivery matters for OTIF dispute credit

---
---

# Project 5 — SQL to Power BI Pipeline

End-to-end data pipeline: raw CSVs → MySQL schema → analytical SQL views → Power BI star schema → 7-page dashboard.

**Dashboard pages:** All pages (pipeline serves the entire report)

---

## Pipeline Architecture

```
CSVs → MySQL Workbench → SQL Views → Power BI Desktop (Import Mode) → 7-page Dashboard
  ↑           ↑               ↑               ↑                              ↑
generate_  schema DDL    walmart_scintilla  star schema +              77 DAX measures
data.py    + constraints    _views.sql      date_key fix               6 display folders
```

---

## Key SQL Views

| View | Dashboard Page |
|---|---|
| `vw_SalesDrivers` | Pages 1 & 2 |
| `vw_KPICards` | Page 1 — KPI cards |
| `vw_Rolling4WkSales` | Page 2 — trend line |
| `vw_InventoryHealth` | Page 3 |
| `vw_InStockRate` | Page 3 — category summary |
| `vw_PromoEffectiveness` | Page 4 |
| `vw_PromoSummary` | Page 4 — mechanic rollup |
| `vw_SupplyChainPerformance` | Pages 5–7 |
| `vw_SupplierScorecard` | Page 5 — OTIF matrix |
| `vw_MasterRetailFlat` | Backup flat table |

---

## Known Issues Resolved

| Issue | Resolution |
|---|---|
| week_id non-unique across fiscal years | Added `date_key = 202400 + [week_id]` in Power Query |
| Standard DAX time intelligence incompatible with 52-week calendar | FILTER/ALL patterns with date_key and year/quarter_id |
| Boolean flags return blank in some visuals | All CALCULATE filters use `= TRUE()` not `= 1` |
| Dim_Fineline → Dim_Category ambiguous path | Deactivated; use USERELATIONSHIP() when needed |
| MySQL 8 caching_sha2_password incompatibility with Power BI | Exported views as CSVs; loaded via CSV connector |

---

## Recruiter Talking Points

- Designed complete end-to-end pipeline from CSV generation through a 7-page Power BI dashboard with 77 DAX measures
- Identified and resolved 5 real data modeling problems including non-unique keys, incompatible time intelligence, and MySQL connector authentication failures
- Built SQL semantic layer (views) that decouples Power BI from raw table structure — the same pattern used in enterprise BI environments
- Supply chain module (Pages 5–7) demonstrates familiarity with Walmart's OTIF compliance framework including MABD, freight type, SCAC codes, and PO edit reason codes
