# SQL -- Complete Session Notes

A structured, GitHub-ready reference for learning **SQL (Structured
Query Language)** from fundamentals to advanced querying concepts.

This guide combines the complete classroom session notes into a single
reference covering database fundamentals, CRUD operations, filtering,
sorting, aggregate functions, joins, string and date functions, CTEs,
and window functions.

> **SQL dialect note:** Most examples use standard SQL. Some date
> examples specifically use **SQLite** syntax. Features such as
> `RIGHT JOIN`, `FULL OUTER JOIN`, `LIMIT`, and string/date functions
> can vary by database.

## Table of Contents

1.  [SQL Fundamentals](#sql-fundamentals)
2.  [Data and Databases](#1-data)
3.  [Basic Database Terminology](#3-basic-database-terminology)
4.  [Types of Databases](#4-types-of-databases)
5.  [What is SQL?](#5-what-is-sql)
6.  [SQL in Data Science](#6-why-is-sql-important-in-data-science)
7.  [SQL vs Pandas](#7-sql-vs-pandas)
8.  [OLTP and OLAP](#8-oltp----online-transaction-processing)
9.  [CRUD Operations](#12-crud-operations)
10. [Day 1 -- SQL Basics and Querying](#sql-querying--day-1)
11. [Day 2 -- Advanced SQL](#day-2--advanced-sql)
12. [Quick Reference](#complete-quick-reference)
13. [Practice Exercises](#practice-exercises)

------------------------------------------------------------------------

# SQL Fundamentals

## 1. Data

**Data** is a collection of raw facts, figures, or values that can be
stored and processed to produce meaningful information.

Examples of data include:

-   Employee name
-   Age
-   Salary
-   Customer ID
-   Product price
-   Transaction date

------------------------------------------------------------------------

## 2. Database

A **Database** is an organized collection of data that can be stored,
managed, and accessed efficiently.

For example, an employee database may contain information about
employees, departments, salaries, and job roles.

------------------------------------------------------------------------

## 3. Basic Database Terminology

### Table

A **Table** stores related data in the form of **rows and columns**.

Example:

  employee_id   employee_name   department     salary
  ------------- --------------- ------------ --------
  101           Arun            IT              50000
  102           Priya           HR              45000
  103           Rahul           Sales           55000

### Row

A **Row** represents one complete record in a table.

For example:

``` text
101 | Arun | IT | 50000
```

This row represents one employee record.

### Column

A **Column** stores one specific type of information.

Examples:

-   `employee_id`
-   `employee_name`
-   `department`
-   `salary`

### Primary Key

A **Primary Key** uniquely identifies every row in a table.

Example:

``` text
employee_id
```

Each employee should have a unique `employee_id`.

### Foreign Key

A **Foreign Key** is a column that creates a relationship between two
tables by referring to a primary key in another table.

Example:

``` text
Employees Table              Departments Table

department_id  ───────────►  department_id
Foreign Key                  Primary Key
```

This relationship allows data from multiple tables to be connected.

------------------------------------------------------------------------

## 4. Types of Databases

### A. Relational Database -- RDBMS

An **RDBMS (Relational Database Management System)** stores data in
structured tables consisting of rows and columns.

Relationships can be created between tables using keys.

Examples:

-   MySQL
-   PostgreSQL
-   Oracle Database
-   Microsoft SQL Server
-   SQLite

### B. NoSQL Database

A **NoSQL database** is commonly used for unstructured, semi-structured,
or flexible-schema data.

Depending on the database type, data may be stored as:

-   Documents
-   Key-value pairs
-   Columns
-   Graphs

Examples:

-   MongoDB
-   Cassandra
-   Redis

### RDBMS vs NoSQL -- Quick Comparison

  RDBMS                       NoSQL
  --------------------------- -----------------------------------
  Table-based structure       Flexible data models
  Rows and columns            Documents, key-value, graph, etc.
  Structured schema           Often flexible schema
  SQL commonly used           Query method varies by database
  MySQL, PostgreSQL, Oracle   MongoDB, Cassandra, Redis

------------------------------------------------------------------------

## 5. What is SQL?

**SQL** stands for **Structured Query Language**.

SQL is the standard language used to communicate with relational
databases.

Using SQL, we can perform operations such as:

-   Create database objects
-   Insert data
-   Retrieve data
-   Update existing data
-   Delete data
-   Filter and sort data
-   Perform calculations and analysis

------------------------------------------------------------------------

## 6. Why is SQL Important in Data Science?

A Data Scientist spends a significant amount of time working with data
before building Machine Learning models.

Data is often stored in databases. SQL helps retrieve only the required
data before further analysis.

### Typical Data Science Workflow

``` text
Database
   ↓
  SQL
   ↓
Extract Required Data
   ↓
Python / Pandas
   ↓
Data Cleaning
   ↓
Data Analysis & Visualization
   ↓
Machine Learning
```

SQL is therefore an important skill for accessing and preparing data for
analysis.

------------------------------------------------------------------------

## 7. SQL vs Pandas

SQL and Pandas are often used together in a Data Science workflow.

### SQL

SQL is mainly used to retrieve, filter, join, aggregate, and transform
required data from databases.

Example questions:

-   Which employees belong to the IT department?
-   What is the average salary?
-   Which employee has the highest salary?
-   How many employees belong to each department?

### Python / Pandas

Pandas is commonly used for further data manipulation, cleaning,
analysis, and preparation after data has been loaded into Python.

Example tasks:

-   Clean missing values
-   Transform data
-   Perform exploratory data analysis
-   Prepare data for visualization
-   Prepare datasets for Machine Learning

### Simple Workflow

``` text
SQL
 ↓
Retrieve Required Data
 ↓
Python / Pandas
 ↓
Clean and Analyze
 ↓
Visualization
 ↓
Machine Learning
```

### Example Scenario

Suppose we have employee salary data and want to answer:

1.  What is the average salary?
2.  Which employee has the highest salary?
3.  How can we visualize salaries using a chart?
4.  Can we predict future salaries using Machine Learning?

SQL can retrieve and summarize the required database data, while
Python/Pandas and related libraries can be used for deeper analysis,
visualization, and Machine Learning.

------------------------------------------------------------------------

## 8. OLTP -- Online Transaction Processing

**OLTP** stands for **Online Transaction Processing**.

OLTP systems are designed to manage **day-to-day business
transactions**.

They typically handle:

-   Small and frequent transactions
-   Insert operations
-   Update operations
-   Delete operations
-   Current or live data
-   Many concurrent users

### Examples

-   Banking systems
-   ATM transactions
-   Online shopping
-   Ticket booking
-   Order processing
-   Payment transactions

### Example

When a customer purchases a product online:

``` text
Customer Places Order
        ↓
Order Created
        ↓
Payment Processed
        ↓
Inventory Updated
```

These are typical OLTP operations.

------------------------------------------------------------------------

## 9. OLAP -- Online Analytical Processing

**OLAP** stands for **Online Analytical Processing**.

OLAP systems are designed to analyze large amounts of data and generate
reports, trends, and business insights.

They typically work with:

-   Large datasets
-   Complex analytical queries
-   Historical data
-   Aggregated information
-   Business reporting
-   Decision-making

### Examples

-   Sales dashboards
-   Business Intelligence (BI) reports
-   Data warehouses
-   Revenue analysis
-   Trend analysis

### Example

A company may analyze:

``` text
Historical Sales Data
        ↓
Compare Monthly Sales
        ↓
Identify Trends
        ↓
Generate Dashboard
        ↓
Business Decision
```

------------------------------------------------------------------------

## 10. OLTP vs OLAP

  -----------------------------------------------------------------------
  Feature                 OLTP                    OLAP
  ----------------------- ----------------------- -----------------------
  Full Form               Online Transaction      Online Analytical
                          Processing              Processing

  Purpose                 Daily transactions      Data analysis

  Data                    Current / live          Historical

  Queries                 Short and frequent      Large and complex

  Operations              Insert, Update, Delete  Analysis and
                                                  aggregation

  Users                   Customers, employees,   Analysts, managers,
                          applications            Data Scientists

  Example                 ATM, shopping, booking  BI reports, dashboards,
                                                  data warehouses
  -----------------------------------------------------------------------

### Easy Way to Remember

``` text
OLTP → Running the Business
OLAP → Analyzing the Business
```

------------------------------------------------------------------------

## 11. SQL Online Editor

For classroom practice, we use the **Programiz SQL Online Compiler**.

Open the Programiz SQL Online Compiler in your browser and use the
available sample tables to execute SQL queries.

------------------------------------------------------------------------

## 12. CRUD Operations

**CRUD** represents the four basic operations performed on data.

  CRUD   Operation   SQL Command   Purpose
  ------ ----------- ------------- ------------------------
  C      Create      `INSERT`      Add new data
  R      Read        `SELECT`      Retrieve existing data
  U      Update      `UPDATE`      Modify existing data
  D      Delete      `DELETE`      Remove existing data

### CREATE / INSERT -- Add Data

``` sql
INSERT INTO Customers (customer_id, first_name, last_name, age)
VALUES (6, 'Arun', 'Kumar', 30);
```

### READ -- Retrieve Data

``` sql
SELECT *
FROM Customers;
```

### UPDATE -- Modify Data

``` sql
UPDATE Customers
SET age = 31
WHERE customer_id = 6;
```

### DELETE -- Remove Data

``` sql
DELETE FROM Customers
WHERE customer_id = 6;
```

> **Important:** Always use the `WHERE` clause carefully with `UPDATE`
> and `DELETE`. Without a `WHERE` condition, multiple or all records may
> be affected.

------------------------------------------------------------------------

# SQL Querying -- Day 1

The following sections cover the SQL queries practiced during the
session.

## Day 1: SQL Basics and Querying

## 1. Introduction

SQL (**Structured Query Language**) is used to interact with relational
databases. Using SQL, we can retrieve, filter, sort, and analyze data
stored in database tables.

### Online SQL Editor Used

**Programiz SQL Online Compiler**

The examples below use the sample tables available in the Programiz SQL
editor, mainly:

-   `Customers`
-   `Orders`
-   `Shippings`

------------------------------------------------------------------------

## 2. SELECT -- Retrieve Data

The `SELECT` statement is used to retrieve data from a table.

### Syntax

``` sql
SELECT column_name
FROM table_name;
```

### Example

``` sql
SELECT first_name, last_name
FROM Customers;
```

This retrieves the `first_name` and `last_name` columns from the
`Customers` table.

------------------------------------------------------------------------

## 3. WHERE -- Filter Records

The `WHERE` clause retrieves only records that satisfy a condition.

### Greater Than `>`

``` sql
SELECT first_name, last_name
FROM Customers
WHERE age > 30;
```

### Less Than `<`

``` sql
SELECT first_name, last_name
FROM Customers
WHERE age < 30;
```

### Equal To `=`

``` sql
SELECT first_name, last_name
FROM Customers
WHERE age = 31;
```

### Not Equal To `<>` or `!=`

``` sql
SELECT first_name, last_name
FROM Customers
WHERE age <> 31;
```

``` sql
SELECT first_name, last_name
FROM Customers
WHERE age != 31;
```

### Comparison Operators

  Operator   Meaning
  ---------- --------------------------
  `=`        Equal to
  `>`        Greater than
  `<`        Less than
  `>=`       Greater than or equal to
  `<=`       Less than or equal to
  `<>`       Not equal to
  `!=`       Not equal to

------------------------------------------------------------------------

## 4. ORDER BY -- Sort Records

`ORDER BY` sorts query results. The default is ascending (`ASC`).

### Ascending

``` sql
SELECT first_name, age
FROM Customers
ORDER BY age;
```

### Descending

``` sql
SELECT first_name, age
FROM Customers
ORDER BY age DESC;
```

-   `ASC` → Lowest to Highest / A to Z
-   `DESC` → Highest to Lowest / Z to A

------------------------------------------------------------------------

## 5. LIMIT -- Restrict Number of Records

``` sql
SELECT first_name, age
FROM Customers
LIMIT 3;
```

This returns only the first 3 records.

### Top 3 by Age

``` sql
SELECT first_name, age
FROM Customers
ORDER BY age DESC
LIMIT 3;
```

> **Note:** `LIMIT 3` alone means the first 3 returned rows. It does not
> automatically mean the 3 highest values.

------------------------------------------------------------------------

## 6. Aggregate Functions

  Function    Purpose
  ----------- ---------------------
  `COUNT()`   Counts records
  `SUM()`     Calculates total
  `AVG()`     Calculates average
  `MIN()`     Finds minimum value
  `MAX()`     Finds maximum value

### COUNT()

``` sql
SELECT COUNT(*) AS customer_count
FROM Customers
WHERE age < 30;
```

### SUM()

``` sql
SELECT SUM(age) AS total_age
FROM Customers
WHERE age < 30;
```

### AVG()

``` sql
SELECT AVG(age) AS average_age
FROM Customers;
```

### MAX()

``` sql
SELECT MAX(age) AS maximum_age
FROM Customers;
```

To retrieve the customer details with the maximum age:

``` sql
SELECT first_name, age
FROM Customers
WHERE age = (SELECT MAX(age) FROM Customers);
```

### MIN()

``` sql
SELECT MIN(age) AS minimum_age
FROM Customers;
```

To retrieve the customer details with the minimum age:

``` sql
SELECT first_name, age
FROM Customers
WHERE age = (SELECT MIN(age) FROM Customers);
```

> Avoid mixing a normal column such as `first_name` directly with
> `MIN(age)` or `MAX(age)` without appropriate grouping.

------------------------------------------------------------------------

## 7. AS -- Alias

An alias gives a temporary display name to a column.

``` sql
SELECT first_name AS full_name
FROM Customers;
```

Another example:

``` sql
SELECT AVG(age) AS average_age
FROM Customers;
```

An alias does not permanently rename the database column.

------------------------------------------------------------------------

## 8. Logical Operators -- AND, OR, NOT

### AND

Both conditions must be true.

``` sql
SELECT order_id, amount
FROM Orders
WHERE item = 'Keyboard'
AND customer_id = 4;
```

### OR

At least one condition must be true.

``` sql
SELECT order_id, amount
FROM Orders
WHERE item = 'Keyboard'
OR customer_id = 4;
```

### NOT

Reverses or excludes a condition.

``` sql
SELECT order_id, item, amount
FROM Orders
WHERE NOT item = 'Keyboard';
```

------------------------------------------------------------------------

## 9. IN Operator

`IN` checks whether a value matches any value in a list.

``` sql
SELECT order_id, amount
FROM Orders
WHERE item IN ('Mouse', 'Monitor');
```

This is a shorter alternative to:

``` sql
SELECT order_id, amount
FROM Orders
WHERE item = 'Mouse'
OR item = 'Monitor';
```

------------------------------------------------------------------------

## 10. LIKE Operator

`LIKE` is used for pattern matching. `%` represents zero or more
characters.

### Starts With

``` sql
SELECT shipping_id, status
FROM Shippings
WHERE status LIKE 'D%';
```

`'D%'` means the value starts with `D`.

### Ends With

``` sql
SELECT shipping_id, status
FROM Shippings
WHERE status LIKE '%ing';
```

`'%ing'` means the value ends with `ing`.

### Contains

``` sql
SELECT shipping_id, status
FROM Shippings
WHERE status LIKE '%ship%';
```

### LIKE Pattern Summary

  Pattern      Meaning
  ------------ ---------------
  `'D%'`       Starts with D
  `'%ing'`     Ends with ing
  `'%ship%'`   Contains ship
  `'A%'`       Starts with A
  `'%ed'`      Ends with ed

------------------------------------------------------------------------

## 11. Comments in SQL

Use `--` for a single-line comment.

``` sql
-- Retrieve customers above age 30
SELECT first_name, last_name
FROM Customers
WHERE age > 30;
```

Comments are useful for adding explanations, organizing practice
queries, or temporarily preventing a query from executing.

------------------------------------------------------------------------

## 12. Combined Query Example

### Requirement

Find customers below age 30, sort them from oldest to youngest, and
return only the first 3.

``` sql
SELECT first_name, last_name, age
FROM Customers
WHERE age < 30
ORDER BY age DESC
LIMIT 3;
```

### Easy Flow

`FROM Customers` → `WHERE age < 30` → `SELECT columns` →
`ORDER BY age DESC` → `LIMIT 3`

------------------------------------------------------------------------

## 13. Quick Revision

  SQL Keyword / Operator   Purpose
  ------------------------ --------------------------------------
  `SELECT`                 Retrieve data
  `FROM`                   Specify the table
  `WHERE`                  Filter records
  `>`                      Greater than
  `<`                      Less than
  `=`                      Equal to
  `<>` / `!=`              Not equal to
  `ORDER BY`               Sort records
  `ASC`                    Ascending order
  `DESC`                   Descending order
  `LIMIT`                  Restrict number of rows
  `COUNT()`                Count records
  `SUM()`                  Calculate total
  `AVG()`                  Calculate average
  `MIN()`                  Find minimum value
  `MAX()`                  Find maximum value
  `AS`                     Create an alias
  `AND`                    All conditions must be true
  `OR`                     At least one condition must be true
  `NOT`                    Reverse/exclude a condition
  `IN`                     Match values from a list
  `LIKE`                   Search using a pattern
  `%`                      Wildcard for zero or more characters

------------------------------------------------------------------------

## 14. Practice Exercises

1.  Retrieve the first name and age of all customers.
2.  Find customers whose age is greater than 25.
3.  Find customers whose age is not equal to 22.
4.  Sort customers by age from lowest to highest.
5.  Sort customers by age from highest to lowest.
6.  Retrieve only the first 2 customers.
7.  Count the total number of customers.
8.  Find the average customer age.
9.  Find the maximum customer age.
10. Find the minimum customer age.
11. Find orders where the item is `Keyboard`.
12. Find orders where the item is either `Mouse` or `Monitor`.
13. Find orders where the item is not `Keyboard`.
14. Find shipping statuses starting with `D`.
15. Find shipping statuses ending with `ing`.

# Day 2 -- Advanced SQL

Day 2 builds on the SQL fundamentals from Day 1 and covers grouping,
joins, functions, conditional logic, CTEs, and window functions.

# SQL Basics -- Day 2 Session Notes

A complete SQL code reference covering **GROUP BY**, **HAVING**,
**JOINs**, **string functions**, **date functions**, **CASE WHEN**,
**SELF JOIN**, **CTEs**, and **window functions**.

## Topics Covered

-   GROUP BY and HAVING
-   INNER JOIN
-   LEFT JOIN
-   RIGHT JOIN and RIGHT JOIN simulation
-   FULL OUTER JOIN simulation
-   String functions
-   Date table creation and data insertion
-   SQLite date functions
-   CASE WHEN
-   SELF JOIN
-   Common Table Expressions (CTEs)
-   Window functions
    -   ROW_NUMBER()
    -   RANK()
    -   DENSE_RANK()
    -   PARTITION BY

------------------------------------------------------------------------

## 1. GROUP BY and HAVING

`GROUP BY` groups rows that have the same values in specified columns.\
`HAVING` is used to filter grouped results, usually after applying
aggregate functions.

### Count customers in each country

``` sql
SELECT country, COUNT(*) AS country_count
FROM Customers
GROUP BY country;
```

### Find average age by country

``` sql
SELECT country, AVG(age) AS average_age
FROM Customers
GROUP BY country;
```

### Show countries where average age is greater than 25

``` sql
SELECT country, AVG(age) AS average_age
FROM Customers
GROUP BY country
HAVING AVG(age) > 25;
```

------------------------------------------------------------------------

## 2. INNER JOIN

`INNER JOIN` returns only the matching records from both tables.

``` sql
SELECT Customers.first_name, Orders.item
FROM Orders
INNER JOIN Customers
ON Customers.customer_id = Orders.customer_id;
```

### INNER JOIN with ORDER BY

``` sql
SELECT Customers.first_name, Orders.item
FROM Orders
INNER JOIN Customers
ON Customers.customer_id = Orders.customer_id
ORDER BY Customers.customer_id;
```

------------------------------------------------------------------------

## 3. LEFT JOIN

`LEFT JOIN` returns all records from the left table and matching records
from the right table.

``` sql
SELECT Customers.last_name, Orders.amount
FROM Customers
LEFT JOIN Orders
ON Customers.customer_id = Orders.customer_id;
```

------------------------------------------------------------------------

## 4. RIGHT JOIN / RIGHT JOIN Simulation

`RIGHT JOIN` returns all records from the right table and matching
records from the left table.

### RIGHT JOIN -- if supported by the database

``` sql
SELECT Customers.last_name, Orders.amount
FROM Customers
RIGHT JOIN Orders
ON Customers.customer_id = Orders.customer_id;
```

### Simulate RIGHT JOIN using LEFT JOIN

This approach is useful in databases where `RIGHT JOIN` is not
supported.

``` sql
SELECT Customers.last_name, Orders.amount
FROM Orders
LEFT JOIN Customers
ON Customers.customer_id = Orders.customer_id;
```

------------------------------------------------------------------------

## 5. FULL OUTER JOIN Simulation

A `FULL OUTER JOIN` returns matching and non-matching records from both
tables.

The following query simulates it using `LEFT JOIN` and `UNION`:

``` sql
SELECT Customers.first_name, Orders.item
FROM Customers
LEFT JOIN Orders
ON Customers.customer_id = Orders.customer_id

UNION

SELECT Customers.first_name, Orders.item
FROM Orders
LEFT JOIN Customers
ON Customers.customer_id = Orders.customer_id;
```

------------------------------------------------------------------------

## 6. String Functions

### UPPER()

Converts text to uppercase.

``` sql
SELECT item, UPPER(item) AS item_uppercase
FROM Orders;
```

### LOWER()

Converts text to lowercase.

``` sql
SELECT item, LOWER(item) AS item_lowercase
FROM Orders;
```

### LENGTH()

Returns the number of characters in a string.

``` sql
SELECT item, LENGTH(item) AS item_length
FROM Orders;
```

### CONCAT()

Combines multiple strings or values.

``` sql
SELECT item,
       CONCAT(item, ' costs ', amount) AS item_details
FROM Orders;
```

### SQLite Concatenation

SQLite supports the `||` operator for concatenation.

``` sql
SELECT item,
       item || ' costs ' || amount AS item_details
FROM Orders;
```

### SUBSTRING()

Extracts part of a string.

``` sql
SELECT item,
       SUBSTRING(item, 1, 2) AS short_name
FROM Orders;
```

### TRIM()

Removes extra spaces from the beginning and end of a string.

``` sql
SELECT item,
       TRIM(item) AS trimmed_item
FROM Orders;
```

------------------------------------------------------------------------

## 7. Date Table -- CREATE and INSERT

### Create the OrderedDate table

``` sql
CREATE TABLE OrderedDate (
    order_id INT PRIMARY KEY,
    item VARCHAR(100),
    amount INT,
    customer_id INT,
    order_date DATE
);
```

### Insert sample data

``` sql
INSERT INTO OrderedDate
(order_id, item, amount, customer_id, order_date)
VALUES
(1, 'Keyboard', 400, 4, '2026-01-10'),
(2, 'Mouse', 300, 4, '2026-02-15'),
(3, 'Monitor', 12000, 3, '2026-03-20'),
(4, 'Keyboard', 400, 1, '2026-04-25'),
(5, 'Mousepad', 250, 2, '2026-05-30');
```

------------------------------------------------------------------------

## 8. Date Functions -- SQLite

### Extract Year

``` sql
SELECT order_date,
       strftime('%Y', order_date) AS orderedYear
FROM OrderedDate;
```

### Extract Month

``` sql
SELECT order_date,
       strftime('%m', order_date) AS month
FROM OrderedDate;
```

### Extract Day

``` sql
SELECT order_date,
       strftime('%d', order_date) AS day
FROM OrderedDate;
```

### Find difference between current date and order date

``` sql
SELECT order_date,
       CAST(
           julianday(CURRENT_DATE) - julianday(order_date)
           AS INT
       ) AS days_difference
FROM OrderedDate;
```

### Find days since each order

``` sql
SELECT item,
       order_date,
       CAST(
           julianday(CURRENT_DATE) - julianday(order_date)
           AS INT
       ) AS days_since_order
FROM OrderedDate;
```

------------------------------------------------------------------------

## 9. CASE WHEN -- Student Pass/Fail

`CASE WHEN` is used to apply conditional logic inside a SQL query.

``` sql
SELECT
    name,
    marks,
    CASE
        WHEN marks >= 50 THEN 'Pass'
        ELSE 'Fail'
    END AS result
FROM Students;
```

------------------------------------------------------------------------

## 10. SELF JOIN -- Employee and Manager

A `SELF JOIN` joins a table with itself.\
Here, it is used to map employees to their managers.

### Create Employee table

``` sql
CREATE TABLE Employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(50),
    manager_id INT
);
```

### Insert sample data

``` sql
INSERT INTO Employee (emp_id, name, manager_id)
VALUES
(1, 'Arun', NULL),
(2, 'Bala', 1),
(3, 'Charan', 1),
(4, 'Divya', 2);
```

### Display Employee and Manager

``` sql
SELECT
    e.name AS Employee,
    m.name AS Manager
FROM Employee e
LEFT JOIN Employee m
ON e.manager_id = m.emp_id;
```

------------------------------------------------------------------------

## 11. CTE -- Passed Students

A **Common Table Expression (CTE)** creates a temporary named result set
that can be used within the main query.

``` sql
WITH PassedStudents AS (
    SELECT name AS PassedStudents, marks
    FROM Students
    WHERE marks >= 60
)

SELECT *
FROM PassedStudents;
```

------------------------------------------------------------------------

## 12. CTE -- Students Above Average Marks

This CTE calculates the average marks first and then displays students
whose marks are above the average.

``` sql
WITH AverageMarks AS (
    SELECT AVG(marks) AS avg_marks
    FROM Students
)

SELECT name, marks
FROM Students, AverageMarks
WHERE marks > avg_marks;
```

------------------------------------------------------------------------

## 13. Window Function -- ROW_NUMBER()

`ROW_NUMBER()` assigns a unique sequential number to every row.

``` sql
SELECT
    name,
    marks,
    ROW_NUMBER() OVER(ORDER BY marks) AS row_num
FROM StudentMarks;
```

------------------------------------------------------------------------

## 14. Window Function -- RANK()

`RANK()` assigns the same rank to rows with equal values and skips the
next rank when there is a tie.

``` sql
SELECT
    name,
    marks,
    RANK() OVER(ORDER BY marks DESC) AS student_rank
FROM StudentMarks;
```

------------------------------------------------------------------------

## 15. Window Function -- DENSE_RANK()

`DENSE_RANK()` assigns the same rank to equal values but does **not**
skip rank numbers after a tie.

``` sql
SELECT
    name,
    marks,
    DENSE_RANK() OVER(ORDER BY marks DESC) AS student_rank
FROM StudentMarks;
```

------------------------------------------------------------------------

## 16. ROW_NUMBER() vs RANK() vs DENSE_RANK()

``` sql
SELECT
    name,
    marks,
    ROW_NUMBER() OVER(ORDER BY marks DESC) AS row_num,
    RANK() OVER(ORDER BY marks DESC) AS rank_num,
    DENSE_RANK() OVER(ORDER BY marks DESC) AS dense_rank_num
FROM StudentMarks;
```

  Function         Duplicate Values       Rank Gaps
  ---------------- ---------------------- -----------
  `ROW_NUMBER()`   Gets a unique number   No
  `RANK()`         Gets the same rank     Yes
  `DENSE_RANK()`   Gets the same rank     No

------------------------------------------------------------------------

## 17. PARTITION BY with RANK()

`PARTITION BY` divides the result into groups before applying the window
function.

The following query ranks students separately within each department:

``` sql
SELECT
    name,
    department,
    marks,
    RANK() OVER(
        PARTITION BY department
        ORDER BY marks DESC
    ) AS dept_rank
FROM StudentMarks;
```

------------------------------------------------------------------------

# Complete Quick Reference

  -----------------------------------------------------------------------
  Category                SQL Feature             Purpose
  ----------------------- ----------------------- -----------------------
  Retrieval               `SELECT`                Retrieve data

  Source                  `FROM`                  Specify source table

  Filtering               `WHERE`                 Filter rows

  Sorting                 `ORDER BY`              Sort query results

  Limiting                `LIMIT`                 Restrict returned rows

  Aliasing                `AS`                    Give a temporary name

  Logic                   `AND`, `OR`, `NOT`      Combine or reverse
                                                  conditions

  Matching                `IN`                    Match values from a
                                                  list

  Pattern Search          `LIKE`                  Search using patterns

  Aggregation             `COUNT()`, `SUM()`,     Summarize data
                          `AVG()`, `MIN()`,       
                          `MAX()`                 

  Grouping                `GROUP BY`              Group rows for
                                                  aggregation

  Group Filtering         `HAVING`                Filter grouped results

  Joins                   `INNER`, `LEFT`,        Combine related tables
                          `RIGHT`                 

  Set Operations          `UNION`                 Combine result sets

  Text                    `UPPER()`, `LOWER()`,   Manipulate strings
                          `LENGTH()`, `CONCAT()`, 
                          `SUBSTRING()`, `TRIM()` 

  Conditional Logic       `CASE WHEN`             Apply conditions in
                                                  query output

  Reusable Query          `CTE` / `WITH`          Create a temporary
                                                  named result set

  Window Functions        `ROW_NUMBER()`,         Rank or number rows
                          `RANK()`,               
                          `DENSE_RANK()`          

  Window Grouping         `PARTITION BY`          Apply window functions
                                                  within groups
  -----------------------------------------------------------------------

# Practice Exercises

Use the sample `Customers`, `Orders`, `Shippings`, `Students`,
`StudentMarks`, `Employee`, and `OrderedDate` tables where applicable.

1.  Retrieve customer names and ages.
2.  Find customers older than 25.
3.  Sort customers by age in descending order.
4.  Return only the top 3 oldest customers.
5.  Calculate the average customer age.
6.  Count customers by country using `GROUP BY`.
7.  Show only countries whose average age is greater than 25 using
    `HAVING`.
8.  Join `Customers` and `Orders` to display customer names with ordered
    items.
9.  Use a `LEFT JOIN` to include customers even when they have no
    matching orders.
10. Convert order item names to uppercase and lowercase.
11. Extract year, month, and day from an order date using SQLite date
    functions.
12. Use `CASE WHEN` to classify students as Pass or Fail.
13. Use a self join to display each employee with their manager.
14. Create a CTE to retrieve students who scored at least 60.
15. Create a CTE to find students who scored above the class average.
16. Compare `ROW_NUMBER()`, `RANK()`, and `DENSE_RANK()` using duplicate
    marks.
17. Rank students separately within each department using
    `PARTITION BY`.

------------------------------------------------------------------------

## Important Notes

-   SQL syntax varies slightly between database systems such as SQLite,
    MySQL, PostgreSQL, Oracle Database, and Microsoft SQL Server.
-   Always use a `WHERE` clause carefully with `UPDATE` and `DELETE`.
-   `HAVING` filters grouped results, while `WHERE` filters rows before
    grouping.
-   `LIMIT` is common in SQLite, MySQL, and PostgreSQL; other databases
    may use different syntax.
-   Verify database-specific support for `RIGHT JOIN`,
    `FULL OUTER JOIN`, string functions, and date functions.

------------------------------------------------------------------------

**Happy Learning!**
