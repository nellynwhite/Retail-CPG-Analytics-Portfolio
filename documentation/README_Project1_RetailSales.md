# Project 1 — Retail Sales Drivers (Scintilla Style)

Reproduce a Walmart Scintilla vendor portal experience: weekly TY vs. LY sales, YoY trends, item-level performance, promo mix, and category scorecards across 5 categories, 10 SKUs, 500 stores, and 52 fiscal weeks.

**Dashboard pages:** Page 1 (Sales Overview) · Page 2 (Weekly Performance)

---

## Business Questions Answered

1. Which categories are driving or dragging total sales growth?
2. Which items are growing fastest and where is growth slowing?
3. What is promo mix by category and how does it track weekly?
4. What is average selling price TY by item?
5. What is gross margin rate by category?

---

## Actual Dashboard KPIs (from live model)

| KPI | Value |
|---|---|
| Sales TY | $32.23M |
| Sales LY | $30.18M |
| YoY Dollar | $2.04M |
| YoY Pct | 6.8% |
| GM Rate TY | 28.5% |
| Units TY | 3M |
| Promo Mix Pct | 26.8% |
| Avg ASP TY | $9.76 |

---

## Category Scorecard (Page 1)

| Category | Sales TY | YoY % | GM Rate |
|---|---|---|---|
| Beverages | $11.55M | 8.0% | 31.0% |
| Home Care | $8.93M | 6.7% | 27.0% |
| Beauty & Personal Care | $4.73M | 7.1% | 30.0% |
| Snacks | $4.57M | 4.9% | 26.0% |
| Pet | $2.44M | 4.0% | 24.0% |

---

## Item Performance (Page 2)

| Item | Category | Sales TY | YoY % | ASP TY |
|---|---|---|---|---|
| Energy Drink 12pk | Beverages | $8.66M | 8.3% | $14.77 |
| Protein Bar Variety Pack | Snacks | $3.16M | 7.2% | $9.81 |
| Sparkling Water 8pk | Beverages | $2.89M | 7.2% | $6.86 |
| Premium Shampoo | Beauty & PC | $2.28M | 7.8% | $8.84 |
| Fresh Breeze Softener | Home Care | $2.28M | 2.5% | $6.87 |
| Hydrating Conditioner | Beauty & PC | $1.61M | 7.3% | $7.85 |
| Granola Clusters | Snacks | $1.41M | 0.2% | $5.89 |
| Kids Bubble Bath | Beauty & PC | $0.84M | 4.7% | $5.82 |
| Dog Treats Chewy Bites | Pet | $2.44M | 4.0% | $8.79 |

---

## DAX Measures — 01 Sales & 05 Walmart Fiscal Calendar Folders

```dax
Total Sales TY = SUM(Fact_WeeklySales[sales_dollars_ty])
Sales % Chg YoY = DIVIDE([Total Sales TY] - [Total Sales LY], [Total Sales LY], 0)
Gross Margin % = DIVIDE([Gross Margin TY], [Total Sales TY], 0)
Promo Mix Pct = DIVIDE(CALCULATE([Total Sales TY], Fact_WeeklySales[is_on_promo] = TRUE()), [Total Sales TY], 0)

-- Fiscal calendar (DATESYTD incompatible with 52-week calendar)
Sales YTD =
    CALCULATE([Total Sales TY],
        FILTER(ALL(Dim_Date),
            Dim_Date[year] = MAX(Dim_Date[year]) &&
            Dim_Date[date_key] <= MAX(Dim_Date[date_key])))
```

---

## SQL Objects

```sql
SELECT * FROM vw_SalesDrivers;       -- Week × Store × Item with YoY
SELECT * FROM vw_KPICards;            -- Single-row top-line summary
SELECT * FROM vw_CategoryScorecard;   -- Category × Quarter rollup
SELECT * FROM vw_Rolling4WkSales;     -- 4-week moving average by item
```

---

