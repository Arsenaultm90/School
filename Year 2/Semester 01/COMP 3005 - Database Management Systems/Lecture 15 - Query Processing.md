**Query processing** is the **sequence of steps** a DBMS takes to **interpret and execute** an SQL query efficiently.

It involves:
- Translating the high-level SQL query (what you type)
- Into a **low-level execution plan** (how the DBMS will do it)
- And then **executing** that plan to produce the result.

In short:
> Query Processing = SQL Query → Execution Plan → Result

| Phase                             | Description                                                                                   |
| --------------------------------- | --------------------------------------------------------------------------------------------- |
| 1. **Parsing and Translation**    | Checks syntax and converts SQL to an internal representation (like a parse tree)              |
| 2. **Optimization**               | Finds the most efficient way to execute the query (choosing join order, indexes, etc.)        |
| 3. **Evaluation Plan Generation** | Converts optimized logical operations into a physical execution plan (what algorithms to use) |
| 4. **Execution**                  | Actually runs the plan and retrieves the data                                                 |


---
#### Parsing and Translation

**Step 1: Parsing**
When you submit:
```
SELECT name FROM Students WHERE age > 20;
```

The **parser** checks:
- SQL **syntax** (is it valid SQL?)
- SQL **semantics** (do those tables and columns exist?)

If correct, it produces a **parse tree** — a tree representation of the query.
```
      SELECT
      /     \
   name     WHERE
              |
          age > 20
```


**Step 2: Translation**
The parse tree is translated into a **relational algebra expression**, like:
```
π_name (σ_age>20 (Students))
```
where:
- π = projection (select columns)
- σ = selection (filter rows)

This is a **logical representation** of what the query wants.


---
#### Query Optimization

The optimizer tries to find the **best (fastest, cheapest)** way to execute that logical query.

It uses:
- **Statistics** (table size, number of rows, distribution of values)
- **Indexes** (available B+ tree or hash indexes)
- **Possible join methods** (nested-loop, hash-join, merge-join)
- **Different query rewrites** (commutative and associative rules)


---
#### Evaluate Plan Generation

Now the DBMS decides **how exactly** to perform each operation.

For example:
- Should it do a **sequential scan** or **index scan**?
- Should it use a **hash join**, **merge join**, or **nested-loop join**?
- Should results be sorted using an **external sort** or an **in-memory sort**?

It maps each logical operator (like `σ`, `π`, or `⨝`) to a **physical operator**.


---
#### Query Execution

Finally, the DBMS executes the plan using the **execution engine**:
1. Read data blocks from disk (using indexes or scans)
2. Apply filters, joins, and sorting
3. Return the final result set to the user or application


---
#### Costs Analysis


**Cost for 'b' block transfers plus 'S' seeks:**
$$b \times t_{T} + S \times t_{S}$$

**Linear Search: $$t_{S} + b_{r} \times t_{T}$$**
**Linear Search, Equality on Key: $$t_{S} + 0.5b_{r} \times t_{T}$$**
**Primary B+-Tree Index, Equality on Key: $$(h_{i} + 1) \times (t_{T} + t_{s})$$**
**Sort-Merge: $$b_{r}(2 + \left[ \log_{m-1} \left( \frac{b_{r}}{M} \right) \right] + 1)$$**

