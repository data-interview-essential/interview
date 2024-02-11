---
layout: default
title: SQL Q&A
parent: SQL
nav_order: 4
---


1. **What is a foreign key in SQL? What role does it play?**
   
   A foreign key is a field or multiple fields in one table that establishes a relationship with the primary key in another table. The table with the primary key is referred to as the parent or referenced table, while the one with the foreign key is the child table. Foreign keys are crucial for maintaining referential integrity in a relational database. They ensure that data in the child table corresponds to valid data in the parent table, preventing inconsistencies or orphaned records. Foreign keys are used to enforce data integrity and maintain the relationships between tables.

2. **Are blank spaces or zero values treated the same as NULL?**

   No, NULL is not equivalent to a zero or blank space. NULL represents the absence of a value or an unknown value in a database column. It is used when a value is unavailable, undefined, or not applicable. In contrast, zero and blank spaces are actual values and can be compared or used in calculations. NULL values cannot be directly compared to other NULL values using standard comparison operators; special NULL handling functions or IS NULL/IS NOT NULL clauses are used instead.

3. **What is meant by SQL injection? What would be the first step in preventing or mitigating an attack?**

   SQL injection is a type of security vulnerability where malicious SQL code is injected into user inputs or application queries to manipulate a database improperly. Attackers can gain unauthorized access, retrieve sensitive data, or even damage the database.

   The first step in preventing or mitigating SQL injection attacks is input validation and sanitization. Validate and sanitize user inputs to ensure they conform to the expected format and reject any inputs that appear suspicious or contain potentially harmful SQL code. Additionally, using parameterized queries or prepared statements in your SQL code can help protect against SQL injection by separating user inputs from the SQL code execution.

4. **What’s the difference between IN and BETWEEN operators?**

   Both IN and BETWEEN operators are used to filter data, but they have different purposes:
   
   - **BETWEEN:** It selects data within a specified range, including the range boundaries. For example, `BETWEEN 1 AND 5` would select values 1, 2, 3, 4, and 5.

   - **IN:** It allows you to specify a list of values and selects data that matches any value in that list. For instance, `IN (1, 3, 5)` would select rows with values 1, 3, or 5.

5. **What is a cursor in SQL?**

   In SQL, a cursor is a database object used to manage the result set of a query. Cursors are particularly useful when you need to work with individual rows in a result set, typically within a procedural language like PL/SQL. There are two main types of cursors:

   - **Implicit Cursors:** These are automatically allocated by the SQL server when you perform DML (Data Manipulation Language) operations like INSERT, UPDATE, or DELETE. You don't need to explicitly declare them.

   - **Explicit Cursors:** These are declared by the user in their SQL code. Explicit cursors are used when you need to control the fetching of rows from a result set, typically within a stored procedure or function.

6. **Explain what a trigger is in SQL. When would you use a trigger?**

   A trigger in SQL is a database object, typically a stored procedure, that is automatically executed when a specific event or action occurs in the database. These events can include INSERT, UPDATE, DELETE, or other data-related changes. Triggers are used to automate tasks or enforce specific rules or actions when certain conditions are met. Common use cases for triggers include:

   - **Auditing database activity:** Triggers can log changes made to a database for security or compliance purposes.

   - **Implementing business rules:** Triggers can enforce business logic or data validation rules.

   - **Enforcing referential integrity:** Triggers can be used to maintain relationships between tables and ensure that data remains consistent.

   Triggers are a powerful but potentially complex feature of SQL, and they should be used judiciously to avoid unintended consequences and performance issues.

7.  **Explain the difference between SQL's SELECT and INSERT statements.**

    - **SELECT:** The SELECT statement is used to retrieve data from one or more tables in a database. It returns a result set that matches specified criteria, and the original data remains unchanged.

    - **INSERT:** The INSERT statement is used to add new records (rows) into a table. It adds data to the specified table, creating new rows with the provided values.

8.  **What is a primary key in SQL, and why is it important?**

    A primary key is a column or a set of columns in a table that uniquely identifies each row within that table. It is essential because it enforces data integrity by ensuring that each row has a unique identifier, preventing duplicate or null values in the primary key column(s).

9.  **What is the difference between INNER JOIN and LEFT JOIN in SQL?**

    - **INNER JOIN:** An INNER JOIN returns only the rows that have matching values in both tables being joined. Rows with no matching values in either table are excluded from the result.

    - **LEFT JOIN (or LEFT OUTER JOIN):** A LEFT JOIN returns all rows from the left table and the matched rows from the right table. If there are no matches in the right table, NULL values are included for columns from the right table.

