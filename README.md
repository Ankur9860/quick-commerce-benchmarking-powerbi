# Quick-Commerce Financial & Supply Chain Benchmarking
### Blinkit vs Zepto vs Swiggy Instamart (FY2024–FY2026) · Power BI

A 7-page Power BI dashboard that compares India's three largest quick-commerce platforms on growth, profitability, dark-store productivity and unit economics, built **only on real, publicly reported company data** (no synthetic or estimated figures).

![Overview](images/01_overview.png)

---

## Key findings (FY2026)

| Metric | Blinkit | Zepto | Instamart |
|---|---|---|---|
| Orders (million) | 916.6 | 640.2 | 412.2 |
| Share of orders | 46.6% | 32.5% | 20.9% |
| Dark stores (Mar 2026) | 2,243 | 1,139 | 1,143 |
| Adjusted EBITDA per order (₹) | −3.0 | −78.8 | −85.2 |
| Orders per store per day (Q4 FY26) | ~1,357 | ~2,049 | ~1,095 |

1. **Fast growth:** the three platforms delivered **1,969 million orders** in FY26, up **89%**, from **4,525 dark stores** (+1,174 in the year).
2. **Blinkit is at break-even:** −₹3 adjusted EBITDA per order for FY26, and EBITDA-positive in Q3 FY26 (+₹4 cr) and Q4 FY26 (+₹37 cr).
3. **Zepto improved the most:** loss per order fell from −₹136.2 (FY25) to −₹78.8 (FY26), mainly because marketing cost per order dropped from ₹52.0 to ₹1.0.
4. **Instamart is under-utilised:** at Zepto's store productivity it could serve the same order volume with about **610 stores instead of 1,143**.
5. **Small savings matter:** every ₹10 saved per order is worth about **₹412 crore a year** at Instamart's FY26 volume.

---

## Dashboard pages

| # | Page | What it shows |
|---|---|---|
| 1 | Overview | Orders, dark stores, combined adjusted EBITDA, order share, EBITDA per order trend, company scorecard |
| 2 | Financial | Revenue by company, quarterly adjusted EBITDA (12 quarters) |
| 3 | Supply chain | Dark-store network growth, orders per store per day, stores added, **Instamart capacity planner** (what-if) |
| 4 | Unit Economics | EBITDA per order vs break-even, **what-if simulator** for savings per order |
| 5 | Zepto case study | Cost per order breakdown, gross and EBITDA margin, free cash flow per order, inventory days |
| 6 | AI Insights | Order forecast (Power BI exponential smoothing), loss-per-order trend review, recommendations |
| 7 | Methodology | Sources, formulas, limitations, supply chain KPIs to track with internal data |

Full dashboard: [`QuickCommerce_Benchmarking.pdf`](QuickCommerce_Benchmarking.pdf)

| Supply chain | Unit economics |
|---|---|
| ![Supply chain](images/03_supply_chain.png) | ![Unit economics](images/04_unit_economics.png) |

---

## Data sources

- **Zepto UDRHP-I (8 June 2026)** – peer KPI comparison for Blinkit, Zepto and Instamart, Q1 FY24 to Q4 FY26 (pp.162–174); Zepto cost per order, cash flow and inventory (pp.404, 406, 549–550, 555–556). Available on the SEBI website.
- **Eternal Ltd Annual Report FY2024-25** (p.23) – used to cross-check Blinkit FY24–FY25 figures.

Every value in `data/QuickCommerce_Peer_Data.xlsx` has its source document and page number.

## Key formulas

- Adjusted EBITDA per order (₹) = Adjusted EBITDA (₹ cr) × 10 ÷ Orders (million)
- Orders per store per day = orders per day in the quarter ÷ closing dark stores
- Stores needed (capacity planner) = orders per day ÷ target orders per store per day
- Simulated EBITDA = (EBITDA per order + saving per order) × orders

Example DAX measure:

```DAX
Adj EBITDA per Order (₹) =
DIVIDE ( [Adj EBITDA (Cr)] * 10, [Total Orders (Mn)] )
```

## Limitations

- **Revenue is not comparable** across companies: Zepto books full sale value, Blinkit moved to an inventory-led model from Q2 FY26, and Instamart earns mainly fees. Orders and EBITDA per order are used for comparison instead.
- Stockouts, wastage, fill rate and delivery time are **not publicly disclosed**, so they are not covered.
- Detailed cost, cash flow and inventory data is available for **Zepto only**.
- Adjusted EBITDA is a company-defined measure, and Zepto's data comes from a draft prospectus that may change.
- The forecast is illustrative only. Power BI anomaly detection was tested but flagged no points with only 12 quarters of data.

## Tools

Power BI Desktop (DAX, what-if parameters, forecasting) · Excel (data collection and source tracking)

## Repository structure

```
├── QuickCommerce_Benchmarking.pbix   # Power BI file
├── QuickCommerce_Benchmarking.pdf    # All 7 pages
├── data/
│   └── QuickCommerce_Peer_Data.xlsx  # Source data with page references
├── images/                           # Page screenshots
└── README.md
```

---

**Author:** Ankur. Feedback welcome via LinkedIn or GitHub issues.
