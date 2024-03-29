---
layout: default
title: SQL Basic
parent: SQL
nav_order: 4
---

# 1 - Basic Clause
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

   Window functions are powerful tools in SQL that allow you to perform calculations across a set of rows that are somehow related to the current row. These functions can be incredibly useful for analytics and data processing tasks. Here are some of the most common window functions in SQL:

   1. **ROW_NUMBER()**: Assigns a unique sequential integer to rows within a partition of a result    set, starting at 1 for the first row in each partition.
   
   2. **RANK()**: Assigns a rank to each row within a partition of a result set, with gaps in the  ranking for tied rows.
   
   3. **DENSE_RANK()**: Similar to `RANK()`, but without gaps in the ranking for tied rows.  Consecutive rank values are assigned in the event of ties.
   
   4. **NTILE(n)**: Divides the rows in an ordered partition into `n` approximately equal groups.  `NTILE` assigns a bucket number to each row for grouping purposes.
   
   5. **LEAD(value, [offset], [default])**: Returns the value of the specified column in a row that   is a certain number of rows after the current row within the partition. If there is no such row,  an optional default value can be returned.
   
   6. **LAG(value, [offset], [default])**: Similar to `LEAD()`, but returns the value of the    specified column in a row that is a certain number of rows before the current row within the    partition.
   
   7. **FIRST_VALUE(column)**: Returns the first value in an ordered set of values in the window   frame.
   
   8. **LAST_VALUE(column)**: Returns the last value in an ordered set of values in the window frame.    Note that proper use of `LAST_VALUE` may require specific frame specification due to its default   window frame behavior.
   
   9. **SUM(column)**: Calculates the sum of the specified column for each row in the window frame.
   
   10. **AVG(column)**: Calculates the average of the specified column for each row in the window  frame.
   
   11. **MIN(column)**: Finds the minimum value of the specified column for each row in the window    frame.
   
   12. **MAX(column)**: Finds the maximum value of the specified column for each row in the window    frame.
   
   13. **COUNT(column)**: Counts the rows in the window frame. If a specific column is provided, it   counts the non-NULL values in that column.
   
   These window functions can be used with the `OVER()` clause, which defines how the rows are  partitioned and ordered for the calculation. The `OVER()` clause can include `PARTITION BY` to   divide the result set into partitions where the window function is applied, and `ORDER BY` to  specify the order within each partition.
   - **Example #1**: Rank users based on their scores.
     ```sql
     SELECT name, score, RANK() OVER (ORDER BY score DESC)
     FROM users;
     ```
     The `PARTITION BY` clause is commonly used in conjunction with window functions to divide the result set into partitions and perform calculations across these partitions. This approach allows you to apply a window function to each partition independently.

   - **Example #2**: Employee Salaries by Department

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
        - `RANK() OVER (...)`: This is the window function used to rank the employees. The        `RANK()` function assigns a unique rank to each row within a partition, with gaps       in the rank values if there are ties.
        - `PARTITION BY department`: This clause divides the employees into partitions        based on their department. The window function (in this case, `RANK()`) is applied        to each partition separately.
        - `ORDER BY salary DESC`: Within each department partition, employees are ordered         by their salary in descending order for the ranking calculation.

        **Result**: The result will be a list of all employees, along with their        department and salary, and a `salary_rank` that indicates their rank within their       department based on salary.

        This query effectively demonstrates how `PARTITION BY` is used with a window        function to perform calculations that are scoped to a subset of the data, allowing        for more nuanced and useful analyses.

8. **Data Types and Conversion**:
   - **Example**: Convert a string to a date.
     ```sql
     SELECT CAST('2023-01-01' AS DATE);
     ```

9.  **Handling NULLs and Data Cleaning Techniques**:
   - **Example**: Coalesce function to replace NULLs.
     ```sql
     SELECT COALESCE(column_name, 'default_value') FROM table;
     ```

