# RetailX Orders Analysis

End-to-end sales analysis on a retail orders dataset using Python and Pandas. The project cleans raw transactional data, engineers revenue metrics, and answers five core business questions around category performance, monthly trends, customer behaviour, regional distribution, and order health.

---


## Project Overview

**Goal:** Extract actionable business insights from raw retail order data.

**Business Questions Answered:**
1. Which product categories drive the most revenue?
2. How does monthly revenue trend over time (MoM growth)?
3. Are customers repeat buyers or one-time purchasers?
4. Which regions generate the highest average order value?
5. What is the financial impact of returns and cancellations?

---

## Dataset

**File:** `fact_orders_clean.csv` (sourced from `retailx_raw_orders.xlsx`)

| Field | Description |
|---|---|
| `order_id` | Unique order identifier (e.g. ORD-1035) |
| `customer_id` | Customer reference code |
| `customer_name` | Customer full name |
| `product_name` | Product purchased |
| `category` | Product category |
| `quantity` | Units ordered |
| `unit_price` | Price per unit (INR) |
| `discount` | Discount applied (%) |
| `region` | Geographic region |
| `status` | Order status: Completed / Cancelled / Returned / Pending |
| `order_date` | Date of order |

**Scale:**
- 300 orders
- 15 unique customers
- 15 unique products across 9 categories
- Date range spans ~1 year

---

## Tools & Libraries

- Python 3.x
- Pandas — data manipulation and aggregation
- Jupyter Notebook — analysis environment

---


## Analysis Performed


### 1. Revenue by Category
Grouped orders by category; computed total revenue, order count, and average order value. Sorted descending by revenue.

### 2. Monthly Sales Trend
Aggregated revenue and order count by month. Calculated Month-over-Month (MoM) growth percentage using `pct_change()`.

### 3. Customer Retention
Counted distinct orders per customer. Identified one-time buyers (order count = 1) and calculated their share as a churn risk signal.

### 4. Average Order Value by Region
Grouped by region to compute total revenue, order volume, and AOV. Sorted by AOV to surface high-value markets.

### 5. Returns & Cancellations Impact
Isolated Returned and Cancelled orders to quantify revenue at risk. Calculated each status as a percentage of total orders and summed lost revenue.

---

## Key Findings

### Revenue by Category
Electronics dominates with **₹6,55,232** — nearly **49.5% of total revenue**. Footwear is second at ₹1,73,120. Stationery sits at the bottom at ₹12,917, more than 50x lower than Electronics.

### Revenue Loss
**28% of potential revenue (₹3,71,000) was lost** to returns and cancellations. That is a significant operational problem — roughly 1 in 4 rupees earned is given back.

| Status | Orders | Revenue |
|---|---|---|
| Completed | 187 (62.3%) | ₹8,17,847 |
| Cancelled | 40 (13.3%) | ₹2,19,012 |
| Pending | 38 (12.7%) | ₹1,35,229 |
| Returned | 35 (11.7%) | ₹1,51,985 |

### Regional Performance
**"Unknown" region accounts for 101 orders (33.7%) and ₹3,91,028 in revenue** — the single largest regional bucket. This is a data collection failure, not a region. It needs to be fixed before regional strategy decisions can be made.

Among mapped regions: East leads in revenue (₹2,75,155), followed by West (₹2,59,930).

### Customer Behaviour
All 15 customers are repeat buyers — zero one-time purchasers in this dataset. Priya Nair is the top customer (30 orders, ₹1,24,452). The top 3 customers account for ~27% of total revenue, indicating mild concentration risk.

### Product Concentration
Electronics alone drives nearly half of all revenue. The business is highly dependent on one category. If that category slows, the whole business slows.

---



Built as part of a retail analytics portfolio project to demonstrate end-to-end data analysis using Python.
