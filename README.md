# [SQL] Business Insights on Sales Performance - Retail Supply Chain Domain

<img width="1200" height="627" alt="image" src="https://github.com/user-attachments/assets/4015d733-4588-4023-9c02-c08b1e297e01" />

## Table of Contents
I. [📌 Introduction](#I.-Introduction)

II. [📂 Dataset](#II.-Dataset)

III. [🧠 Main Process](#III.-Main-Process)

IV. [📊 Exploring the Dataset](#IV.-Exploring-the-Dataset)

V. [🔎 Final Conclusion](#V.-Conclusion)

## I. Introduction
🎉 Overview:

The project investigates global sales performance by analyzing transactional data. It covers metrics such as total cost, revenue, and profit by region and item type, identifies top-performing countries and products, and examines delivery efficiency across different markets.

🏹 Objective:

The primary goal is to extract actionable insights from sales data to answer specific business questions, including:

✔️ Which regions and product categories are most profitable?

✔️ Which countries lead in online sales orders and profit generation?

✔️ How do delivery times vary across regions and years?

✔️ Which products contribute the most profit in seasonal contexts?

👤 Who is this project for?

✔️ Sales & Marketing Teams

✔️ Supply Chain & Inventory Managers

✔️ Business Analysts & Decision-makers

## II. Dataset

The dataset comes from two original sheets merged into one consolidated table.

* Columns include:

  - Order ID, Order Priority, Order Date, Ship Date

  - Item Type, Units Sold, Price, Cost, Sales Channel

  - Country, Region

* The dataset captures multi-regional transactions across different sales channels (online and offline) and product categories (e.g., Beverages, Clothing, Cosmetics, etc.).

## III. Main Process

1️⃣ Data Preparation
* Merge the Orders and Regions sheets into a single dataset with an added Region column for each country.

2️⃣ Business Question Analysis with SQL in BigQuery
* Calculate total cost, revenue, and profit by both region and item type.
* Count the number of beverage orders in 2011.
* Identify for each item type the country with the highest profit.
* Find the region with the longest average delivery time in 2016 using DENSE_RANK().
* Determine which item type contributes the most profit in January using DENSE_RANK().
* Compute the total profit of the top 5 countries ranked by online channel orders.

3️⃣ Ranking & Comparative Insights
* Apply SQL ranking functions (DENSE_RANK) to highlight leaders in profit and performance.
* Compare countries and regions across multiple dimensions (profit, delivery time, sales channel).

## IV. Exploring the Dataset
### Query 01: Total cost, revenue and profit by both region and item type?

We start by calculating the main financial metrics grouped by both region and item type.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:cfa406542a4b41eba93f80237f3672c3)
* SQL code

<img width="900" height="234" alt="image" src="https://github.com/user-attachments/assets/e5e23c06-c25e-4f87-8ef5-1dd4d10e40c1" />

* Query results

<img width="900" height="545" alt="image" src="https://github.com/user-attachments/assets/bf829b38-d72b-44dd-9b61-b620aa40a18a" />

Insight: This query highlights which product categories generate the most profit in each region.

### Query 02: How many orders of Beverages are there in 2011?

We filter orders for beverages in the year 2011 and count them.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:0a6a974416f34cf38e1038393b32dbad)
* SQL code

<img width="900" height="151" alt="image" src="https://github.com/user-attachments/assets/caf3c6e7-f291-422d-a817-ff528101f512" />

* Query results

<img width="900" height="333" alt="image" src="https://github.com/user-attachments/assets/b16160ed-8650-46a1-98ac-54173b7c3879" />

Insight: This gives us the demand size for beverages in a specific year.

### Query 03: For each item type, what is the country which gains the max profit?

We use a CTE with ranking to find the top-profit country for each item type.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:49d756a653c84b389366b489d212c1b4)
* SQL code

<img width="900" height="501" alt="image" src="https://github.com/user-attachments/assets/3103c588-444c-485c-aecc-1470257803c9" />

* Query results

<img width="900" height="529" alt="image" src="https://github.com/user-attachments/assets/d5a5e1d2-21ca-4c81-b102-efeca6f3d412" />

Insight: Identifies which country dominates profit for each product line.

### Query 04: Which region has longest average delivery time in 2016? How long?

We calculate delivery time and use DENSE_RANK() to find the region with the highest average.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:8297014946ab4527b42d3128ee4be9a9)
* SQL code

<img width="900" height="426" alt="image" src="https://github.com/user-attachments/assets/e9b780bc-674f-46ec-905b-3c432f9e8eac" />

* Query results

<img width="900" height="283" alt="image" src="https://github.com/user-attachments/assets/f22ed6ce-c6e7-48b0-8c5a-3324fb9e9304" />

Insight: Helps identify logistical challenges in certain regions.

### Query 05: Which item type contributes most profit in Jan?

We calculate profit for January across all years and rank results with DENSE_RANK().

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:80f22b804d7f4f7eb528e3a712c5b459)
* SQL code

<img width="900" height="444" alt="image" src="https://github.com/user-attachments/assets/5e80d459-70a3-4ccc-a817-fedf8944314d" />

* Query results

<img width="900" height="331" alt="image" src="https://github.com/user-attachments/assets/c5a437a0-ee48-4ee8-b9f8-5ff43b917ad7" />

Insight: Shows which products are most profitable in the first month of the year, useful for seasonal sales planning.

### Query 06: What is total profit of top 5 countries which are sorted by Online channel orders?

We rank countries by the number of online orders and sum the profits of the top 5.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:3f85d25bd5d64feaaa20fd04c6cffc84)
* SQL code

<img width="900" height="484" alt="image" src="https://github.com/user-attachments/assets/372df065-c614-4b20-ac54-60cf42382fb6" />

* Query results

<img width="900" height="284" alt="image" src="https://github.com/user-attachments/assets/efefe4db-f374-4f31-a434-02506e3b1119" />

Insight: Reveals the collective contribution of the top 5 most active online countries to total profit.

## V. Conclusion

This project demonstrates how SQL and BigQuery can be applied to answer real-world business questions in retail and supply chain analytics. By systematically analyzing cost, revenue, profit, order patterns, and delivery performance, the project delivers insights that support strategic decision-making. It highlights the value of using ranking and aggregation techniques to identify top performers, seasonal patterns, and operational inefficiencies.

The findings can be extended further by integrating visualization tools (e.g., Power BI, Tableau) to present dashboards for business stakeholders. Ultimately, this project serves as a practical case study of data-driven decision-making using SQL in a retail and supply chain domain.


