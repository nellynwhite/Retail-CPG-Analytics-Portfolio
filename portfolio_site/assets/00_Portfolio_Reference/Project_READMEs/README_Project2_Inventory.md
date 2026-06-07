# Project 2 — Inventory & In-Stock Health

Simulate a Walmart replenishment analyst's view: on-hand positions, fill rates, weeks of supply, reorder triggers, and lost sales quantification. Dashboard page 3 surfaces a chain-wide WOS deficit costing an estimated **$4.14M in annual lost sales**.

**Dashboard page:** Page 3 (Inventory Health)

---

## Business Questions Answered

1. What is the in-stock rate by category and item?
2. Where are we losing the most sales to stockouts?
3. Which items are below WOS target?
4. What drove weekly stockout spikes?
5. How does fill rate vary by category?

---

## Actual Dashboard KPIs (from live model)

| KPI | Value |
|---|---|
| In-Stock Rate | 88.9% |
| Lost Sales Dollars | $4.14M |
| Avg WOS | 1.4 |
| Fill Rate | 87.3% |
| WOS vs Target | -0.6 |

---

## Store-Item Detail (Store 103 Sample)

| Item | Category | In-Stock Rate | Lost Sales $ | Avg WOS | WOS vs Target |
|---|---|---|---|---|---|
| Energy Drink 12pk | Beverages | 86.5% | $19,506 | 1.4 | -0.6 |
| Protein Bar Variety Pack | Snacks | 82.7% | $8,345 | 1.3 | -0.7 |
| Sparkling Water 8pk | Beverages | 88.5% | $6,998 | 1.4 | -0.6 |
| Fresh Breeze Softener | Home Care | 82.7% | $5,960 | 1.3 | -0.7 |
| Premium Shampoo | Beauty & PC | 92.3% | $4,880 | 1.4 | -0.6 |
| Dog Treats Chewy Bites | Pet | 90.4% | $4,934 | 1.4 | -0.6 |
| Hydrating Conditioner | Beauty & PC | 88.5% | $3,865 | 1.4 | -0.6 |
| Granola Clusters | Snacks | 92.3% | $2,878 | 1.4 | -0.6 |
| Kids Bubble Bath | Beauty & PC | 96.2% | $955 | 1.5 | -0.5 |

---

## DAX Measures — 03 Inventory Display Folder

```dax
In Stock Rate =
    DIVIDE(
        CALCULATE(COUNTROWS(Fact_Inventory), Fact_Inventory[in_stock_flag] = TRUE()),
        COUNTROWS(Fact_Inventory), 0)

OOS % = 1 - [In Stock Rate]
Avg Weeks of Supply = AVERAGE(Fact_Inventory[weeks_of_supply])
Lost Sales Units = SUM(Fact_Inventory[lost_sales_units])
Fill Rate = AVERAGE(Fact_Inventory[fill_rate])
```

Lost Sales Dollars calculated in `vw_InventoryHealth` SQL view: `lost_sales_units × base_price`.

---

## SQL Objects

```sql
SELECT * FROM vw_InventoryHealth;  -- Store × Item × Week with stock status
SELECT * FROM vw_InStockRate;      -- Category × Quarter summary
```

---

## Recruiter Talking Points

- Chain-wide in-stock rate of 88.9% is materially below the 95% Walmart vendor benchmark — quantified at $4.14M in lost sales
- Energy Drink 12pk has the worst per-store lost sales at $19,506; extrapolated across 500 stores this represents ~$9.75M annual exposure on a single item
- Every store-item in the sample shows WOS vs Target of -0.6 to -0.7, confirming this is structural across the chain, not isolated to specific stores
- Kids Bubble Bath is the only item above 95% in-stock (96.2%) with WOS of 1.5 — its replenishment model can serve as an internal benchmark
- Built stockout trend visual connecting weekly lost sales dollars to stockout event counts — the same format used in Walmart vendor business reviews
