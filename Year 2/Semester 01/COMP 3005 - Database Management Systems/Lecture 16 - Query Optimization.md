Query optimization is basically the DBMS’s “brain” that figures out **how** to run your SQL query as fast as possible, without changing _what_ it does.


When you send an SQL query to a DBMS, roughly this happens:
1. **Parser**
    - Checks syntax (`SELECT`, `FROM`, etc. correct)
    - Checks semantics (tables & columns exist, types match)

2. **Query Rewrite / Logical Optimization**
    - Converts SQL into a **logical plan** (relational algebra tree)
    - Applies equivalence rules to improve the logical plan (but keeps same result)

3. **Physical Optimization / Plan Generation**
    - Chooses:
        - **Join order** (which tables to join first)
        - **Physical operators** (Hash join vs Nested loop vs Merge join, etc.)
        - **Access paths** (Index scan vs Sequential scan)
    - Estimates the **cost** of different plans using statistics
    - Picks the cheapest plan

4. **Execution Engine**
    - Runs the chosen plan and returns rows.



---
### Step 1: Parsing and initial logical plan
- SQL is turned into a **parse tree**.
- Then into a **logical query tree** using relational algebra:  
    Operators like `σ` (selection), `π` (projection), `⨝` (join), `×` (Cartesian product), `∪`, `∩`, etc.

For example:
```
SELECT s.name
FROM Student s
JOIN Enroll e ON s.sid = e.sid
JOIN Course c ON e.cid = c.cid
WHERE s.gpa > 3.5 AND c.dept = 'CS';
```

Initial logical plan might be:
- Start with Cartesian products + selection:
    - `σ (s.gpa > 3.5 AND c.dept = 'CS' AND s.sid = e.sid AND e.cid = c.cid) (Student × Enroll × Course)`

Then converted to joins:
- `σ (s.gpa > 3.5 AND c.dept = 'CS') ((Student ⨝ s.sid = e.sid Enroll) ⨝ e.cid = c.cid Course )`

This is a **logical plan**: it says _what_ operations are done, not _how_.


### Step 2: Logical optimization (query rewrite)
The optimizer applies **algebraic rules** that produce equivalent queries but potentially cheaper to execute.

Typical **heuristics**:
1. **Predicate pushdown (selection pushdown)**  
    Push `WHERE` conditions as close as possible to the base tables.
    
    From:
    - `σ (s.gpa > 3.5 AND c.dept = 'CS') (Student ⨝ Enroll ⨝ Course)`
    
    To:
    - `(σ s.gpa > 3.5 (Student)) ⨝ Enroll ⨝ (σ c.dept = 'CS' (Course))`
    
    Why? Because you:
    - Filter `Student` first ⇒ fewer `Student` rows go into the join
    - Filter `Course` first ⇒ fewer `Course` rows

2. **Projection pushdown**  
    Remove unused columns early.
    
    Our query only needs `s.name` in final output, but `sid`, `dept`, etc. are only needed for joins/filters. The optimizer adds `π` (projection) operators to drop unnecessary columns as early as possible. Smaller rows = fewer bytes to move and sort.
    
3. **Join reordering (associativity & commutativity)**  
    Joins are associative and commutative (under usual conditions), so:
    - `(Student ⨝ Enroll) ⨝ Course`
    - `Student ⨝ (Enroll ⨝ Course)`
    - `Course ⨝ (Enroll ⨝ Student)`
    
    all give the same result, but costs can be wildly different.
    
4. **Subquery flattening**  
    Turn some subqueries into joins or `IN`/`EXISTS` into semi-joins. (Not in our small example, but common.)
    
5. **Eliminate redundancy**
    - Remove duplicate predicates
    - Remove unnecessary joins (e.g., joining to a table that doesn’t affect output)

After logical optimization, we still have a **logical** plan, but much “leaner” and more selective early on.


### Step 3: Physical optimization (plan enumeration)
Now the optimizer must decide:
1. **Join order**  
    Which table goes first, second, third?

2. **Access path** for each table
    - Full table scan?
    - Index scan (range, equality)?
    - Index-only scan?

3. **Join methods**
    - **Nested loop join** (simple, good if one input is small & we have index on other)
    - **Hash join** (good for large joins, require hashing both sides)
    - **Sort–merge join** (good if both sides are already sorted or can be sorted cheaply)

The optimizer explores many combinations (search space) and uses **cost estimates** to pick one.


### Step 4: Cost estimation
The optimizer uses **statistics** such as:
- Number of rows (cardinality) in each table
- Number of pages (disk blocks)
- Distribution of values (histograms) for columns
- Selectivity of predicates (e.g., `gpa > 3.5` selects maybe 10% of students)

Typical cost model (simplified):
- Cost ≈ estimated **I/O cost** (page reads/writes) + maybe CPU cost
- For a table:
    - Full scan cost ≈ number_of_pages
    - Index scan cost ≈ index_height + expected_qualifying_rows * cost_per_row

For a join:
- Cost depends on chosen join algorithm + sizes of inputs.

The optimizer recursively estimates the size of intermediate results and computes the cost of each candidate plan.


### Step 5: Choose the best plan
The plan with lowest estimated cost is chosen as the **execution plan**.  

This is often represented as a tree of physical operators (e.g., IndexScan → HashJoin → Projection).