10.  **With Clause and CTE**:
    
      The `WITH` clause is used to define a Common Table Expression (CTE), which is a       temporary result set that you can reference within a SELECT, INSERT, UPDATE, or       DELETE statement. A CTE can be thought of as a way to create a temporary result       set that is defined within the execution scope of a single statement and can be       referred to later within that statement.

      CTEs are particularly useful for organizing complex queries, making them more       readable and maintainable by breaking down the query into simpler parts. They are       also helpful in recursive queries, where you need to perform a query based on the       result of a previous query.

      ### Example: Employee Management System

      **Scenario**: Suppose you have an `employees` table with the following columns:       `employee_id`, `name`, `manager_id`, and `salary`. You want to find the average       salary of employees under each manager.

      **Table: Employees**

      - `employee_id` (integer)
      - `name` (varchar)
      - `manager_id` (integer, references `employee_id` indicating the manager of this      employee)
      - `salary` (numeric)

      **Objective**: Use a CTE to organize the query that calculates the average salary       for employees under each manager.

      **SQL Query with CTE**:
      ```sql
      WITH ManagerSalaries AS (
        SELECT manager_id, AVG(salary) AS avg_salary
        FROM employees
        GROUP BY manager_id
      )
      SELECT e.name AS manager_name, ms.avg_salary
      FROM ManagerSalaries ms
      JOIN employees e ON ms.manager_id = e.employee_id;
      ```

11. **CASE clause**
    The `CASE` clause in SQL is a versatile conditional expression that allows you to perform if-then-else type logic directly within your SQL queries. It's useful for transforming data based on certain conditions, implementing conditional aggregation, and more.

   **Scenario**: You have an `employees` table with columns for `employee_id`, `name`, `department`,  and `performance_score`. The `performance_score` is an integer that rates the employee's   performance.

   **Table: Employees**

   - `employee_id` (integer)
   - `name` (varchar)
   - `department` (varchar)
   - `performance_score` (integer)

   **Objective**: Use the `CASE` clause to categorize employees into 'Excellent', 'Good', 'Average',  'Below Average', based on their `performance_score`.

   **SQL Query with CASE Clause**:
   ```sql
   SELECT employee_id,
          name,
          department,
          performance_score,
          CASE 
              WHEN performance_score >= 90 THEN 'Excellent'
              WHEN performance_score >= 75 AND performance_score < 90 THEN 'Good'
              WHEN performance_score >= 60 AND performance_score < 75 THEN 'Average'
              ELSE 'Below Average'
          END AS performance_category
   FROM employees;
   ```

   **Explanation**:

   - The `CASE` clause evaluates the `performance_score` for each employee.
   - Based on the score, it assigns a `performance_category`:
       - Scores 90 and above are categorized as 'Excellent'.
       - Scores between 75 (inclusive) and 90 (exclusive) are 'Good'.
       - Scores between 60 (inclusive) and 75 (exclusive) are 'Average'.
       - Scores below 60 are categorized as 'Below Average'.
   - The result is a list of employees along with their `performance_category` based on their   `performance_score`.

   This example illustrates how the `CASE` clause can be used to analyze and categorize data directly    within an SQL query, providing a powerful tool for data transformation and insight generation   without the need for additional processing outside the database.

12.  **Optimization and Performance**:
    - **Example**: Use indexes to improve query performance.
      ```sql
      CREATE INDEX idx_column ON table(column_name);
      ```

13.  **Database-specific Features** (depending on the SQL database being used, e.g., MySQL, PostgreSQL):
    - **Example**: PostgreSQL's JSON functions.
      ```sql
      SELECT data->>'key' FROM json_table;
      ```

  Make sure you understand the concepts behind each example and can modify or write   similar queries based on different scenarios. Practice is key in mastering SQL for  data science interviews.

# 2 - Examples cover the above topic

Here are two SQL test examples that collectively cover points 1 to 9. These examples will include various aspects of SQL queries relevant to a data scientist's role.

