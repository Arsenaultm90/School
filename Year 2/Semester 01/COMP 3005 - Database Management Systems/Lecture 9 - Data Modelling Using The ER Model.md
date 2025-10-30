**Data modelling** is the process of creating a _conceptual representation_ of the data and how it relates to other data.  
It helps you structure data logically before implementing it in a database.

Think of it as designing a **blueprint** for your database, just like an architect designs a building before construction.

The **Entity-Relationship (ER) Model**, introduced by _Peter Chen in 1976_, is a **high-level conceptual model** used to describe data and their relationships in a system.

The ER model is typically represented by an **ER diagram**, which uses symbols to represent:
- **Entities** → things or objects in the system
- **Attributes** → properties of those entities
- **Relationships** → associations between entities

**Advantages of the ER Model**:
- Provides a **clear conceptual structure**  
- **Easy to communicate** between developers and stakeholders  
- Helps during **database normalization and design**  
- Simplifies **conversion** into relational tables


---
#### Entities

An **entity** is any object in the real world that can be identified and stored in the database.

**Types of Entities:**
- **Strong Entity**: Exists independently (e.g., `Student`, `Employee`).
- **Weak Entity**: Depends on another entity for existence (e.g., `Dependent`, `InvoiceItem`).

**Example:**
`Student`, `Course`, and `Department` could be entities in a university database.

In ER diagrams:
- Entities are represented by **rectangles**.


---
#### Attributes

An **attribute** describes a property or characteristic of an entity.

| Type            | Description                             | Example                            |
| --------------- | --------------------------------------- | ---------------------------------- |
| **Simple**      | Cannot be divided further               | `Name`, `Age`                      |
| **Composite**   | Can be divided into sub-parts           | `FullName → {FirstName, LastName}` |
| **Derived**     | Can be calculated from other attributes | `Age` (derived from `DateOfBirth`) |
| **Multivalued** | Can have multiple values                | `PhoneNumber`, `Email`             |
In ER diagrams:
- Attributes are represented by **ellipses (ovals)** connected to their entity.


---
#### Relationships

A **relationship** represents an association between two or more entities.

Example:
A `Student` **enrolls in** a `Course`.

Types of Relationships (Based on Cardinality):

|Type|Description|Example|
|---|---|---|
|**One-to-One (1:1)**|One entity is related to only one other|`Person` ↔ `Passport`|
|**One-to-Many (1:N)**|One entity relates to many others|`Department` → `Employees`|
|**Many-to-Many (M:N)**|Many entities relate to many others|`Students` ↔ `Courses`|
In ER diagrams:
- Relationships are represented by **diamonds** connecting related entities.


---
#### Keys

Keys are attributes that help **uniquely identify** an entity.

Common Types:

|Key Type|Description|Example|
|---|---|---|
|**Primary Key**|Uniquely identifies each record|`StudentID`, `EmployeeID`|
|**Candidate Key**|A possible choice for primary key|`Email`, `PhoneNumber`|
|**Foreign Key**|References the primary key of another table|`DeptID` in `Employee` refers to `Department`|


---
#### Weak Entities and Identifying Relationships

A **weak entity** cannot be identified without another (strong) entity.

Example:
- `OrderItem` depends on `Order`.
- It has a **partial key** (e.g., `ItemNo`) and an **identifying relationship** connecting it to its owner (`Order`).

In ER diagrams:
- Weak entities use **double rectangles**.
- Identifying relationships use **double diamonds**.


---
#### ER Diagram Example

**Scenario:**  
A university wants to track which students enroll in which courses.

**Entities:**
- `Student (StudentID, Name, Major)`
- `Course (CourseID, Title, Credits)`

**Relationship:**
- `Enrolls` (between `Student` and `Course`)

**Cardinality:**
- A student can enroll in many courses
- A course can have many students  
    → **Many-to-Many relationship**

ER Diagram (conceptually):
```
[STUDENT]──<ENROLLS>──[COURSE]
   |                     |
 (StudentID)         (CourseID)
```

To implement this in a database, we’d need a **junction table** (like `Enrollment(StudentID, CourseID, Grade)`).


---
#### Converting ER Model to Relational Model

Once you finalize the ER diagram, you can **map it into tables**:

Example (University DB):
```
STUDENT(StudentID, Name, Major)
COURSE(CourseID, Title, Credits)
ENROLLMENT(StudentID, CourseID, Grade)
```

Here, `ENROLLMENT` resolves the many-to-many relationship.