1. Select employees whose salaries are greater than $3000.
```
{t | t ∈ Employees ∧ t.SALARY > 3000}
```


2. Find the position of David.
```
{t.POSITION | t ∈ Employees ∧ t.NAME = 'David'}
```


3. Find the names of employees who are managers in the IT department.
```
{t.NAME | t ∈ Employees ∧
	t.POSITION = 'Manager' ∧ ∃s (s ∈ Departments ∧
	t.DEPTID = s.DEPTID ∧ s.DEPTNAME = 'IT')}
```


4. Each project is led by an employee. For projects with a budget greater than $1,000,000, show the project's budget and the details of the department (DeptID, DeptName, ManagerID) where the project lead is also the manager of their department.
```
{p.BUDGET, d.DEPTID, d.DEPTNAME, d.MANAGERID |
	p ∈ ProjectsTable ∧ p.BUDGET > 1000000 ∧
	∃s (s ∈ Employees ∧ s.EMPID = p.LEADEMPID ∧
	∃d (d ∈ Departments ∧ s.DEPTID = d.DEPTID ∧ s.EMPID = d.MANAGERID))}
```


5. List project names led by employees from the Finance department.
```
{p.PROJECTNAME | p ∈ ProjectsTable ∧
	∃e (e ∈ Employees ∧ e.EMPID = p.LEADEMPID ∧
	∃d (d ∈ Departments ∧ e.DEPTID = d.DEPTID ∧ d.DEPTNAME = Finance'))}
```

6. Show employee names alongside the names of the projects they lead, ignoring employees who do not lead any projects.
```
{e.NAME, p.PROJECTNAME | e ∈ Employees ∧
	∃p (p ∈ ProjectsTable ∧ e.EMPID = p.LEADEMPID)}
```


7. Select employees, showing only their id and name, who are not designated as managers in any department. Solve this query under the assumption that a 'position' attribute does not exist in the database.
```
{e.EMPID, e.NAME | e ∈ Employees ∧ 
	¬∃d (d ∈ Departments ∧ e.EMPID = d.MANAGERID)}
```
