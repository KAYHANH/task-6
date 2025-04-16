# 📊 Task 6: Sales Trend Analysis Using Aggregations

## 📝 Objective
Analyze **monthly revenue** and **order volume** from the `orders` table in the `online_sales` database using SQL aggregation functions.

---

## 🧰 Tools & Technologies
- **Database**: MySQL  
- **Tool**: MySQL Workbench (or any SQL IDE)

---

## 🗃️ Dataset
**Table:** `online_sales.orders`  
**Relevant Columns:**
- `order_id` – Unique identifier for each order
- `order_date` – Date of the order
- `amount` – Total revenue of the order
- `product_id` – Product reference (not used in this analysis)

---

## 📌 Requirements
- Extract month and year from `order_date`
- Calculate:
  - **Total Revenue** → `SUM(amount)`
  - **Order Volume** → `COUNT(DISTINCT order_id)`
- Group results by year and month
- Sort results in chronological order
- (Optional) Filter results for a specific time period

---

## 📄 SQL Script

```sql
-- Task 6: Sales Trend Analysis Using Aggregations (MySQL)

SELECT
    EXTRACT(YEAR FROM order_date) AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS order_volume
FROM
    online_sales.orders
WHERE
    order_date BETWEEN '2023-01-01' AND '2023-12-31'
GROUP BY
    EXTRACT(YEAR FROM order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY
    order_year ASC,
    order_month ASC;
