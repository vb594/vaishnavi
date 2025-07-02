# # 📊 Superstore Power BI Analysis

A data visualization project built using Power BI to analyze and gain insights from Superstore sales data. The dashboard focuses on key business metrics, product performance, and regional trends to help stakeholders make informed decisions.

---

## 📁 Project Overview

This Power BI report showcases:

- 📈 **Sales**, **Profit**, and **% Returned Orders** with **Year-over-Year (YoY)** comparisons
- 🧾 Sales performance trends over time
- 💰 Most **profitable** and **loss-making** products
- 🗺️ Regions/states contributing the most to profit
- 👥 Segment-wise sales distribution

---

## 🛠 Tools & Technologies

- **Power BI Desktop**
- **DAX (Data Analysis Expressions)**
- Data modeling & transformation
- Conditional formatting
- Visual storytelling techniques

---

## 🧱 Dataset Details

- **Orders Table** – Includes product, region, sales, and profit data
- **Returns Table** – Contains returned `Order IDs`

---

## 🧰 Key Steps in the Project

### 🔹 Data Preparation
- Loaded and transformed `Orders` and `Returns` tables
- Removed returned orders by joining on `Order ID`
- Filtered unnecessary columns for a clean model

### 🔹 Data Modeling
- Created and marked a custom **Date Table**
- Built relationships:
  - `Order ID` (Orders ↔ Returns)
  - `Date` (Date Table ↔ Orders[Order Date])

### 🔹 DAX Measures

Defined key KPIs and comparisons:

DAX
Sales = SUM(Orders[Sales])
Profit = SUM(Orders[Profit])

% Returned Orders = 
VAR _total_orders = DISTINCTCOUNT(Orders[Order ID])
VAR _returned_orders = DISTINCTCOUNT(Returns[Order ID])
RETURN DIVIDE(_returned_orders, _total_orders)

Sales PY = CALCULATE([Sales], SAMEPERIODLASTYEAR('Date Table'[Date]))
Profit PY = CALCULATE([Profit], SAMEPERIODLASTYEAR('Date Table'[Date]))
Sales vs PY = [Sales] - [Sales PY]
