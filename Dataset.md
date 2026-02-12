# Dataset

Source: CSV dataset from Lorenzo Rosa’s SQL analytics project.

Imported into Google BigQuery.

## Table

Dataset: `data_01_sales`  
Table: `User_event`

## Columns

- user_id → Unique user identifier
- event_type → page_view, add_to_cart, checkout_start, payment_info, purchase
- event_date → Event timestamp
- traffic_source → Acquisition channel
- amount → Revenue amount (purchase events only)

Note:
Funnel analysis is based on distinct users per stage.
Revenue metrics use `amount` from purchase events.
