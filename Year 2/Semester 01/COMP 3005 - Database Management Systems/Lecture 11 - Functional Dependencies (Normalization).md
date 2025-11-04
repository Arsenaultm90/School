A **functional dependency (FD)** is a relationship between **two sets of attributes** in a **relation (table)**.

It describes how **one attribute (or a group of attributes)** uniquely determines another.

**Formal Definition:**
Let **R** be a relation (table).  
A **functional dependency X → Y** means:

> For any two tuples (rows) _t₁_ and _t₂_ in R,  
> if _t₁[X] = t₂[X]_, then _t₁[Y] = t₂[Y]_.

In simple terms:  
If two rows have the same values for **X**, they must also have the same values for **Y**.


---
#### Normalization

**Normalization** is the process of **organizing data** in a database to:
- Eliminate **redundancy** (duplicate data)
- Prevent **update anomalies**
- Ensure **data integrity**

It’s based on analyzing **functional dependencies** between attributes and breaking large, unstructured tables into smaller, related ones.

Normal Forms (1NF → 5NF)
Each **Normal Form (NF)** builds on the previous one.

##### 1NF – _First Normal Form_
**Rule:**
- Each cell should contain **atomic (indivisible)** values.
- No **repeating groups** or arrays.
- Each record must be **unique** (identified by a key).

Example:
**Not NF**:

|StudentID|Name|Courses|
|---|---|---|
|1|Alice|Math, English|
|2|Bob|Physics|
**NF**:

| StudentID | Name  | Course  |
| --------- | ----- | ------- |
| 1         | Alice | Math    |
| 1         | Alice | English |
| 2         | Bob   | Physics |

##### 2NF – _Second Normal Form_
**Rule:**
- Must be in **1NF**
- **No partial dependencies** — i.e., no non-key attribute should depend on **part of a composite key**

 Applies **only** when the table has a **composite primary key**.

##### 3NF – _Third Normal Form_
**Rule:**
- Must be in **2NF**
- **No transitive dependencies**  
    (Non-key attributes should not depend on other non-key attributes)

A **transitive dependency** occurs when:
> A non-key attribute depends on another **non-key attribute**, not directly on the primary key.

Formally:  
If  `A → B` and `B → C`, then **A → C** is a _transitive dependency_.

