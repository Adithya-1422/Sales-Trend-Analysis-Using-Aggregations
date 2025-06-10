# Sales-Trend-Analysis-Using-Aggregations

## Project Overview

This project was completed as part of Task 6 in the Data Analyst Internship Program. The goal was to perform sales trend analysis using SQL by calculating monthly revenue and monthly order volume from a sales dataset. The dataset used (`sales_sample_v2.csv`) contains transaction-level data such as order ID, product ID, order date, and revenue amount.

The project demonstrates SQL skills including data grouping, aggregation, date formatting, and sorting — all essential for real-world business data analysis.

---

## Tools Used

- SQLite (via DB Browser for SQLite)
- SQL (SQLite dialect)
- sales_sample_v2.csv (provided dataset)
- Notepad++ / VS Code (to save SQL queries)
- Snipping Tool (for screenshots)

---

## Dataset Description

- **File Name**: `sales_sample_v2.csv`
- **Total Rows**: 20
- **Columns**:
  - `order_id`: Unique order identifier
  - `product_id`: ID of the product sold
  - `order_date`: Date when the order was placed
  - `amount`: Total amount paid for the order

---

## SQL Tasks Performed

1. **Monthly Revenue and Order Volume**
   - Used `strftime('%Y', order_date)` and `strftime('%m', order_date)` to extract year and month
   - Applied `SUM(amount)` to calculate monthly revenue
   - Applied `COUNT(DISTINCT order_id)` to calculate total orders per month

2. **Top 3 Revenue Months**
   - Grouped by year and month
   - Ordered by `SUM(amount)` descending
   - Limited to 3 records using `LIMIT 3`

3. **Product Performance (optional)**
   - Grouped data by `product_id` to calculate total revenue and order count per product

---

## Sample SQL Query

```sql
SELECT 
  strftime('%Y', "order_date") AS year,
  strftime('%m', "order_date") AS month,
  SUM("amount") AS monthly_revenue,
  COUNT(DISTINCT "order_id") AS total_orders
FROM online_sales
GROUP BY year, month
ORDER BY year, month;
