**ER Mapping** is the process of converting an **Entity-Relationship (ER) Diagram** into a **set of relational tables**.

Each entity, attribute, and relationship from your ER model gets converted into appropriate **tables (relations)**, **columns (attributes)**, and **keys (constraints)** in the database.


---
#### Step 1: Map Strong Entities

For each **strong entity** in your ER diagram:
- Create a **table** with the same name as the entity.
- Each **simple attribute** becomes a **column**.
- Choose the **primary key** of the entity as the **primary key** of the table.

Example:
```
Entity: STUDENT(StudentID, Name, Major)
```

Mapped Table:
```
STUDENT(
  StudentID PRIMARY KEY,
  Name,
  Major
)
```


---
#### Step 2: Map Weak Entities

A **weak entity** depends on a **strong entity**, and it usually has a **partial key**.

For each weak entity:
- Create a **separate table**.
- Include **all its attributes**.
- Add the **primary key of its owning strong entity** as a **foreign key**.
- The **primary key** of the weak entity’s table is the **combination** of the foreign key and its partial key.

**Example:**
```
Weak Entity: DEPENDENT(Name, Age)
Owner Entity: EMPLOYEE(EmpID, Name)
```

Mapped Table:
```
EMPLOYEE(
  EmpID PRIMARY KEY,
  Name
)

DEPENDENT(
  EmpID,
  DependentName,
  Age,
  PRIMARY KEY (EmpID, DependentName),
  FOREIGN KEY (EmpID) REFERENCES EMPLOYEE(EmpID)
)
```


---
#### Step 3: Map Relationships

**(a) One-to-One (1:1)**
You can map a **1:1 relationship** by adding a **foreign key** to either (or both) of the tables.

**Example:**
```
EMPLOYEE(EmpID, Name)
PARKING_SPACE(SpaceID, Location)
Relationship: Each employee is assigned one parking space.
```

Mapped Tables:
```
EMPLOYEE(
  EmpID PRIMARY KEY,
  Name,
  SpaceID UNIQUE,
  FOREIGN KEY (SpaceID) REFERENCES PARKING_SPACE(SpaceID)
)
```


**(b) One-to-Many (1:N)**
Place the **foreign key on the "many" side"** of the relationship.

Example:
```
DEPARTMENT(DeptID, DeptName)
EMPLOYEE(EmpID, Name)
Relationship: One department has many employees.
```

Mapped Table:
```
DEPARTMENT(
  DeptID PRIMARY KEY,
  DeptName
)

EMPLOYEE(
  EmpID PRIMARY KEY,
  Name,
  DeptID,
  FOREIGN KEY (DeptID) REFERENCES DEPARTMENT(DeptID)
)
```


**(c) Many-to-Many (M:N)**
Create a **new table** (called a **bridge** or **junction table**) to represent the relationship.

Example:
```
STUDENT(StudentID, Name)
COURSE(CourseID, Title)
Relationship: Students enroll in courses.
```

Mapped Table:
```
STUDENT(
  StudentID PRIMARY KEY,
  Name
)

COURSE(
  CourseID PRIMARY KEY,
  Title
)

ENROLLMENT(
  StudentID,
  CourseID,
  Grade,
  PRIMARY KEY (StudentID, CourseID),
  FOREIGN KEY (StudentID) REFERENCES STUDENT(StudentID),
  FOREIGN KEY (CourseID) REFERENCES COURSE(CourseID)
)
```


---
#### Step 4: Map Multivalued Attributes

For **multivalued attributes** (those that can have multiple values for one entity), create a **new table**.

**Example:**
```
Entity: EMPLOYEE(EmpID, Name, PhoneNumber)
PhoneNumber is multivalued.
```

Mapped Table:
```
EMPLOYEE(
  EmpID PRIMARY KEY,
  Name
)

EMPLOYEE_PHONE(
  EmpID,
  PhoneNumber,
  PRIMARY KEY (EmpID, PhoneNumber),
  FOREIGN KEY (EmpID) REFERENCES EMPLOYEE(EmpID)
)
```


---
#### Step 5: Map Derived Attributes

**Derived attributes** are _not stored_ directly in the database, they are **computed when needed**.

**Example:**
```
Age = CurrentDate - DateOfBirth
```

No new column for `Age`, just compute it in queries when required.


---
#### Step 6: Map Composite Attributes

For **composite attributes**, you store each **component attribute** as a separate column.

**Example:**
```
Address = {Street, City, State, Zip}
```

Mapped Table:
```
CUSTOMER(
  CustomerID PRIMARY KEY,
  Street,
  City,
  State,
  Zip
)
```


---
#### Summary 

|ER Concept|Relational Mapping Rule|
|---|---|
|Strong Entity|Create a table with its attributes|
|Weak Entity|Create a table with owner’s PK + partial key|
|1:1 Relationship|Add FK to either entity|
|1:N Relationship|Add FK to "many" side|
|M:N Relationship|Create a separate relation|
|Multivalued Attribute|Create a separate relation|
|Derived Attribute|Do not store; compute as needed|
|Composite Attribute|Store individual components|
