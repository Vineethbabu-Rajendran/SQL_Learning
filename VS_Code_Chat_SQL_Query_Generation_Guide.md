# SQL Query Generation Using VS Code Chat

## Step-by-Step User Guide

This document explains how to configure the chat available in Visual
Studio Code to act as an SQL Developer. After providing a reusable
instruction prompt, you can enter a table structure and a requirement.
The chat should respond with only the required SQL query in a clean,
standard SQL code block.

## 1. Objective

The objective is to use VS Code Chat as a simple SQL query generator.
The user first provides a fixed instruction prompt. After that, the user
supplies the database table structure and a clear requirement. The
assistant generates only the SQL query, without explanations, headings,
comments, or additional text.

## 2. Prerequisites

-   Visual Studio Code is installed and available.
-   A supported AI chat extension or built-in chat capability is
    configured and signed in.
-   You know the table name, column names, and relevant data types.
-   You have a clear SQL requirement, such as SELECT, JOIN, GROUP BY,
    INSERT, UPDATE, DELETE, or filtering.

## 3. Open the Chat in VS Code

### Step 1: Open Visual Studio Code

Launch Visual Studio Code on your system.

### Step 2: Open the Chat panel

Open the AI Chat/Chat panel available in your VS Code environment. You
can use the Chat icon or the command provided by your installed chat
extension.

### Step 3: Start a new chat

Starting a fresh chat is recommended so that the SQL-specific
instruction is applied consistently to the conversation.

## 4. Provide the SQL Developer Instruction Prompt

Paste the following prompt as the first message in the chat. This
defines the expected role and response format.

> You are an expert SQL Developer. Whenever I provide a table structure
> and a requirement, return only the SQL query inside a SQL code block.
> Do not include explanations, comments, headings, or formatting other
> than the query. Use clear, readable, and standard SQL formatting with
> SQL keywords in uppercase, meaningful aliases where required,
> consistent indentation, and each major SQL clause on a separate line.
> Wait for my table structure and requirement.

The additional standard-format instruction ensures that generated SQL is
consistently readable---for example, uppercase SQL keywords, proper
indentation, and separate lines for major clauses.

## 5. Provide the Table Structure

After the assistant accepts the instruction and waits for input, provide
the table structure. Include the table name, column names, and data
types whenever possible. Primary-key or relationship information can
also be included if the requirement involves joins.

### Example Table Structure

``` text
Table: employees

employee_id INT PRIMARY KEY
employee_name VARCHAR(100)
department VARCHAR(50)
salary DECIMAL(10,2)
joining_date DATE
```

## 6. Provide the Requirement

In the same message or immediately after the table structure, describe
exactly what data or operation is required. Use a clear business
requirement rather than trying to write the SQL yourself.

**Example requirement:**

Display the employee name, department, and salary for employees whose
salary is greater than 50000. Sort the result by salary in descending
order.

## 7. Recommended Input Format

For consistent results, use the following simple structure whenever you
ask for a query:

``` text
Table Structure:
<Table name and columns>

Requirement:
<Describe the SQL requirement clearly>
```

## 8. Complete Example

### Input provided in VS Code Chat

``` text
Table Structure:

Table: employees
employee_id INT PRIMARY KEY
employee_name VARCHAR(100)
department VARCHAR(50)
salary DECIMAL(10,2)
joining_date DATE

Requirement:
Display the employee name, department, and salary for employees whose salary is greater than 50000. Sort the result by salary in descending order.
```

### Expected response from the chat

``` sql
SELECT
    employee_name,
    department,
    salary
FROM employees
WHERE salary > 50000
ORDER BY salary DESC;
```

The response should contain only the SQL code block. It should not
include text such as "Here is your query," explanations, comments, or
headings.

## 9. Example with Multiple Tables

### Input

``` text
Table Structure:

Table: employees
employee_id INT PRIMARY KEY
employee_name VARCHAR(100)
department_id INT
salary DECIMAL(10,2)

Table: departments
department_id INT PRIMARY KEY
department_name VARCHAR(100)

Requirement:
Display employee name, department name, and salary for all employees. Sort by employee name.
```

### Expected SQL

``` sql
SELECT
    e.employee_name,
    d.department_name,
    e.salary
FROM employees AS e
INNER JOIN departments AS d
    ON e.department_id = d.department_id
ORDER BY e.employee_name;
```

## 10. Standard SQL Formatting Expected

-   Use uppercase for SQL keywords such as SELECT, FROM, WHERE, JOIN,
    GROUP BY, HAVING, and ORDER BY.
-   Place major SQL clauses on separate lines.
-   Indent selected columns and nested conditions consistently.
-   Use meaningful table aliases when multiple tables are involved.
-   Terminate the query with a semicolon.
-   Return only the SQL query inside a SQL code block.

## 11. Workflow Summary

1.  Open Visual Studio Code.
2.  Open the available AI Chat panel.
3.  Start a new chat.
4.  Paste the SQL Developer instruction prompt.
5.  Wait for the assistant to request the table structure and
    requirement.
6.  Provide the table structure with table name, columns, and data
    types.
7.  Provide the SQL requirement clearly.
8.  Review the generated SQL query.
9.  Copy the query into your SQL editor or database tool.
10. Validate the query in the appropriate development or test
    environment before using it on production data.

## 12. Best Practices

-   Mention the SQL dialect when it matters, for example MySQL,
    PostgreSQL, SQL Server, or Oracle.
-   Provide all tables and relationship columns required for JOIN
    operations.
-   State expected filters, sorting, grouping, and aggregation
    explicitly.
-   If exact output columns are required, list them in the requirement.
-   For UPDATE or DELETE requirements, verify the WHERE condition
    carefully before execution.
-   Do not share production passwords, secrets, or sensitive data in the
    chat.
-   Always validate AI-generated SQL before executing data-changing
    statements.

## 13. Reusable Prompt

Use this prompt whenever you start a fresh SQL-focused chat in VS Code:

> You are an expert SQL Developer. Whenever I provide a table structure
> and a requirement, return only the SQL query inside a SQL code block.
> Do not include explanations, comments, headings, or formatting other
> than the query. Use clear, readable, and standard SQL formatting with
> SQL keywords in uppercase, meaningful aliases where required,
> consistent indentation, and each major SQL clause on a separate line.
> Wait for my table structure and requirement.

## 14. Conclusion

By setting the instruction prompt first and then supplying a structured
table definition and requirement, VS Code Chat can be used as a
consistent SQL query-generation assistant. The defined response rule
keeps the output focused on executable SQL, while the formatting
guidelines make the generated query easier to read, review, and reuse.
