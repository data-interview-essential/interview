---
layout: default
title: SQL Exercise
parent: SQL
nav_order: 8
---

For a data engineer position at a big tech company, the SQL coding test might involve complex scenarios requiring advanced SQL skills, data modeling insights, and an understanding of efficient data processing techniques. Here’s an illustrative example that includes database design, writing complex queries, and potential follow-up questions with answers.

# SQL Coding Test Example 1: User Engagement Analysis

**Scenario**: You are given two tables, `users` and `page_views`. The `users` table contains information about users, and the `page_views` table tracks each user's page visits on a website.

- `users` table:
  - `user_id` (integer)
  - `signup_date` (date)
  - `country` (varchar)

- `page_views` table:
  - `view_id` (integer)
  - `user_id` (integer)
  - `page_id` (integer)
  - `view_date` (date)

**Task**:
1. **Find the total number of page views for each country.**
2. **Calculate the monthly active users (MAU) for each month.**
3. **Identify the first page viewed by each user after signup.**

**SQL Queries**:

1. Total number of page views for each country:
   ```sql
   SELECT u.country, COUNT(p.view_id) AS total_views
   FROM users u
   JOIN page_views p ON u.user_id = p.user_id
   GROUP BY u.country;
   ```
   **Answer**: This query joins the `users` and `page_views` tables on `user_id` to aggregate the total page views by country.

2. Monthly active users (MAU) for each month:
   ```sql
   SELECT YEAR(view_date) AS year, MONTH(view_date) AS month, COUNT(DISTINCT user_id) AS MAU
   FROM page_views
   GROUP BY YEAR(view_date), MONTH(view_date);
   ```
   **Answer**: This query counts the distinct `user_id`s per month and year in the `page_views` table, calculating the MAU.

3. First page viewed by each user after signup:
   ```sql
   WITH RankedPageViews AS (
     SELECT
       u.user_id,
       p.page_id,
       p.view_date,
       RANK() OVER (PARTITION BY u.user_id ORDER BY p.view_date ASC) AS rank
     FROM users u
     JOIN page_views p ON u.user_id = p.user_id
     WHERE p.view_date >= u.signup_date
   )
   SELECT
     user_id,
     page_id,
     view_date AS first_view_date
   FROM RankedPageViews
   WHERE rank = 1;
   ```
   **Answer**: This query finds the first page each user viewed after their signup date by selecting the minimum `view_date` for each user that is on or after their `signup_date`.

### Follow-up Questions:

1. **How would you optimize the database schema for querying large datasets?**
   
   **Answer**: To optimize the schema, consider indexing key columns (`user_id`, `country`, `view_date`) to speed up join operations and WHERE clause filtering. Partitioning the `page_views` table by `view_date` can also improve query performance for time-based queries.

2. **If the database is very large, how would you handle performance issues?**
   
   **Answer**: Besides indexing and partitioning, consider query optimization techniques such as avoiding SELECT *, using appropriate join types, and leveraging aggregate functions wisely. For very large datasets, using a distributed SQL database or a columnar storage format can improve performance. Caching frequently accessed data and using materialized views for complex aggregations can also be effective.

3. **How can you ensure data quality in this scenario?**
   
   **Answer**: Implement data validation rules at the point of data entry (e.g., constraints in the database schema). Regularly run data quality checks to identify and correct anomalies or inconsistencies. Use foreign key constraints to maintain referential integrity between `users` and `page_views`.

These tasks and follow-up questions cover a range of skills relevant to a data engineer role, including SQL querying, database optimization, and data quality assurance.
