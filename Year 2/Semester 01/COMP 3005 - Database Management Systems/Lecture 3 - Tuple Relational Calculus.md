Tuple Relational Calculus (**TRC**) is a way of describing queries in relational databases, but instead of writing _how_ to get the data (like in SQL), you describe _what_ you want.

- **Non-procedural query language** (a kind of logic-based query language).
- You specify the **properties** the result should satisfy, not the sequence of steps to compute it.
- The “tuple” part means it’s expressed in terms of variables that represent **rows (tuples)** from relations (tables).

Relation = Table
Tuple = Row (Finite ordered list of items)
Attribute = Columns

---
#### RA To TRC

1. **Selection (σ)**
**RA:**
`σAge>30(Employee)

**TRC:**
`{t ∣ t ∈ Employee ∧ t.Age > 30}`


2. **Projection (π)**
**RA:**
`πName,Dept(Employee)π{Name,Dept}(Employee)πName,Dept​(Employee)`

**TRC:**
`{⟨t.Name, t.Dept⟩ ∣ ∃e ∈ Employee(t=e)}`
In TRC, we specify only the attributes we want (similar to projection in RA).


3. **Union (⋃)**
**RA:**
`Employee⋃ManagerEmployee ⋃ ManagerEmployee⋃Manager`

**TRC:**
`{t ∣ t ∈ Employee ∨ t ∈ Manager}`


4. **Set Difference (−)**
**RA:**
`Employee−ManagerEmployee − ManagerEmployee−Manager`

**TRC:**
`{t ∣ t ∈ Employee ∧ ¬(t ∈ Manager)}`


5. **Cartesian Product (×)**
**RA:**
`Employee×DepartmentEmployee × DepartmentEmployee×Department`

**TRC:**
`{⟨t,e⟩ ∣ t ∈ Employee ∧ e ∈ Department}`


6. **Rename (ρ)**
**RA:**
`ρEmp(Employee)ρ{Emp}(Employee)ρEmp​(Employee)`

**TRC:**  
Renaming isn’t a query itself in TRC, but we can represent it by using a different tuple variable:
	`{e ∣ e ∈ Employee}`
	
(where `e` is just an alias).


7. **Join (⋈)**
Say we want an **equi-join** on `Employee.DeptID = Department.DeptID`.

**RA:**
`Employee ⋈ Employee.DeptID = Department.DeptIDDepartment`

**TRC:**
`{t ∣ ∃e ∈ Employee ∃d ∈ Department(t.EmpID=e.EmpID ∧ t.DeptID=d.DeptID ∧ e.DeptID=d.DeptID)}`


---
#### Bound and Free Variables

1. **Free Variables**
- A variable is **free** if it is **not inside the scope of a quantifier** (`∃` or `∀`).
- Free variables determine what the query **returns**.
- In TRC/DRC, the **free variables** are the attributes/tuples you actually project into the result set.

Example :

```
{ t.Name | t ∈ Student ∧ t.Age > 18 }
```
- Here `t` is free because it’s not quantified by `∃` or `∀`.
- The query result will be the set of `Name` values for those `t`.


2. **Bound Variables**
- A variable is **bound** if it is inside the scope of a quantifier (`∃` or `∀`).
- Bound variables are like “temporary” variables used to express a condition.
- They don’t appear in the final output.

Example :

```
{ s.Name |
  s ∈ Student ∧
  ∃t ∈ Takes (s.id = t.sid ∧ t.cid = 'CS101')
}
```
- `s` is **free** → it’s in the result (student names).
- `t` is **bound** → it’s only used inside `∃` to check if `s` takes course CS101.

The output will only show student names (`s.Name`), not the `t` values.

