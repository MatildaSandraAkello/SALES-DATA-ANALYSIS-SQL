# SALES DATA ANALYSIS
## TABLE OF CONTENTS
- [PROJECT OVERVIEW](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [EXPLORATORY DATA ANALYSIS (EDA)](#exploratory-data-analysis)
- [DATA ANALYSIS](#data-analysis)
- [FINDINGS](#findings)
- [RECOMMENDATIONS](#recommendations)
## PROJECT OVERVIEW
![Picture1](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/9b987a93-1df2-4ba8-8a33-b59e0013606f)

**Purpose:** To Analyze sales data and identify trends, top-selling products, and revenue metrics for business decision-making.

**Description:** In this project, I will dive into a large sales dataset to extract valuable insights. I’ll explore sales trends over time, identify the best-selling products, calculate revenue metrics such as total sales and profit margins, and create visualizations to present my findings effectively. This project showcases my ability to manipulate and derive insights from large datasets, enabling me to make data-driven recommendations for optimizing sales strategies.

## Data Source
The "sales_data.csv" dataset was provided as part of the MeriSkill Interniship requirement. The dataset contains detailed sales information made by a company.

## Tools
- SQL - Data Analysis
- PowerBi - Data Visualization (Dashboard) [Click to View](https://app.powerbi.com/view?r=eyJrIjoiYzRhMTkzMTctYjZmNS00ZWU5LWJjMDQtODU0YmU5MTBlOTU4IiwidCI6ImZhMTBkMTMyLWI3NzktNGVjMy1iZTgzLTc3N2QxYWQ1ODVhYiJ9)

## EXPLORATORY DATA ANALYSIS
1. What is the Total Profit?
2. What is the Total Sales Quantity?
3. What is the Profit Margin?
4. What do the Monthly Sales Trend look like?
5. What do the Weekly Sales Trend look like?
6. What are the Top 5 best-selling product?
7. What are the Top 5 worst performing products?
8. What do the Sales look like, by City?

## DATA ANALYSIS
1. Total Profit – This is the sum of Net Profit from all Sales Transactions.
```sql
SELECT SUM(Sales) AS Total_Profit
FROM [Sales Data]
```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/65bcc256-f3f8-4ddf-bf64-0fcc87078d9c)

2. Sales Quantity – This is the Total Units Sold.
``` sql
SELECT SUM(Quantity_Ordered) AS Sales_Qty
FROM [Sales Data]
```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/0153ad42-bf73-4e31-a04e-a247ba88771f)

3. Profit Margin – This is the ratio of net profit to total revenue expressed as a percentage.
```sql
SELECT (((SUM(Sales)) - (SUM(Price_Each))) / SUM(Sales))*100 AS Profit_Margin
FROM [Sales Data]
```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/508fd9e0-c9bc-47a6-8034-ef28e9dac5c6)

4. Monthly Sales Trend
```sql
SELECT DATENAME(MONTH, Order_Date) AS Month_Name, 
SUM(Sales) AS Total_Sales
FROM [Sales Data]
GROUP BY DATENAME(MONTH, order_date)
```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/7b26e464-261d-4972-9a25-4a19635914de)

5. Weekly Sales Trend
``` sql
SELECT DATENAME(DW, Order_Date) AS Day_Name, 
SUM(Sales) AS Total_Sales
FROM [Sales Data]
GROUP BY DATENAME(DW, order_date)
 ```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/3f11967b-00f7-4104-94ef-7e0b4733808f)

6. Top 5 best-selling product
``` sql
SELECT TOP 5 Product, SUM(Sales) AS Total_Sales
FROM [Sales Data]
GROUP BY Product
ORDER BY Total_Sales DESC
```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/953c7742-11b1-448f-b098-6ee35091dc7c)

7. Top 5 worst performing products
``` sql
SELECT TOP 5 Product, SUM(Sales) AS Total_Sales
FROM [Sales Data]
GROUP BY Product
ORDER BY Total_Sales ASC
```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/44def466-c3d2-4995-b9a0-45c6dd0bdd11)

8. Sales by City
``` sql
SELECT City, SUM(Sales) AS Total_Sales
FROM [Sales Data]
GROUP BY City
```
![image](https://github.com/MatildaSandraAkello/SALES-DATA-ANALYSIS-SQL/assets/146660748/15c1d4fb-f242-401f-a66c-3e7089bdb314)

## FINDINGS
- December is when the sales peaked seeing as it's a festive season.
- Over the months, Tuesday is the highest revenue generating day of the week.
- The 2 best performing products are Macbook Pro Laptops and Iphones.
- The 2 worst performing products are the Lightning Charging Cables and USB-C Charging Cables.

## RECOMMENDATIONS
1. Management should invest in marketing especially during the festive seasons so as to maximize revenue.
2. Management should also invest in running promotions on Tuesdays inorder to maximize sales and also promote slow selling products.
3. Management should consider pairing up items that are slow selling, with those that are fast selling as a strategy to encourage increased sales.


