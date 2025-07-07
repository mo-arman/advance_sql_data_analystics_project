# 📊 Advanced Data Analytics Project – Product Performance Report (SQL-Based)

## 🧠 Project Summary

This project is part of an **Advanced SQL Data Analytics pipeline**, designed to extract deep insights from raw transactional data and transform it into a **gold-layer analytical report** focused on **Product Performance**. The report is built as a reusable and scalable **SQL View** within a **star-schema data warehouse**, serving as a core data asset for BI tools, data analysts, and decision-makers.

---

## 🎯 Purpose

- Convert complex raw data into **actionable product-level KPIs**.
- Segment products based on **sales performance and engagement**.
- Enable **cross-functional use** for business teams in sales, inventory, and marketing.
- Lay the foundation for **automated reporting and dashboards**.

---

## 🏗️ Architecture

- **Layer:** Gold (Reporting Layer)
- **Data Model:** Star Schema
- **Tools:** Microsoft SQL Server / Azure SQL Data Warehouse  
- **View Name:** `gold.report_products`

### 🔗 Tables Used:

- `gold.fact_sales` – core sales transactions
- `gold.dim_products` – product metadata (name, category, etc.)
- `gold.dim_customers` – customer dimension to calculate engagement

---

## 📐 Metrics Engineered

| KPI                      | Description |
|--------------------------|-------------|
| `total_orders`           | Count of unique orders for the product |
| `total_sales`            | Gross revenue from the product |
| `total_quantity`         | Total units sold |
| `unique_customers`       | Distinct customers who purchased the product |
| `active_months`          | Lifespan of the product in months (first to last sale) |
| `avg_selling_price`      | Total Sales ÷ Quantity Sold |
| `revenue_per_customer`   | Total Sales ÷ Unique Customers |
| `monthly_velocity`       | Total Sales ÷ Active Months |

---

## 🧠 Product Segmentation Logic

Products are classified into performance tiers based on sales volume:

```sql
CASE
  WHEN total_sales >= 10000 THEN 'Best Seller'
  WHEN total_sales BETWEEN 3000 AND 9999 THEN 'Average Performer'
  ELSE 'Low Performer'
END
