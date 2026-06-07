<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CPG Domain Reference — Promo, KPIs & Fiscal Calendar</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600&family=IBM+Plex+Sans:wght@300;400;500;600&display=swap');

  :root {
    --navy: #0A1628;
    --blue: #1B3A6B;
    --accent: #0066CC;
    --gold: #C8932A;
    --light-blue: #E8F0FA;
    --border: #CBD5E8;
    --text: #1A2340;
    --muted: #5A6A8A;
    --white: #FFFFFF;
    --green: #1A7A4A;
    --green-light: #E6F4EE;
    --red: #C23B22;
    --red-light: #FDECEA;
    --amber: #8C5A00;
    --amber-light: #FFF4E5;
    --code-bg: #0D1F35;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }
  body { font-family: 'IBM Plex Sans', sans-serif; background: #F4F6FB; color: var(--text); font-size: 14px; line-height: 1.6; }
  .page { max-width: 960px; margin: 0 auto; background: var(--white); }

  .header {
    background: var(--navy);
    padding: 36px 48px 28px;
    border-bottom: 4px solid var(--gold);
  }

  .header-top { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 10px; }

  .badge {
    background: var(--gold);
    color: var(--navy);
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 4px 10px;
    border-radius: 2px;
    white-space: nowrap;
  }

  .header h1 { font-size: 24px; font-weight: 600; color: var(--white); margin-bottom: 4px; }
  .header-sub { font-size: 13px; color: #8AA4CC; font-weight: 300; }

  .content { padding: 36px 48px; }
  .section { margin-bottom: 48px; }

  .section-label {
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after { content: ''; flex: 1; height: 1px; background: var(--border); }

  /* PROMO FRAMEWORK */
  .promo-framework {
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 20px;
  }

  .promo-fw-header {
    background: var(--navy);
    padding: 14px 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .promo-fw-title { font-size: 13px; font-weight: 600; color: var(--white); }
  .promo-fw-sub { font-size: 11px; color: #8AA4CC; }

  .promo-flow {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    border-bottom: 1px solid var(--border);
  }

  .promo-step {
    padding: 16px 14px;
    border-right: 1px solid var(--border);
    position: relative;
  }

  .promo-step:last-child { border-right: none; }

  .promo-step::after {
    content: '→';
    position: absolute;
    right: -9px;
    top: 50%;
    transform: translateY(-50%);
    color: var(--muted);
    font-size: 14px;
    z-index: 1;
  }

  .promo-step:last-child::after { display: none; }

  .step-num {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 10px;
    color: var(--gold);
    font-weight: 600;
    margin-bottom: 4px;
  }

  .step-title { font-size: 12.5px; font-weight: 600; color: var(--navy); margin-bottom: 4px; }
  .step-body { font-size: 11.5px; color: var(--muted); line-height: 1.45; }

  .promo-body { padding: 16px 20px; }

  /* MECHANIC DETAIL TABLE */
  .mech-detail-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 12.5px;
  }

  .mech-detail-table thead th {
    background: var(--navy);
    color: #8AA4CC;
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 9px 12px;
    text-align: left;
  }

  .mech-detail-table tbody tr { border-bottom: 1px solid var(--border); }
  .mech-detail-table td { padding: 11px 12px; vertical-align: top; }

  .mech-badge {
    display: inline-block;
    font-size: 10px;
    font-weight: 700;
    padding: 2px 8px;
    border-radius: 2px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
  }

  .mech-tpr { background: #EAF1FB; color: #0A4F8C; border: 1px solid #B0CCEA; }
  .mech-bogo { background: var(--green-light); color: var(--green); border: 1px solid #9ECBB8; }
  .mech-feat { background: var(--amber-light); color: var(--amber); border: 1px solid #F0C980; }
  .mech-disp { background: #F0EAF8; color: #5A1A6B; border: 1px solid #C0A0D8; }

  .lift-bar {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .lift-fill {
    height: 8px;
    border-radius: 4px;
  }

  .lift-tpr { background: #2E6AAA; width: 50px; }
  .lift-bogo { background: var(--green); width: 100px; }
  .lift-feat { background: var(--amber); width: 83px; }
  .lift-disp { background: #5A1A6B; width: 40px; }

  .lift-pct { font-family: 'IBM Plex Mono', monospace; font-size: 12px; font-weight: 600; }

  /* BASE + INCREMENT VISUAL */
  .lift-visual {
    background: var(--light-blue);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 16px 20px;
    margin-top: 16px;
  }

  .lift-visual-title {
    font-size: 11px;
    font-weight: 600;
    color: var(--navy);
    letter-spacing: 0.04em;
    margin-bottom: 12px;
  }

  .lift-bars-visual {
    display: flex;
    align-items: flex-end;
    gap: 8px;
    height: 80px;
    margin-bottom: 6px;
  }

  .lvbar { border-radius: 3px 3px 0 0; position: relative; }
  .lvbar-label {
    position: absolute;
    bottom: -20px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 10px;
    color: var(--muted);
    white-space: nowrap;
  }

  .lvbar-val {
    position: absolute;
    top: -18px;
    left: 50%;
    transform: translateX(-50%);
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    font-weight: 600;
    white-space: nowrap;
  }

  /* KPI CHEAT SHEET */
  .kpi-cheat-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
  }

  .kpi-entry {
    background: var(--white);
    padding: 14px 16px;
  }

  .kpi-entry-name {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 12.5px;
    font-weight: 600;
    color: var(--accent);
    margin-bottom: 3px;
  }

  .kpi-entry-full { font-size: 11px; color: var(--muted); margin-bottom: 6px; }

  .kpi-entry-def {
    font-size: 12.5px;
    color: var(--text);
    line-height: 1.5;
    margin-bottom: 6px;
  }

  .kpi-entry-formula {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    background: #EEF3FA;
    color: var(--blue);
    padding: 3px 8px;
    border-radius: 2px;
    display: inline-block;
    margin-bottom: 4px;
  }

  .kpi-entry-context { font-size: 11px; color: var(--muted); font-style: italic; line-height: 1.45; }

  .kpi-section-header {
    background: var(--navy);
    color: var(--gold);
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 8px 16px;
    grid-column: 1 / -1;
  }

  /* FISCAL CALENDAR */
  .fiscal-block {
    background: var(--navy);
    border-radius: 4px;
    padding: 24px 28px;
    margin-bottom: 16px;
  }

  .fiscal-title { font-size: 13px; font-weight: 600; color: var(--white); margin-bottom: 16px; }

  .fiscal-quarters {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin-bottom: 20px;
  }

  .fiscal-q {
    border: 1px solid rgba(255,255,255,0.15);
    border-radius: 4px;
    overflow: hidden;
  }

  .fq-header {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 5px 10px;
    color: var(--navy);
  }

  .fq-q1 { background: #C8932A; }
  .fq-q2 { background: #2E6AAA; }
  .fq-q3 { background: #1A7A4A; }
  .fq-q4 { background: #5A1A6B; }

  .fq-body { padding: 8px 10px; }
  .fq-months { font-size: 12px; color: #E8EEFF; margin-bottom: 4px; }
  .fq-weeks { font-family: 'IBM Plex Mono', monospace; font-size: 10px; color: #5A7A9A; }
  .fq-event { font-size: 10px; color: #F0C070; margin-top: 4px; }

  .fiscal-note {
    background: rgba(255,255,255,0.05);
    border: 1px solid rgba(255,255,255,0.1);
    border-left: 3px solid var(--gold);
    border-radius: 0 4px 4px 0;
    padding: 10px 14px;
  }

  .fiscal-note-title { font-size: 10px; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; color: var(--gold); margin-bottom: 6px; }

  .fiscal-note-body { font-size: 12px; color: #B8CADD; line-height: 1.6; }

  .dax-problem-block {
    margin-top: 16px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .dax-box {
    border-radius: 4px;
    overflow: hidden;
    border: 1px solid var(--border);
  }

  .dax-box-header {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 7px 12px;
    color: var(--white);
  }

  .dax-bad { background: var(--red); }
  .dax-good { background: var(--green); }

  .dax-box-body {
    padding: 10px 12px;
    background: var(--code-bg);
    font-family: 'IBM Plex Mono', monospace;
    font-size: 11px;
    color: #B8CADD;
    line-height: 1.6;
  }

  .dax-note { font-size: 11.5px; padding: 8px 12px; background: var(--white); color: var(--muted); border-top: 1px solid var(--border); }

  /* OTIF EXPLAINER */
  .otif-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .otif-card {
    border: 1px solid var(--border);
    border-radius: 4px;
    overflow: hidden;
  }

  .otif-card-header {
    background: var(--navy);
    padding: 10px 16px;
    font-size: 12px;
    font-weight: 600;
    color: var(--white);
  }

  .otif-card-body { padding: 14px 16px; }

  .otif-formula {
    font-family: 'IBM Plex Mono', monospace;
    font-size: 13px;
    font-weight: 600;
    color: var(--accent);
    margin-bottom: 8px;
    padding: 8px 12px;
    background: var(--light-blue);
    border-radius: 4px;
  }

  .otif-body-text { font-size: 12.5px; color: var(--text); line-height: 1.55; }

  .otif-threshold {
    margin-top: 10px;
    display: flex;
    gap: 8px;
    align-items: center;
  }

  .thresh-label { font-size: 11px; color: var(--muted); }
  .thresh-val { font-family: 'IBM Plex Mono', monospace; font-size: 13px; font-weight: 600; }
  .thresh-ok { color: var(--green); }
  .thresh-warn { color: var(--amber); }
  .thresh-bad { color: var(--red); }

  /* FOOTER */
  .footer {
    background: var(--navy);
    padding: 18px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .footer-note { font-size: 11px; color: #4A6080; font-family: 'IBM Plex Mono', monospace; }
  .footer-tag { font-size: 11px; color: var(--gold); font-weight: 600; }
</style>
</head>
<body>
<div class="page">

  <div class="header">
    <div class="header-top">
      <div>
        <h1>CPG Domain Reference</h1>
        <div class="header-sub">Trade promotion framework · Retail KPI definitions · Walmart 52-week fiscal calendar · OTIF standard</div>
      </div>
      <div class="badge">Layer 4 · CPG Domain Expertise</div>
    </div>
  </div>

  <div class="content">

    <!-- PROMO FRAMEWORK -->
    <div class="section">
      <div class="section-label">Trade promotion framework</div>

      <div class="promo-framework">
        <div class="promo-fw-header">
          <span class="promo-fw-title">Base + Incremental decomposition model</span>
          <span class="promo-fw-sub">Standard CPG framework for measuring promo effectiveness</span>
        </div>
        <div class="promo-flow">
          <div class="promo-step">
            <div class="step-num">Step 1</div>
            <div class="step-title">Establish base velocity</div>
            <div class="step-body">Non-promoted weekly unit rate for this SKU/store. Typically a 4–8 week pre-promo average, excluding adjacent promo weeks.</div>
          </div>
          <div class="promo-step">
            <div class="step-num">Step 2</div>
            <div class="step-title">Measure promo units</div>
            <div class="step-body">Actual units sold during the promo week. Source: Fact_WeeklySales where is_on_promo = 1.</div>
          </div>
          <div class="promo-step">
            <div class="step-num">Step 3</div>
            <div class="step-title">Calculate incremental</div>
            <div class="step-body">Incremental = Promo units − Base units. This is the net new demand generated by the promotion, not just total volume.</div>
          </div>
          <div class="promo-step">
            <div class="step-num">Step 4</div>
            <div class="step-title">Calculate trade ROI</div>
            <div class="step-body">ROI = Incremental Gross Margin ÷ Estimated Trade Spend. A value &gt;1.0 means the promotion more than paid for itself.</div>
          </div>
        </div>
        <div class="promo-body">
          <strong style="font-size:12px">Key caveat:</strong>
          <span style="font-size:12.5px; color:var(--muted)"> Post-promo weeks must be excluded from baseline calculations. Demand pull-forward (consumers stocking up during promo) depresses the following 1–2 weeks' sales and will artificially inflate the measured lift if not adjusted for.</span>
        </div>
      </div>

      <table class="mech-detail-table">
        <thead>
          <tr>
            <th>Mechanic</th>
            <th>Avg lift vs. base</th>
            <th>Primary driver</th>
            <th>Best use case</th>
            <th>Key risk</th>
            <th>In this model</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><span class="mech-badge mech-tpr">TPR</span><br><span style="font-size:11px;color:var(--muted)">Temporary Price Reduction</span></td>
            <td>
              <div class="lift-bar">
                <div class="lift-fill lift-tpr"></div>
                <span class="lift-pct">+15%</span>
              </div>
            </td>
            <td style="font-size:12px">Price sensitivity</td>
            <td style="font-size:12px">High-velocity commodity SKUs, competitive response</td>
            <td style="font-size:12px">Erodes base price perception at high frequency; trains deal-seeking behavior</td>
            <td style="font-family:'IBM Plex Mono',monospace; font-size:11px">promo_type = 'TPR'</td>
          </tr>
          <tr>
            <td><span class="mech-badge mech-bogo">BOGO</span><br><span style="font-size:11px;color:var(--muted)">Buy One Get One</span></td>
            <td>
              <div class="lift-bar">
                <div class="lift-fill lift-bogo"></div>
                <span class="lift-pct">+30%</span>
              </div>
            </td>
            <td style="font-size:12px">Household loading</td>
            <td style="font-size:12px">Trial conversion, shelf-stable categories (Home Care, Snacks)</td>
            <td style="font-size:12px">Strong pull-forward effect; watch 4-week post-promo dip vs. baseline</td>
            <td style="font-family:'IBM Plex Mono',monospace; font-size:11px">promo_type = 'BOGO'</td>
          </tr>
          <tr>
            <td><span class="mech-badge mech-feat">Feature</span><br><span style="font-size:11px;color:var(--muted)">Weekly Ad Feature</span></td>
            <td>
              <div class="lift-bar">
                <div class="lift-fill lift-feat"></div>
                <span class="lift-pct">+25%</span>
              </div>
            </td>
            <td style="font-size:12px">Awareness / reach</td>
            <td style="font-size:12px">New item launches, seasonal items, restage support</td>
            <td style="font-size:12px">Requires price reduction to fully activate; standalone feature with no price change underperforms</td>
            <td style="font-family:'IBM Plex Mono',monospace; font-size:11px">promo_type = 'Feature'</td>
          </tr>
          <tr>
            <td><span class="mech-badge mech-disp">Display</span><br><span style="font-size:11px;color:var(--muted)">In-Store Display</span></td>
            <td>
              <div class="lift-bar">
                <div class="lift-fill lift-disp"></div>
                <span class="lift-pct">+12%</span>
              </div>
            </td>
            <td style="font-size:12px">Impulse purchase</td>
            <td style="font-size:12px">End-cap or off-shelf placement; stacks with Feature for 3× effect</td>
            <td style="font-size:12px">Lowest standalone ROI; must be combined with Feature or TPR to justify trade investment</td>
            <td style="font-family:'IBM Plex Mono',monospace; font-size:11px">overlap_feature_display = 1</td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- KPI CHEAT SHEET -->
    <div class="section">
      <div class="section-label">CPG retail KPI reference — definitions & context</div>
      <div class="kpi-cheat-grid">

        <div class="kpi-section-header">Sales performance</div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">Sales Velocity</div>
          <div class="kpi-entry-full">Units per Store per Week (UPSPW)</div>
          <div class="kpi-entry-def">Average weekly unit sales per actively-selling store. The primary measure of how fast a SKU moves off the shelf independent of distribution.</div>
          <div class="kpi-entry-formula">Sales Units TY ÷ (# Stores Selling × 52 weeks)</div>
          <div class="kpi-entry-context">CPG context: Walmart uses velocity to determine ranging decisions. Low velocity = de-list risk. High velocity = reset/expansion opportunity.</div>
        </div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">ACV %</div>
          <div class="kpi-entry-full">All Commodity Volume weighted distribution</div>
          <div class="kpi-entry-def">% of total retailer sales volume (in $) coming from stores that carry your SKU. A SKU in 50% ACV reaches stores that generate half of the retailer's total revenue.</div>
          <div class="kpi-entry-formula">Σ(Sales Volume of Stocking Stores) ÷ Σ(Total Chain Sales Volume)</div>
          <div class="kpi-entry-context">CPG context: A new item at 80% ACV means most high-volume stores are stocking it — the distribution rollout is largely complete.</div>
        </div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">YoY % Chg</div>
          <div class="kpi-entry-full">Year-over-Year percentage change</div>
          <div class="kpi-entry-def">Percentage change in sales vs. the same period last fiscal year. In this model, TY/LY comparisons are stored as columns to accommodate the NRF 52-week calendar.</div>
          <div class="kpi-entry-formula">(Sales TY − Sales LY) ÷ Sales LY</div>
          <div class="kpi-entry-context">CPG context: Walmart's Scintilla portal displays this metric by default. A vendor review typically starts here before decomposing the delta into price vs. volume drivers.</div>
        </div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">Promo Mix %</div>
          <div class="kpi-entry-full">Promotional sales as share of total sales</div>
          <div class="kpi-entry-def">Percentage of total dollar sales achieved during promoted weeks. High promo mix (>35%) signals the category may be over-reliant on trade investment to sustain velocity.</div>
          <div class="kpi-entry-formula">Promo Sales TY ÷ Total Sales TY</div>
          <div class="kpi-entry-context">CPG context: This model runs at 26.8% promo mix — within normal range but approaching the threshold where base velocity erosion becomes a risk.</div>
        </div>

        <div class="kpi-section-header">Inventory & replenishment</div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">In-Stock Rate</div>
          <div class="kpi-entry-full">Percentage of observations with adequate stock</div>
          <div class="kpi-entry-def">% of week × store × item observations where on-hand inventory was sufficient to meet demand. Measured as a binary flag per row, averaged across the selection.</div>
          <div class="kpi-entry-formula">Σ(in_stock_flag = 1) ÷ Total observations</div>
          <div class="kpi-entry-context">CPG context: Walmart expects vendors to maintain ≥95% in-stock rate. This model averages 88.9%, representing a 6-point gap and $4.1M in quantified lost sales.</div>
        </div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">WOS</div>
          <div class="kpi-entry-full">Weeks of Supply</div>
          <div class="kpi-entry-def">On-hand inventory at end of period divided by average weekly demand. A forward-looking inventory health measure — how many weeks of current demand the current stock covers.</div>
          <div class="kpi-entry-formula">On-Hand EOP Units ÷ Avg Weekly Demand Units</div>
          <div class="kpi-entry-context">CPG context: Walmart guidance is ≥2.0 WOS. At 1.4 WOS (this model's average), the portfolio is vulnerable to stockouts during any demand spike or supply disruption.</div>
        </div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">Fill Rate</div>
          <div class="kpi-entry-full">Order fulfillment rate</div>
          <div class="kpi-entry-def">Units sold as a percentage of units demanded. The gap between 100% and fill rate represents demand that could not be fulfilled — this is the source of lost sales quantification.</div>
          <div class="kpi-entry-formula">Actual Sold Units ÷ Demand Forecast Units</div>
          <div class="kpi-entry-context">CPG context: This model averages 87.3% fill rate. At a portfolio level, a 1pp improvement in fill rate translates to approximately $370K in recovered lost sales at current velocity.</div>
        </div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">EDLP vs. Hi-Lo</div>
          <div class="kpi-entry-full">Every Day Low Price vs. High-Low pricing strategy</div>
          <div class="kpi-entry-def">EDLP (Walmart's core strategy): consistently low regular prices with minimal promotions. Hi-Lo: higher regular prices offset by frequent deep-discount promotions. Most CPG vendors must align their trade strategy to the retailer's pricing philosophy.</div>
          <div class="kpi-entry-formula">Not a formula — a pricing strategy classification</div>
          <div class="kpi-entry-context">CPG context: Walmart operates on EDLP. This means trade spend should optimize for efficiency (Feature/Display) over frequency (heavy TPR), which conflicts with Hi-Lo-trained vendor teams.</div>
        </div>

        <div class="kpi-section-header">Supply chain</div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">OTIF</div>
          <div class="kpi-entry-full">On-Time In-Full delivery rate</div>
          <div class="kpi-entry-def">A PO is OTIF-compliant only if it was delivered both on time (MABD ±1 day) and in full (≥98% of ordered quantity). Both conditions must be true simultaneously — partial credit is not granted.</div>
          <div class="kpi-entry-formula">OTIF = On-Time AND In-Full (binary AND logic)</div>
          <div class="kpi-entry-context">CPG context: Walmart's OTIF standard is stringent. Missing either component on a single PO results in a non-compliant delivery, triggering potential fines. This model's 91.3% average is 2.1pp below the 93.4% target.</div>
        </div>

        <div class="kpi-entry">
          <div class="kpi-entry-name">MAPE</div>
          <div class="kpi-entry-full">Mean Absolute Percentage Error</div>
          <div class="kpi-entry-def">Forecast accuracy measure. Average of the absolute percentage deviation between forecasted and actual demand. Lower is better. A naive forecast uses the prior year's same-week actuals as the forecast.</div>
          <div class="kpi-entry-formula">Mean(|Actual − Forecast| ÷ Actual) × 100</div>
          <div class="kpi-entry-context">CPG context: This model's ML forecast achieves 2.0% MAPE vs. 2.6% for the naive baseline — a 23% accuracy improvement that translates to fewer shortage events upstream.</div>
        </div>

      </div>
    </div>

    <!-- FISCAL CALENDAR -->
    <div class="section">
      <div class="section-label">Walmart 52-week NRF fiscal calendar — and why it breaks standard DAX</div>

      <div class="fiscal-block">
        <div class="fiscal-title">FY2024 fiscal calendar structure (NRF 4-5-4 layout)</div>
        <div class="fiscal-quarters">
          <div class="fiscal-q">
            <div class="fq-header fq-q1">Q1 · FY2024</div>
            <div class="fq-body">
              <div class="fq-months">Feb — Apr 2024</div>
              <div class="fq-weeks">Weeks 1–13</div>
              <div class="fq-event">⚑ FY starts last Fri. of January</div>
            </div>
          </div>
          <div class="fiscal-q">
            <div class="fq-header fq-q2">Q2 · FY2024</div>
            <div class="fq-body">
              <div class="fq-months">May — Jul 2024</div>
              <div class="fq-weeks">Weeks 14–26</div>
              <div class="fq-event">⚑ Memorial Day · 4th of July</div>
            </div>
          </div>
          <div class="fiscal-q">
            <div class="fq-header fq-q3">Q3 · FY2024</div>
            <div class="fq-body">
              <div class="fq-months">Aug — Oct 2024</div>
              <div class="fq-weeks">Weeks 27–39</div>
              <div class="fq-event">⚑ Back-to-school · Halloween</div>
            </div>
          </div>
          <div class="fiscal-q">
            <div class="fq-header fq-q4">Q4 · FY2024</div>
            <div class="fq-body">
              <div class="fq-months">Nov — Jan 2025</div>
              <div class="fq-weeks">Weeks 40–52</div>
              <div class="fq-event">⚑ Thanksgiving · Christmas · FY ends</div>
            </div>
          </div>
        </div>
        <div class="fiscal-note">
          <div class="fiscal-note-title">Critical design note</div>
          <div class="fiscal-note-body">Walmart's fiscal year ends on the last Friday of January, not December 31. Q1 begins in February, not January. This means standard Power BI time intelligence functions — DATEADD, SAMEPERIODLASTYEAR, DATESYTD — calculate based on the Gregorian calendar and produce wrong comparisons. A Q1 fiscal filter in Power BI using standard time intelligence returns January–March calendar data, which is Q4 in Walmart's fiscal year.</div>
        </div>
      </div>

      <div class="dax-problem-block">
        <div class="dax-box">
          <div class="dax-box-header dax-bad">❌ Standard time intelligence — breaks with NRF calendar</div>
          <div class="dax-box-body">Sales LY (WRONG) =
CALCULATE(
    [Total Sales TY],
    SAMEPERIODLASTYEAR(
        Dim_Date[Date]
    )
)

-- Problem: SAMEPERIODLASTYEAR maps to same
-- Gregorian calendar dates last year, not the
-- same NRF fiscal week. Week 1 of FY2024
-- (Feb 2) maps to Feb 2, 2023 — but that was
-- Week 2 of FY2023 in the NRF calendar.
-- YoY comparisons are off by 1–2 weeks.</div>
          <div class="dax-note">Produces incorrect YoY comparisons for any NRF-aligned retailer (Walmart, Target, Home Depot).</div>
        </div>
        <div class="dax-box">
          <div class="dax-box-header dax-good">✓ Column-based pattern — correct for NRF calendar</div>
          <div class="dax-box-body">Sales LY (CORRECT) =
SUM(
    Fact_WeeklySales[sales_dollars_ly]
)

-- Pattern: TY and LY values are stored in the
-- SAME fact row, pre-aligned to the same
-- fiscal week number. Week 3 TY is always
-- compared to Week 3 LY — guaranteed by
-- the data generation logic, not by DAX.

-- Fiscal year filter still works correctly:
-- Filter on Dim_Date[fiscal_year_label]
-- instead of calendar year.</div>
          <div class="dax-note">This pattern mirrors how Walmart Scintilla exports data and eliminates all fiscal calendar DAX edge cases.</div>
        </div>
      </div>
    </div>

    <!-- OTIF EXPLAINER -->
    <div class="section">
      <div class="section-label">OTIF — Walmart's primary supplier performance standard</div>
      <div class="otif-grid">
        <div class="otif-card">
          <div class="otif-card-header">On-Time component</div>
          <div class="otif-card-body">
            <div class="otif-formula">Delivered within ±1 day of MABD</div>
            <div class="otif-body-text">MABD = Must Arrive By Date. Walmart specifies the exact date a PO must arrive at the DC. Deliveries arriving more than 1 day early or 1 day late are considered non-compliant for the on-time component, regardless of quantity received.</div>
            <div class="otif-threshold">
              <span class="thresh-label">Portfolio avg:</span>
              <span class="thresh-val thresh-warn">On-time component varies by supplier</span>
            </div>
          </div>
        </div>
        <div class="otif-card">
          <div class="otif-card-header">In-Full component</div>
          <div class="otif-card-body">
            <div class="otif-formula">Received ÷ Ordered ≥ 98%</div>
            <div class="otif-body-text">Walmart requires that ≥98% of the ordered quantity on a PO is received. A PO for 10,000 units that delivers 9,700 units is in-full non-compliant (97% &lt; 98% threshold), even if it arrived on time.</div>
            <div class="otif-threshold">
              <span class="thresh-label">In-full gap creates:</span>
              <span class="thresh-val thresh-bad">Shortage units → in-stock risk</span>
            </div>
          </div>
        </div>
        <div class="otif-card">
          <div class="otif-card-header">OTIF combined — AND logic</div>
          <div class="otif-card-body">
            <div class="otif-formula">OTIF = On-Time AND In-Full</div>
            <div class="otif-body-text">A delivery is OTIF-compliant only if BOTH components are met on the same PO. A delivery that arrives perfectly on time but is 3% short of ordered quantity is an OTIF failure. This binary AND logic is the most common source of OTIF confusion for vendors new to Walmart.</div>
            <div class="otif-threshold">
              <span class="thresh-label">This model:</span>
              <span class="thresh-val thresh-warn">91.3% avg (−2.1pp vs. 93.4% target)</span>
            </div>
          </div>
        </div>
        <div class="otif-card">
          <div class="otif-card-header">Financial consequences</div>
          <div class="otif-card-body">
            <div class="otif-formula">Fine = % of PO value × non-compliant rate</div>
            <div class="otif-body-text">Walmart charges a percentage of the PO invoice value for OTIF non-compliance once a vendor falls below their contractual target. For large-volume suppliers, this can represent material P&L exposure. OTIF fine exposure is tracked as a dedicated measure in this portfolio's Power BI model.</div>
            <div class="otif-threshold">
              <span class="thresh-label">Measured in:</span>
              <span class="thresh-val" style="color:var(--accent)">OTIF Fine Exposure $ DAX measure</span>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>

  <div class="footer">
    <span class="footer-note">CPG domain reference · NRF 52-week fiscal calendar · Walmart OTIF standard · Trade promo framework</span>
    <span class="footer-tag">Layer 4 · CPG Domain Expertise</span>
  </div>

</div>
</body>
</html>
