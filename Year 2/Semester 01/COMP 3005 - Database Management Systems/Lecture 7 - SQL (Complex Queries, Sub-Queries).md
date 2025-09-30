#### Subqueries

A **subquery** is a query inside another query (like a nested SELECT).

**Types of subqueries**
- **Scalar subquery** → returns a single value
- **Row subquery** → returns a single row
- **Table subquery** → returns multiple rows (can be used with `IN`, `EXISTS`, etc.)

**Example: Scalar subquery**
```
-- Get employees who earn more than the average salary
SELECT first_name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

**Example: Row subquery**
```
-- Get employee with the highest salary
SELECT *
FROM employees
WHERE (salary, employee_id) = (
    SELECT MAX(salary), employee_id
    FROM employees
);
```

**Example: Table subquery**
```
-- Get employees in departments located in 'Toronto'
SELECT first_name, department_id
FROM employees
WHERE department_id IN (
    SELECT department_id
    FROM departments
    WHERE location = 'Toronto'
);
```



---
#### Quantifiers

Quantifiers are used with subqueries to compare values. The most common are:
- `ANY` (or `SOME`)
- `ALL`
- `EXISTS`

`ANY`
True if condition matches **at least one row**.
```
-- Employees who earn more than at least one Manager
SELECT first_name, salary
FROM employees
WHERE salary > ANY (
    SELECT salary FROM employees WHERE designation = 'Manager'
);
```


`ALL`
True if condition matches **every row**.
```
-- Employees who earn more than all Managers
SELECT first_name, salary
FROM employees
WHERE salary > ALL (
    SELECT salary FROM employees WHERE designation = 'Manager'
);
```


`EXISTS`
True if subquery returns **at least one row**.
```
-- Find departments that have employees
SELECT department_name
FROM departments d
WHERE EXISTS (
    SELECT 1
    FROM employees e
    WHERE e.department_id = d.department_id
);
```



---
#### WITH Clause (Common Table Expressions – CTE)

The `WITH` clause lets you create a **temporary named result set** you can reuse inside a query.

Example :
```
WITH DeptAvg AS (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
)
SELECT e.first_name, e.salary, d.avg_salary
FROM employees e
JOIN DeptAvg d
  ON e.department_id = d.department_id
WHERE e.salary > d.avg_salary;
```
	
This finds employees earning more than their department’s average salary.



---
#### Divide By Operator

This isn’t part of SQL syntax itself, but it’s a **relational algebra concept**. In SQL, we simulate it.

**Problem it solves:**  
“Find entities that are related to **all values** in another set.”

 **Example problem**
> Find customers who bought **all products** in the `Products` table.

```
SELECT customer_id
FROM Purchases p
GROUP BY customer_id
HAVING COUNT(DISTINCT product_id) = (
    SELECT COUNT(*) FROM Products
);

```

The idea is:
- Count how many distinct products each customer bought.
- Compare that to the total number of products.
- If they match, that customer bought _all_ products (the "division").