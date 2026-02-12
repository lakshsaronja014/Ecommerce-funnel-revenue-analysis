# BigQuery E-commerce Funnel & Revenue Analysis

## Overview

This project analyzes event-level e-commerce data in BigQuery (SQL) to diagnose declining profit despite stable order volume.

The objective was to identify conversion bottlenecks, evaluate traffic quality, and assess unit economics impact using behavioral event data.

Credit: Lorenzo Rosa.

---

## Dataset

Source: CSV dataset from Lorenzo Rosa’s SQL analytics project.

Table: `user_events.csv`

Columns:
- user_id
- event_type (page_view, add_to_cart, checkout_start, payment_info, purchase)
- event_date (TIMESTAMP)
- traffic_source
- amount (purchase revenue)

Analysis window: Last 30 days.

---

## Analytical Approach

The analysis was structured into four layers:

### 1) Funnel Conversion Analysis
- Page View → Add to Cart → Checkout → Payment → Purchase
- Stage-wise conversion rate calculation
- Drop-off identification between stages

### 2) Traffic Source Performance
- Conversion benchmarking by channel
- Channel efficiency ranking
- Identification of low-converting traffic sources

### 3) Time-to-Conversion
- Average time from first view to cart
- Average time from cart to purchase
- Total user journey duration

### 4) Revenue & Unit Economics Diagnostics
- Total revenue
- Average Order Value (AOV)
- Revenue per buyer
- Revenue per visitor
- CAC sensitivity simulation

---

## Key Findings

- Checkout → Purchase conversion ~80%+  
  → Payment stage is not the primary bottleneck.

- Social Media drives ~30% of traffic  
  → Lowest purchase conversion (~6%).

- Email channel shows highest purchase conversion (~13%+).

- AOV ≈ $115  
  → If CAC via low-converting channels exceeds ~$30–$40, margin compression is likely.

---

## Business Interpretation

The profit decline was not driven by checkout friction.

The primary issue was traffic acquisition efficiency and channel quality.

Improving unit economics requires:
- Reallocating spend toward higher-converting channels
- Reducing dependence on low-efficiency traffic
- Monitoring CAC relative to AOV thresholds

---

## Screenshots (BigQuery Output)

### Funnel Conversion Output
![Funnel]<img width="1914" height="912" alt="Screenshot 2026-02-12 101141" src="https://github.com/user-attachments/assets/aff86585-e532-4bc0-8436-e644ba3f660d" />


### Traffic Source Performance
![Traffic]<img width="1914" height="909" alt="Screenshot 2026-02-12 101230" src="https://github.com/user-attachments/assets/57bb82be-3049-4469-8e83-de0076fe518b" />


### Time-to-Conversion Analysis
![Time]<img width="1917" height="912" alt="Screenshot 2026-02-12 101337" src="https://github.com/user-attachments/assets/4d57b247-983b-486e-be74-a501336a4890" />


### Revenue Diagnostics
![Revenue]<img width="1914" height="912" alt="Screenshot 2026-02-12 101414" src="https://github.com/user-attachments/assets/29e400e4-8d2a-492b-a347-7ee8ea6467a8" />


---

## Tech Stack

- Google BigQuery
- SQL (CTEs, conditional aggregation, window functions, timestamp logic)
- Event-level Exploratory Data Analysis (EDA)

---

## Repository Structure

- `README.md` → Project documentation
- `dataset.md` → Table schema and structure
- `analysis.sql` → Complete SQL queries
- `screenshots/` → BigQuery result outputs

---

## How to Run

1. Upload the CSV dataset into Google BigQuery.
2. Create a dataset named: `data_01_sales`
3. Create a table named: `User_event`
4. Ensure schema matches `dataset.md`
5. Open `analysis.sql` in BigQuery and run each section sequentially.

Note:
Queries use a 30-day rolling window via `CURRENT_DATE()`. Adjust if needed.

---

## Summary

This project demonstrates structured SQL-based funnel diagnostics, traffic benchmarking, and revenue analysis using event-level data in BigQuery.

Focus was placed on business decision support rather than dashboard creation.
