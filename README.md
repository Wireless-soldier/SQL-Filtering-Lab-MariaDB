# SQL Filtering Lab — MariaDB

## Activity Overview

This lab provided practical experience using SQL filters to retrieve specific information from a MariaDB database.

The lab focused on:

- Using `SELECT` to retrieve specific columns
- Using `WHERE` to filter records
- Using `=` to match specific values
- Using `LIKE` to search for patterns
- Using `%` as a wildcard
- Querying employee and machine information

---

## Scenario

The organization database contains information about employees, their machines, departments, and offices.

The goal of the lab was to retrieve specific information by applying SQL filters.

The tasks were:

1. List all organization machines and their operating systems
2. Identify machines running `OS 2`
3. Identify employees in the Finance and Sales departments
4. Identify employees associated with machines in the South building

---

## Database

The lab uses a MariaDB database named:

```bash
organization

Orientation — Know Your Data

Before querying the database, I inspected the structure of the tables using DESCRIBE.

DESCRIBE machines;
DESCRIBE employees;

DESCRIBE shows the structure of a table, including:

Column names
Data types
Table fields

This is useful because SQL queries must use the exact column names defined in the database.

Task 1 — List All Organization Machines
Objective

Retrieve the device_id and operating_system columns from the machines table.

SQL Query
SELECT device_id, operating_system
FROM machines;
Result
+--------------+------------------+
| device_id    | operating_system |
+--------------+------------------+
| a184b775c707 | OS 1             |
| a192b174c940 | OS 2             |
| a305b818c708 | OS 3             |
| a317b635c465 | OS 1             |
| a320b137c219 | OS 2             |
| a398b471c573 | OS 3             |
|...                              |
+--------------+------------------+
200 rows in set (0.028 sec)

How many rows were returned from the machines table? (You can view the number of

The query returned:

200 rows

Answer

200

Task 2 — Retrieve Machines Running OS 2
Objective

Find all machines that are running the OS 2 operating system.

SQL Query
SELECT device_id, operating_system
FROM machines
WHERE operating_system = 'OS 2';

The WHERE clause filters the results so that only records matching the specified condition are returned.

Result
+--------------+------------------+
| device_id    | operating_system |
+--------------+------------------+
| a192b174c940 | OS 2             |
| a320b137c219 | OS 2             |
| a821b452c176 | OS 2             |
| b157c491d493 | OS 2             |
| b264c773d977 | OS 2             |
|...                              |
+--------------+------------------+
80 rows in set (0.264 sec)

The database contains:

80 machines running OS 2

Answer

80

Task 3 — List Employees in Specific Departments
Finance Department
Objective

Retrieve all employees who work in the Finance department.

SQL Query
SELECT *
FROM employees
WHERE department = 'Finance';
Result

The first employee returned has the employee ID:

1003

Answer

1003

Sales Department
Objective

Retrieve all employees who work in the Sales department.

SQL Query
SELECT *
FROM employees
WHERE department = 'Sales';
Result

There are:

33 employees

working in the Sales department.

Answer

33

Task 4 — Identify Employee Machines
South-109
Objective

Identify the employee who uses the office associated with the machine issue at South-109.

SQL Query
SELECT *
FROM employees
WHERE office = 'South-109';
Result

The employee is:

jlansky

Answer

jlansky

Employees in the South Building

The organization uses office names that contain the building name followed by a hyphen and office number.

Examples:

South-109
South-210
South-305

To find all employees whose office begins with South, the LIKE operator and % wildcard can be used.

SQL Query
SELECT *
FROM employees
WHERE office LIKE 'South%';
Result

The first employee listed in the South building belongs to the:

Finance department.

Answer

Finance

SQL Concepts Learned
SELECT

SELECT is used to specify which columns should be returned.

Example:

SELECT device_id, operating_system
FROM machines;
WHERE

WHERE filters records based on a condition.

Example:

SELECT *
FROM employees
WHERE department = 'Finance';

Only employees whose department is Finance are returned.

Equality Operator

The = operator is used to match an exact value.

Example:

WHERE operating_system = 'OS 2';

This returns records where the operating system is exactly OS 2.

LIKE Operator

The LIKE operator is used to perform pattern matching.

Example:

WHERE office LIKE 'South%';

The % wildcard represents zero or more characters.

Therefore, the query can match values such as:

South-109
South-210
South-305
Complete SQL Queries

All queries used during the lab are collected below.

-- Inspect table structures
DESCRIBE machines;
DESCRIBE employees;




-- Task 1: List all organization machines
SELECT device_id, operating_system
FROM machines;




-- Task 2: Find machines running OS 2
SELECT device_id, operating_system
FROM machines
WHERE operating_system = 'OS 2';




-- Task 3: Find employees in Finance
SELECT *
FROM employees
WHERE department = 'Finance';




-- Task 3: Find employees in Sales
SELECT *
FROM employees
WHERE department = 'Sales';




-- Task 4: Identify employee using South-109
SELECT *
FROM employees
WHERE office = 'South-109';




-- Task 4: Find all employees in the South building
SELECT *
FROM employees
WHERE office LIKE 'South%';
Lab Results
Task	Result
Total machines	200
Machines running OS 2	80
First Finance employee ID	1003
Employees in Sales	33
Employee at South-109	jlansky
First South-building employee's department	Finance
Key Takeaways

This lab provided hands-on practice with SQL filtering in a MariaDB environment.

The main concepts practiced were:

SELECT
WHERE
=
LIKE
% wildcard
DESCRIBE
Filtering database records
Retrieving specific employee and machine information

These SQL skills are useful for security analysts because databases can contain large amounts of information. Filtering allows analysts to quickly locate the records relevant to an investigation or security task.

Skills Demonstrated
SQL
MariaDB
Database querying
SQL filtering
WHERE clauses
Pattern matching with LIKE
Database reconnaissance
Security analyst fundamentals
Data retrieval and analysis
