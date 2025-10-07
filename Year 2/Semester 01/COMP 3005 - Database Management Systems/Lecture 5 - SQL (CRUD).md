**SQL (Structured Query Language)** is the standard language used to communicate with **relational databases** (MySQL, PostgreSQL, SQL Server, SQLite, Oracle, etc.). It lets you **store, retrieve, update, and manage data**.

These are the four operations you’ll use most often:

1. **CREATE** – Add new data (INSERT).
2. **READ** – Get data (SELECT).
3. **UPDATE** – Modify data.
4. **DELETE** – Remove data.

**SELECT** (Read data)
```
-- Select all columns from the table
SELECT * FROM employees;

-- Select specific columns
SELECT first_name, last_name, email FROM employees;

-- Filtering with WHERE
SELECT * FROM employees WHERE designation = 'Manager';

-- Sorting results
SELECT * FROM employees ORDER BY last_name ASC;

-- Limiting results
SELECT * FROM employees LIMIT 5;

```


**INSERT** (Create new row)
```
INSERT INTO employees (first_name, last_name, email, designation)
VALUES ('John', 'Doe', 'jdoe@example.com', 'Engineer');
```


**UPDATE** (Modify data)
```
UPDATE employees
SET designation = 'Senior Engineer'
WHERE employee_id = 5;
```


**DELETE** (Remove data)
```
DELETE FROM employees
WHERE employee_id = 5;
```



---
#### Filtering and Conditions

```
-- Comparison operators
SELECT * FROM employees WHERE salary > 50000;

-- Multiple conditions
SELECT * FROM employees 
WHERE designation = 'Engineer' AND salary > 60000;

-- Either/or conditions
SELECT * FROM employees 
WHERE designation = 'Engineer' OR designation = 'Manager';

-- Pattern matching
SELECT * FROM employees WHERE email LIKE '%@gmail.com';
```


---
#### Aggregate Functions

```
SELECT COUNT(*) FROM employees;       -- Count rows
SELECT AVG(salary) FROM employees;    -- Average salary
SELECT MAX(salary) FROM employees;    -- Highest salary
SELECT MIN(salary) FROM employees;    -- Lowest salary
SELECT SUM(salary) FROM employees;    -- Total salary

-- Grouping
SELECT designation, AVG(salary)
FROM employees
GROUP BY designation;

-- Group + filter
SELECT designation, COUNT(*)
FROM employees
GROUP BY designation
HAVING COUNT(*) > 5;
```


---
#### Joins (Combining Tables)

A **join** combines rows from two (or more) tables based on a logical relationship between them — usually a **foreign key** and a **primary key**.

The **`ON`** clause tells SQL **how** two tables are related — that is, _which columns_ should match up when combining rows.

The `WHERE` clause tells SQL how to filter the tables after the join.

| Type of JOIN            | Description                                                                                            | When to Use                                                                          |
| ----------------------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| **INNER JOIN** (`JOIN`) | Returns **only rows that match** in both tables.                                                       | When you only care about records that exist in _both_ tables.                        |
| **LEFT JOIN**           | Returns **all rows from the left table**, and matches from the right if they exist (otherwise `NULL`). | When you need _everything_ from the left side, even if no match exists on the right. |


```
-- INNER JOIN: only matching rows
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments 
ON employees.department_id = departments.department_id;

-- LEFT JOIN: all employees, even if no department
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments 
ON employees.department_id = departments.department_id;

```


---
#### Creating and Modifying Tables

```
-- Create a new table
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100) UNIQUE,
    designation VARCHAR(50),
    salary DECIMAL(10,2)
);

-- Add a column
ALTER TABLE employees ADD hire_date DATE;

-- Remove a column
ALTER TABLE employees DROP COLUMN hire_date;
```


---
#### Keys & Constraints

- **PRIMARY KEY** → Unique identifier for rows (usually `id`).
- **FOREIGN KEY** → Connects rows across tables.
- **UNIQUE** → Value must not repeat.
- **NOT NULL** → Value must exist.

Example :
```
CREATE TABLE departments (
    department_id INT PRIMARY KEY AUTO_INCREMENT,
    department_name VARCHAR(100) UNIQUE NOT NULL
);

CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
);
```
