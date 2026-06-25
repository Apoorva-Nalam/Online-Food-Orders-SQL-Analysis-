# Online-Food-Orders-SQL-Analysis

## Overview
This project analyzes online Food orders data using MySQL to identify sales trends, customer behavior, and product performance.

## Skills Used
- SQL
- Joins
- Aggregate Functions
- Group By
- Subqueries
- CTE
- Data Analysis

## Tools
- MySQL Workbench
- MySQL

## Key Questions Answered
1.	Display all completed orders along with customer name and restaurant name.
   
'''sql
SELECT C.Customer_Id,  C.customer_name, R.restaurant_name ,O.Order_Status
FROM customers C JOIN orders O 
ON C.Customer_Id = O.Customer_Id
JOIN restaurants R 
ON O.Restaurant_Id = R.Restaurant_Id
WHERE Order_Status = "Completed";
'''
```sql
CREATE DATABASE p1_retail_db;

CREATE TABLE retail_sales
(
    transactions_id INT PRIMARY KEY,
    sale_date DATE,	
    sale_time TIME,
    customer_id INT,	
    gender VARCHAR(10),
    age INT,
    category VARCHAR(35),
    quantity INT,
    price_per_unit FLOAT,	
    cogs FLOAT,
    total_sale FLOAT
);
```
- Which customers placed the most orders?
- Monthly order trends
- Category-wise performance


