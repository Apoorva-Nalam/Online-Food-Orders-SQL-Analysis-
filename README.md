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
   
```sql
SELECT C.Customer_Id,  C.customer_name, R.restaurant_name ,O.Order_Status
FROM customers C JOIN orders O 
ON C.Customer_Id = O.Customer_Id
JOIN restaurants R 
ON O.Restaurant_Id = R.Restaurant_Id
WHERE Order_Status = "Completed";
```

2.	Display restaurants whose average order value is greater than the overall average order value. 
```sql
SELECT R.restaurant_name , COUNT(O.order_id) AS above_avg_orders
FROM restaurants R JOIN orders O 
ON R.Restaurant_Id = O.Restaurant_Id
GROUP BY R.Restaurant_Name
HAVING COUNT(Order_Id ) > 
( 
		SELECT AVG(avg_count) FROM 
		(  SELECT COUNT(order_id) AS avg_count 
		FROM orders
        GROUP BY Restaurant_id
		) temp
);

3. Calculate month-wise revenue and show the previous month revenue.
   
```sql
SELECT month_no, revenue,
       LAG(revenue) OVER(ORDER BY month_no) AS previous_month_revenue
       FROM ( SELECT MONTH(order_date) AS month_no,
			  SUM(order_amount) AS revenue
              FROM orders
              GROUP BY MONTH(order_date)
			) temp;
```





