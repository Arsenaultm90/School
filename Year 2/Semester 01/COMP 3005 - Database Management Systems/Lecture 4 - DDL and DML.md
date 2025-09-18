#### Data Definition Language (DDL)

Defines or changes the **structure** of the database (tables, schemas, constraints).

**Commands :**
- `CREATE` → make new database objects (e.g., `CREATE TABLE`)
- `ALTER` → modify an existing object (e.g., add/drop a column)
- `DROP` → delete an object (e.g., `DROP TABLE`)
- `TRUNCATE` → remove all rows from a table but keep its structure
- `COMMENT` (in some DBMSs) → Add a comment to schema objects
- `RENAME` → Change the name of a database object

Example :
```
CREATE TABLE Student (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);

ALTER TABLE Student ADD email VARCHAR(100);

DROP TABLE Student;
```


---
#### Data Manipulation Language (DML)

Used to manipulate the **data inside tables** (insert, update, delete, query).

**Commands :**
- `SELECT` (Also in DQL, Data Query Language) → query data
- `INSERT` → add new records
- `UPDATE` → modify existing records
- `DELETE` → remove records
- `MERGE` (a.k.a. UPSERT, depends on DBMS) → Insert or update depending on conditions
- `CALL` (procedures/functions in some DBMSs)
- `EXPLAIN` (some classify this as DML) → Show execution plan

Example :
```
INSERT INTO Student (id, name, age, email)
VALUES (1, 'Alice', 20, 'alice@example.com');

UPDATE Student
SET age = 21
WHERE id = 1;

DELETE FROM Student
WHERE id = 1;

SELECT * FROM Student;
```
