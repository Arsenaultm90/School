
Relational Algebra = **theoretical language** for querying relational databases.
- **Input**: Relations (tables)
- **Output**: New relations (tables)
- Used in query optimization and forms basis of **SQL**.


```
Employees = { EMPID, NAME, POSITION, SALARY, DEPTID
	101, "Alice", "Manager", 3000, D01
	102, "Bob", "Manager", 4500, D02
	103, "Charlie", "Developer", 4000, D01
	104, "David", "Developer", 3800, D03
	105, "Emily", "Manager", 2900, D03
} 

Departments = { DEPTID, DEPTNAME, MANAGERID
	D01, "IT", 101
	D02, "Finance", 102
	D03, "Marketing", 105
}

ProjectsTable = { PROJECTID, PROJECTNAME, LEADEMPID, BUDGET
	P01, "Alpha", 101, 500000
	P02, "Beta", 103, 2000000
	P03, "Gamma", 102, 750000
	P04, "Delta", 104, 1250000
}
```

---
#### Basic Operations

**1.1 Selection (σ)**
- Filters rows based on condition.
- Syntax:  
    `σ_condition(Relation)`
Example :
```
σ_salary > 50000 (Employee)  
```
→ all employees with salary > 50,000.


**1.2 Projection (π)**
- Chooses specific columns.
- Syntax:  
    `π_col1, col2,...(Relation)`
Example:
```
π_name, salary (Employee)  
```
→ table with only employee names + salaries.


**1.3 Union (⋃)**
- Combines tuples from two relations (no duplicates).
- Syntax:  
    `R ⋃ S`
- Requirements: **same attributes & domains**.

 1.4 **Intersection (∩)**
- Returns tuples that are **in both relations**.
- Requires both relations to have **same attributes**.

**Relational Algebra Notation:** `R ∩ S`
SQL Example :
```
SELECT * FROM R
INTERSECT
SELECT * FROM S;
```
Only common rows are kept.

**1.5 Set Difference (−)**
- Tuples in one relation but not the other.
- Syntax:  
    `R − S`


**1.6 Cartesian Product (×)**
- Combines all tuples from R with all tuples from S.
- Syntax:  
    `R × S`
Example:
```
Employee × Department  
```
→ all employee-department combinations.


**1.7 Rename (ρ)**
- Renames relation or attributes.
- Syntax:  
    `ρ_newName(Relation)` or `ρ_newRelName(A1, A2,...)(Relation)`



---
#### Outer Joins

Outer joins = join + keep **unmatched tuples**, filling with `NULL` where no match.

1. **Left Outer Join (⟕)**
- Keeps **all tuples from left relation (R)**.
- If no match in right relation (S), fill with `NULL`.

**Relational Algebra Notation:** `R ⟕ S`
SQL Example :
```
SELECT E.name, D.deptName
FROM Employee E
LEFT OUTER JOIN Department D
ON E.deptID = D.deptID;
```
Shows all employees. If an employee’s dept doesn’t exist in `Department`, `deptName` = NULL.

2. **Right Outer Join (⟖)**
- Keeps **all tuples from right relation (S)**.
- If no match in left relation (R), fill with `NULL`.

**Relational Algebra Notation:** `R ⟖ S`
SQL Example :
```
SELECT E.name, D.deptName
FROM Employee E
RIGHT OUTER JOIN Department D
ON E.deptID = D.deptID;
```
Shows all departments. If a dept has no employees, employee `name` = NULL.

3. **Full Outer Join (⟗)**
- Keeps **all tuples from both R and S**.
- Where no match, fill with `NULL` on the missing side.

**Relational Algebra Notation:** `R ⟗ S`
SQL Example :
```
SELECT E.name, D.deptName
FROM Employee E
FULL OUTER JOIN Department D
ON E.deptID = D.deptID;
```
Shows all employees + all departments. If a tuple exists only on one side, other side’s attributes = NULL.

|Join Type|Keeps All From|NULLs On|
|---|---|---|
|Left Outer Join|Left table|Right|
|Right Outer Join|Right table|Left|
|Full Outer Join|Both tables|Both|


---
#### Inner Join

**Inner Join (⨝θ)**
- Joins two relations on a **condition (θ)**.
- Keeps only tuples that **satisfy condition**.

**Relational Algebra Notation:** `R ⨝ condition S`
SQL Example :
```
SELECT E.name, D.deptName
FROM Employee E
INNER JOIN Department D
ON E.deptID = D.deptID;
```
Only employees that have a matching department appear.


---
#### Natural Join

**Natural Join (⨝)**
- Special case of inner join.
- Joins **on all attributes with the same name**.
- Removes duplicate columns.

**Relational Algebra Notation:** `R ⨝ S`
SQL Example :

```
SELECT *
FROM Employee
NATURAL JOIN Department;
```
f both have `deptID`, join automatically on `deptID` (no need to write `ON`).