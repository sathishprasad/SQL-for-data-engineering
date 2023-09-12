# Table Creation and Exploration
```sql
-- Creating a DATABASE
CREATE DATABASE sathish_sales

-- Creating a new table
CREATE TABLE sales (
  id INT,
  sale_date DATE,
  product VARCHAR(50),
  quantity INT,
  revenue DECIMAL(10,2)
);

-- Inserting Data into the table
INSERT INTO sales (id, sale_date, product, quantity, revenue)
VALUES
  (1, '2021-01-01', 'Product A', 10, 100.00),
  (2, '2021-01-02', 'Product B', 5, 50.00),
  (3, '2021-01-03', 'Product C', 15, 150.00),
  (4, '2021-01-04', 'Product A', 8, 80.00),
  (5, '2021-01-05', 'Product B', 12, 120.00),
  (6, '2021-01-06', 'Product C', 20, 200.00),
  (7, '2021-01-07', 'Product A', 6, 60.00),
  (8, '2021-01-08', 'Product B', 18, 180.00),
  (9, '2021-01-09', 'Product C', 10, 100.00),
  (10, '2021-01-10', 'Product A', 4, 40.00);

```
---
```sql
--  Exploring the sales data
SELECT * 
FROM sales;
```
---
```sql
--Retrieve data only for a specific product, such as "Product A":
SELECT *
FROM SALES
WHERE product = 'Product A';
```
---
```sql
--Retrieve the total revenue for each day:
SELECT
	sale_date,
	SUM(revenue) As Total_Revenue
FROM sales
GROUP BY sale_date;
```
---
```sql
--Retrieve the total revenue for each product:
SELECT 
	product,
	SUM(revenue) As Total_Revenue
FROM sales
GROUP BY product
ORDER BY 2 DESC;
```
---
```sql
--Retrieve the top-selling products in descending order by quantity sold:
SELECT 
	product, 
	SUM(quantity) As Total_products_sold,
	AVG(revenue) As Average_product_price
FROM sales 
GROUP BY product 
ORDER BY 2 DESC;
```
---
# Test questions
- Which products were sold on January 2nd?
- What was the total revenue for Product C?  
- Which days had revenue greater than $150? 
- Which products had a total quantity sold greater than 30?
- What was the average revenue per sale for Product B? 
- Which products had a revenue per sale greater than $15?
## Solutions
```sql
-- 1.Which products were sold on January 2nd?
SELECT 
	product
FROM sales
WHERE     
	DATE_PART('month', sale_date) = 1
    AND DATE_PART('day', sale_date) = 2;
```
---
```sql
-- 2.What was the total revenue for Product C? 
SELECT
	product,
	SUM(revenue) As total_revenue
FROM sales
GROUP BY product
HAVING product = 'Product C';

--OR

SELECT
	product,
	SUM(revenue) As total_revenue
FROM sales
WHERE product = 'Product C'
GROUP BY product;
```
---
```sql
-- 3.Which days had revenue greater than $150?
SELECT 
	sale_date
FROM sales
WHERE revenue > 150;
```
---
```sql
-- 4. Which products had a total quantity sold greater than 30?
SELECT 
	product,
	SUM(quantity) AS Total_quantity_sold
FROM sales
GROUP BY product
HAVING SUM(quantity)>30;
```
---
```sql
-- 5. What was the average revenue per sale for Product B?
SELECT 
	AVG(revenue) as Avg_revenue_per_sale
FROM sales
WHERE product = 'Product B';
```
---
```sql
-- 6. Which products had a revenue per sale greater than $15?
SELECT
	product,
	AVG(revenue) as Avg_revenue_per_sale
FROM sales
GROUP BY product
HAVING AVG(revenue) > 15;
```
---