### Example 1: Customer Orders Analysis
This example will cover points 1 to 5 (Basic SQL Syntax, Aggregation Functions, Join Operations, Subqueries, and Group By & Having Clauses).

**Scenario**: You have two tables: `customers` and `orders`. The `customers` table has columns `id`, `name`, and `age`, while the `orders` table has `order_id`, `customer_id`, and `order_date`.

**Task**:
1. List all customers.
2. Calculate the average age of customers.
3. Show each customer's latest order date.
4. Find customers who have placed more than 3 orders.

**SQL Queries**:
1. List all customers:
   ```sql
   SELECT * FROM customers;
   ```
2. Average age of customers:
   ```sql
   SELECT AVG(age) FROM customers;
   ```
3. Each customer's latest order date:
   ```sql
   SELECT customers.name, MAX(orders.order_date) as latest_order
   FROM customers
   JOIN orders ON customers.id = orders.customer_id
   GROUP BY customers.name;
   ```
4. Customers with more than 3 orders:
   ```sql
   SELECT customers.name
   FROM customers
   JOIN orders ON customers.id = orders.customer_id
   GROUP BY customers.name
   HAVING COUNT(orders.order_id) > 3;
   ```

### Example 2: Product Sales Analysis
This example will cover points 6 to 9 (Set Operations, Window Functions, Data Types and Conversion, Handling NULLs).

**Scenario**: You have two tables: `products` and `sales`. The `products` table has columns `product_id`, `product_name`, and `price`, while the `sales` table has `sale_id`, `product_id`, `sale_date`, and `quantity`.

**Task**:
1. Find products that had sales in both 2022 and 2023.
2. Rank products based on the total quantity sold.
3. Convert `sale_date` from string to date format.
4. Show total sales quantity, replacing NULL with 0.

**SQL Queries**:
1. Products with sales in both 2022 and 2023:
   ```sql
   SELECT product_name 
   FROM products 
   WHERE product_id IN (
       SELECT product_id FROM sales WHERE YEAR(sale_date) = 2022
       INTERSECT
       SELECT product_id FROM sales WHERE YEAR(sale_date) = 2023
   );
   ```
2. Rank products by total quantity sold:
   ```sql
   SELECT product_name, SUM(quantity) as total_sold,
          RANK() OVER (ORDER BY SUM(quantity) DESC) as sales_rank
   FROM products
   JOIN sales ON products.product_id = sales.product_id
   GROUP BY product_name;
   ```
3. Convert `sale_date` to date format:
   ```sql
   SELECT sale_id, CAST(sale_date AS DATE) as sale_date_formatted
   FROM sales;
   ```
4. Total sales quantity, NULL as 0:
   ```sql
   SELECT product_id, COALESCE(SUM(quantity), 0) as total_quantity
   FROM sales
   GROUP BY product_id;
   ```
### Example 3: Fill Null with partition average


   ```sql
   WITH DepartmentSalaryAverage AS (
       SELECT 
           department, 
           AVG(salary) AS avg_salary
       FROM 
           your_table_name
       GROUP BY 
           department
   )
   SELECT 
       t.department, 
       COALESCE(t.salary, dsa.avg_salary) AS salary
   FROM 
       your_table_name t
   LEFT JOIN 
       DepartmentSalaryAverage dsa ON t.department = dsa.department;
   ```
   
   This code snippet uses a CTE (`WITH` clause) to calculate the average salary for each department   first. Then, it selects the department and salary from the original table, using `LEFT JOIN` to   include the average salary calculated in the CTE. `COALESCE` is used to substitute any `NULL`  salary with the average salary for the respective department. This approach ensures that every row  has a salary value, either the actual salary or the department's average salary if the original  salary is `NULL`.


These examples provide a comprehensive test covering a wide range of SQL skills relevant to data science. Practicing these scenarios will help you prepare effectively for your SQL interview.