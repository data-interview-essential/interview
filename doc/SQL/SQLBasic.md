---
layout: default
title: SQL Basic
parent: python
nav_order: 4
---

Preparing for a SQL interview as a data scientist involves focusing on several key areas. Here are the essentials, along with examples for each:

1. **Basic SQL Syntax and Queries**:
   - **Example**: Retrieve all records from a table. 
     ```sql
     SELECT * FROM customers;
     ```

2. **Aggregation Functions**:
   - **Example**: Calculate the average age of users.
     ```sql
     SELECT AVG(age) FROM users;
     ```

3. **Join Operations**:
   - **Example**: Combine data from two tables, like orders and customers.
     ```sql
     SELECT customers.name, orders.order_date
     FROM customers
     JOIN orders ON customers.id = orders.customer_id;
     ```

4. **Subqueries and Nested Queries**:
   - **Example**: Find products that are above average price.
     ```sql
     SELECT product_name FROM products
     WHERE price > (SELECT AVG(price) FROM products);
     ```

5. **Group By and Having Clauses**:
   - **Example**: List the number of orders for each customer, only include those with more than 5 orders.
     ```sql
     SELECT customer_id, COUNT(*)
     FROM orders
     GROUP BY customer_id
     HAVING COUNT(*) > 5;
     ```

6. **Set Operations (UNION, INTERSECT, EXCEPT)**:
   - **Example**: Find names that appear in both table1 and table2.
     ```sql
     SELECT name FROM table1
     INTERSECT
     SELECT name FROM table2;
     ```

7. **Window Functions**:
   - **Example**: Rank users based on their scores.
     ```sql
     SELECT name, score, RANK() OVER (ORDER BY score DESC)
     FROM users;
     ```
     The `PARTITION BY` clause is commonly used in conjunction with window functions to divide the result set into partitions and perform calculations across these partitions. This approach allows you to apply a window function to each partition independently.

   - **Example**: Employee Salaries by Department

**Scenario**: Imagine you have an `employees` table with columns for `employee_id`, `department`, and `salary`. You want to calculate the rank of each employee within their department based on their salary.

**Table: Employees**
- `employee_id`
- `department`
- `salary`

**Task**: Rank employees within each department by their salary in descending order.

**SQL Query**:
```sql
SELECT employee_id,
       department,
       salary,
       RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS salary_rank
FROM employees;
```

**Explanation**:
- `RANK() OVER (...)`: This is the window function used to rank the employees. The `RANK()` function assigns a unique rank to each row within a partition, with gaps in the rank values if there are ties.
- `PARTITION BY department`: This clause divides the employees into partitions based on their department. The window function (in this case, `RANK()`) is applied to each partition separately.
- `ORDER BY salary DESC`: Within each department partition, employees are ordered by their salary in descending order for the ranking calculation.

**Result**: The result will be a list of all employees, along with their department and salary, and a `salary_rank` that indicates their rank within their department based on salary.

This query effectively demonstrates how `PARTITION BY` is used with a window function to perform calculations that are scoped to a subset of the data, allowing for more nuanced and useful analyses.

8. **Data Types and Conversion**:
   - **Example**: Convert a string to a date.
     ```sql
     SELECT CAST('2023-01-01' AS DATE);
     ```

9. **Handling NULLs and Data Cleaning Techniques**:
   - **Example**: Coalesce function to replace NULLs.
     ```sql
     SELECT COALESCE(column_name, 'default_value') FROM table;
     ```

10. **Optimization and Performance**:
    - **Example**: Use indexes to improve query performance.
      ```sql
      CREATE INDEX idx_column ON table(column_name);
      ```

11. **Database-specific Features** (depending on the SQL database being used, e.g., MySQL, PostgreSQL):
    - **Example**: PostgreSQL's JSON functions.
      ```sql
      SELECT data->>'key' FROM json_table;
      ```

Make sure you understand the concepts behind each example and can modify or write similar queries based on different scenarios. Practice is key in mastering SQL for data science interviews.