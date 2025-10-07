#### View

- A **View** is a **virtual table** created from a SQL query.
- It doesn’t store the data itself but provides a way to look at data from one or more tables.
    
- Useful for:
    - Simplifying complex queries
    - Providing security (restricting access to certain columns/rows)
    - Presenting data in a user-friendly format

**Example:**
```
CREATE VIEW EmployeeView AS
SELECT first_name, last_name, department
FROM Employees
WHERE active = 1;
```


---
#### Materialized View

- A **Materialized View** is similar to a view, but **it stores the query result physically** in the database.
- Unlike normal views, materialized views take up storage space.
- They are **faster for repeated queries**, but need to be **refreshed** when underlying data changes.

**Example:**
```
CREATE MATERIALIZED VIEW SalesSummary AS
SELECT region, SUM(amount) AS total_sales
FROM Sales
GROUP BY region;
```


---
#### Sequence

- A **Sequence** is a database object that generates **unique numbers**.
- Commonly used to create **primary keys**.
- Values are generated in order (incrementing or decrementing).

**Example:**
```
CREATE SEQUENCE emp_seq
START WITH 1
INCREMENT BY 1;

INSERT INTO Employees (id, name)
VALUES (emp_seq.NEXTVAL, 'Alice');
```


---
#### Index

- An **Index** improves query performance by allowing the database to **find rows faster** (like an index in a book).
- It speeds up `SELECT` queries but may slow down `INSERT`/`UPDATE`/`DELETE` since the index also needs updating.
- Types: **B-tree index, unique index, composite index, bitmap index**, etc.

**Example:**
```
CREATE INDEX idx_emp_lastname
ON Employees(last_name);
```


---
#### Functions

- A **Function** is a **stored block of code** in SQL that performs an operation and returns a single value.
- Can accept parameters and be reused in queries.

**Example:**
```
CREATE FUNCTION GetFullName(emp_id INT)
RETURNS VARCHAR(100)
AS
BEGIN
   RETURN (SELECT first_name || ' ' || last_name 
           FROM Employees WHERE id = emp_id);
END;
```


---
#### Triggers

- A **Trigger** is a special procedure that **automatically executes** when a certain event occurs on a table (e.g., `INSERT`, `UPDATE`, `DELETE`).
- Used for enforcing rules, auditing changes, or maintaining derived data.

**Example:**
```
CREATE TRIGGER trg_update_salary
AFTER UPDATE ON Employees
FOR EACH ROW
BEGIN
   INSERT INTO Salary_Audit(emp_id, old_salary, new_salary, changed_on)
   VALUES (:OLD.id, :OLD.salary, :NEW.salary, SYSDATE);
END;
```


---
#### Transactions

- A **Transaction** is a group of one or more SQL statements executed as a single unit of work.
- Transactions follow the **ACID properties**:
    - **A**tomicity – all or nothing
    - **C**onsistency – must leave DB in a valid state
    - **I**solation – transactions don’t interfere
    - **D**urability – once committed, changes are permanent

**Example:**
```
BEGIN;

UPDATE Accounts SET balance = balance - 500 WHERE id = 1;
UPDATE Accounts SET balance = balance + 500 WHERE id = 2;

COMMIT;  -- save changes permanently
-- or ROLLBACK; to undo if something goes wrong
```


---
#### DCL (Data Control Language)

- **DCL** controls **access rights and permissions** in the database.
- Main commands:
    - `GRANT` – give permission
    - `REVOKE` – take back permission

**Example:**
```
GRANT SELECT, INSERT ON Employees TO user1;
REVOKE INSERT ON Employees FROM user1;
```


---
#### Summary

- **View** → Virtual table (no data stored).
- **Materialized View** → Physical table storing results.
- **Sequence** → Generates unique numbers.
- **Index** → Speeds up queries.
- **Function** → Custom reusable code that returns a value.
- **Trigger** → Auto-executes on table events.
- **Transaction** → Bundle of SQL statements with ACID rules.
- **DCL** → Manage permissions and access control.