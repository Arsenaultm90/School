## Instructions

**Objective:** Students are tasked with designing a system similar to _Relax_ that can accept text representing relations and relational algebra queries, then execute and display the results.

---

### Background and Guidance

Before starting this project, you should first practice writing and executing relational algebra queries using the [Relax](https://dbis-uibk.github.io/relax/calc/local/uibk/local/0) system. This practice will give you a strong foundation in how queries are expressed and executed in relational algebra. Try defining relations, running selections, projections, joins, and set operations, and observing the results.

Once you are comfortable with Relax, the next step is to deepen your understanding by attempting to implement a simplified system of your own. In essence, your system should be able to accept text that describes **relations** (tables) and **queries**, just like Relax. Behind the scenes, the system must include a **parser** that:

- Reads the relation definition in text form and converts it into a suitable internal data structure (e.g., lists, dictionaries, or classes).
- Parses the relational algebra query and maps it into a sequence of **ordered operations** (selection, projection, join, union, etc.).

After parsing, the system should **execute these operations one by one**. For example, a query such as `σAge > 30(Employees)` should be broken down into an operation call like `select(Employees, Age > 30)`, which filters rows. A join query would translate into another call such as `join(Relation1, Relation2, condition)`. In other words, your task is to _convert algebraic expressions into an execution plan_ and then implement each operation from scratch.

Importantly, your system must also be able to handle **multiple operations applied in sequence** as well as **nested operations**. For instance:

- A sequential query like `πName(σAge > 30(Employees))` should first run the selection to filter rows, then run the projection to reduce columns. In execution-plan form, this would look like:  
    `temp1 = select(Employees, Age > 30)`  
    `result = project(temp1, ["Name"])`

Through these examples, you can see that relational algebra queries are not limited to single operations. Your parser should be able to map queries into _an ordered tree or sequence of function calls_ and your system should correctly execute them step by step.

**Important:** You must not rely on ready-made data processing libraries such as `pandas` in Python for filtering, projection, or joins. Instead, you should manually implement these operations using core programming constructs (loops, conditionals, data structures). This will help you better understand how relational algebra operations are carried out at a fundamental level.

---

### 1. Example: How the System Works

To better understand what you need to build, let’s walk through how your system should operate on an example input. Suppose the user provides a relation and a query as plain text:

```javascript

// Input text provided by the user
Employees (EID, Name, Age) = {
  E1, John, 32
  E2, Alice, 28
  E3, Bob, 29
}

Query: select Age > 30 (Employees)
    
```

|Step|What the system does|
|---|---|
|Parsing Relations|Reads the text `Employees(...)` and creates a data structure such as a list of rows or a dictionary keyed by attributes.|
|Parsing Query|Identifies the operation `select`, the condition `Age > 30`, and the target relation `Employees`.|
|Execution Plan|Maps the query into a function call like `select(Employees, Age > 30)`.|
|Execution|Applies the filter on the `Employees` relation to produce the result.|

---

### 2. Example Output

Once executed, the system displays the result of the query:

```javascript

// Result after execution
Employees = {EID, Name, Age
  "E1", "John", 32
}
    
```

|EID|Name|Age|
|---|---|---|
|E1|John|32|

**Explanation:** The system takes plain text input, converts it into structured data, parses the query into an ordered function call, and executes the operation step by step. The final output is shown both as text and as a table for clarity.

---

### 3. Project Requirements

- Your system must be general — it should work for any valid relation and query input, not only for fixed hard-coded examples.
- Support at least the following relational algebra operations:
    - Selection (σ)
    - Projection (π)
    - Join (⋈)
    - Set operations (⋃, ∩, −)
- All operations must be implemented from scratch without using data-processing libraries such as `pandas`.
- Work must be done individually (no groups).

---

### 4. Deliverables

- **Code:** Upload your implementation to GitHub and submit the repository link on Brightspace.
- **Video:** Record a short video (about 5 minutes) demonstrating your system:
    - Show the system running with different queries.
    - Briefly explain how your code is structured (at a high level).
    - Point out key functions and how they work together.

---

### 5. Grading

- I will personally grade all submissions (no TAs involved).
- Correctness, completeness, and clarity of your implementation and video explanation will determine your score.

---

### 6. Points and Benefits

This project is worth **5 extra points**. There is no penalty for not submitting, but completing it can help you recover points lost in assignments or the final project. _**It is expected that only a few students will successfully submit this assignment. This is a challenging task, and it is completely fine if you decide not to do it.**_

---

### 7. Deadline

You have **1 week** to complete this project.

---

### 8. Important Note

You may use ChatGPT or other resources for guidance, but you must understand your code. During grading, I may ask questions to confirm your understanding.