10. **Explain the concept of SQL indexing. Why is it used, and what are the advantages?**

    SQL indexing is the process of creating data structures (indexes) on one or more columns of a table to improve query performance. Indexes allow the database engine to quickly locate and retrieve specific rows based on the indexed columns. Advantages of indexing include faster data retrieval, improved query efficiency, and reduced I/O operations.

11. **What is a subquery in SQL, and how does it differ from a JOIN clause?**

    A subquery, also known as a nested query, is a query nested within another SQL statement, such as SELECT, INSERT, UPDATE, or DELETE. It is used to retrieve data that will be used as input for the outer query. Subqueries are enclosed in parentheses and typically return a single value or a result set.

    A JOIN clause, on the other hand, is used to combine rows from two or more tables based on a related column between them. JOINs are used to retrieve data from multiple tables simultaneously and return a combined result set.

12. **What is normalization in the context of relational databases? Why is it important?**

    Normalization is the process of organizing and structuring a relational database to minimize data redundancy and maintain data integrity. It involves dividing a database into multiple related tables and defining relationships between them. Normalization reduces data duplication, improves data consistency, and makes the database more efficient in terms of storage and maintenance.

13. **What is the difference between a stored procedure and a function in SQL?**

    - **Stored Procedure:** A stored procedure is a precompiled set of one or more SQL statements that can be executed with a single call. Stored procedures can perform actions, modify data, and return results. They may not return values directly but can use output parameters.

    - **Function:** A function is a reusable block of SQL code that returns a single value. Functions are primarily used to compute and return values based on input parameters. They always return a value and cannot perform actions or modify data directly.

These SQL interview questions cover fundamental SQL concepts, query optimization, and database design principles that are essential for SQL practitioners.

14. `PARTITION BY` and `GROUP BY` are both SQL operations that organize data into subsets for further analysis, but they serve different purposes and are used in different contexts. 

    Here's an overview of the key differences:

    ### PARTITION BY

    - **Context**: Used with window functions.
    - **Purpose**: Divides the result set into partitions to which the window function  is applied, but does not collapse these partitions into a single output row per  partition. Instead, it keeps the original rows and adds a new column with the    window function result for each row.
    - **Functionality**: Enables you to perform calculations over a set of rows that    are somehow related to the current row while still returning the full dataset.     Common window functions include `ROW_NUMBER()`, `RANK()`, `SUM()`, `AVG()`, and     more.
    - **Result**: The original number of rows in the query result is maintained, with   each row now including additional information calculated by the window function.

    **Example Usage**:
    Calculating the cumulative salary within each department without changing the   number of rows in the output.
    ```sql
    SELECT employee_id, department, salary,
           SUM(salary) OVER (PARTITION BY department ORDER BY salary) AS    cumulative_salary
    FROM employees;
    ```

    ### GROUP BY

    - **Context**: Used in aggregation queries.
    - **Purpose**: Groups rows that have the same values in specified columns into  summary rows, like "find the total salary by department."
    - **Functionality**: When you use `GROUP BY`, you must use an aggregate function    (`SUM()`, `COUNT()`, `MAX()`, `MIN()`, `AVG()`, etc.) to reduce the rows in each   group to a single summary row. You cannot select individual row details unless    they are included in the GROUP BY clause or are used in an aggregate function.
    - **Result**: The result set is a condensed version of the original dataset,    usually with fewer rows, where each row represents a group.

    **Example Usage**:
    Calculating the total salary for each department, reducing the output to one row    per department.
    ```sql
    SELECT department, SUM(salary) AS total_salary
    FROM employees
    GROUP BY department;
    ```

    ### Key Differences

    - **Aggregation vs. Windowing**: `GROUP BY` aggregates rows across the entire   table and returns a single row per group, while `PARTITION BY` is used with window    functions to perform calculations across rows that are somehow related to the  current row within each partition, without collapsing these rows into a single row.
    - **Output**: `GROUP BY` produces a summary result with fewer rows, whereas     `PARTITION BY` maintains the original dataset's row count, enriching each row with  additional calculations.

    Understanding when to use `PARTITION BY` versus `GROUP BY` depends on whether you   need to retain individual row details while performing calculations (`PARTITION   BY`) or you need to summarize your data into fewer rows (`GROUP BY`).