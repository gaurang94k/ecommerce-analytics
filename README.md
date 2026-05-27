# E-Commerce Analytics

SQL-driven business analysis of a Brazilian e-commerce marketplace — 99k orders, 3k sellers, 74 product categories across two years of transaction data. Each notebook tackles a real stakeholder question with SQL queries, visualizations, and actionable recommendations.

Built with DuckDB for portable, zero-config SQL (same syntax as PostgreSQL).

## What's Inside

### [01 — Revenue & Growth](notebooks/01_revenue_and_growth.ipynb)
Monthly revenue trends, month-over-month growth rates, top product categories, revenue concentration (Pareto), payment method breakdown, day-of-week patterns.

**Key finding:** Revenue scaled ~25x in under two years, peaking near R$1M/month. 24% of categories generate 80% of revenue — moderate concentration. Credit cards with installments dominate (74% of transactions, avg 3.5 installments), meaning top-line revenue and actual cash collected diverge significantly.

### [02 — Customer Behavior](notebooks/02_customer_behavior.ipynb)
Repeat purchase rates, monthly cohort retention heatmap, time-to-second-purchase, new vs returning revenue split, AOV by purchase number.

**Key finding:** Only 3% of customers ever make a second purchase — 97% buy once and disappear. The business is almost entirely acquisition-driven (R$12.9M new vs R$358k returning). Median time to second purchase is 29 days, giving a tight re-engagement window.

### [03 — Delivery & Operations](notebooks/03_delivery_and_operations.ipynb)
Delivery time distribution, late delivery rates, delivery by state, late delivery impact on reviews (dose-response), monthly delivery trend.

**Key finding:** Late deliveries average 2.57 stars vs 4.29 for on-time — a 1.7-point gap. The damage is proportional: 1-2 weeks late craters to 1.68 stars. The cheapest fix may be adjusting delivery estimates for remote states rather than overhauling logistics.

### [04 — Seller Performance](notebooks/04_seller_performance.ipynb)
Seller revenue concentration, tier segmentation, quality ratings, geographic distribution.

**Key finding:** 18% of sellers generate 80% of revenue. São Paulo accounts for ~60% of sellers and 64% of revenue — directly explaining why remote-state customers face longer delivery times.

## SQL Concepts Demonstrated

- Multi-table JOINs (2, 3, and 4-table joins)
- Window functions — LAG, ROW_NUMBER, RANK, running SUM, PARTITION BY
- Common Table Expressions (CTEs, including multi-CTE chains)
- Cohort retention analysis pattern
- Pareto / cumulative distribution analysis
- Date manipulation — DATE_TRUNC, DATEDIFF, DAYNAME
- Conditional aggregation — CASE inside SUM, AVG, COUNT
- Percentile calculations — PERCENTILE_CONT
- Subqueries and HAVING clauses

## Dataset

[Olist Brazilian E-Commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) — real, anonymized order data from a Brazilian marketplace (2016–2018). Seven tables covering orders, items, payments, reviews, products, sellers, and customers.

## Setup

```bash
pip install -r requirements.txt
```

Download the dataset from Kaggle, place the CSV files in `data/`, then:

```bash
cd notebooks/
jupyter notebook
```

## Tech Stack

- **SQL Engine:** DuckDB (PostgreSQL-compatible syntax)
- **Environment:** Jupyter Notebook
- **Visualization:** matplotlib
- **Language:** Python 3.11+
