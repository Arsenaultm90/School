Allocation of resources is in a state where (there is a set of) two or more processes are waiting (indefinitely) for an event that can only be caused by one of the waiting processes (in the set).

---
#### **Necessary Conditions**
1. **Mutual exclusion:** only one thread at a time can use a resource.

2. **Hold and wait:** a thread holding at least one resource is waiting to acquire additional resources held by other threads.

3. **No preemption:** a resource can be released only voluntarily by the thread holding it, after that thread has completed its task.

4. **Circular wait:** there exists a set {T0, T1, ..., Tn} of waiting threads such that T0 is waiting for a resource that is held by T1, T1 is waiting for a resource that is held by T2, ..., Tn–1 is waiting for a resource that is held by Tn, and Tn is waiting for a resource that is held by T0.

All four conditions are necessary for deadlock, but not sufficient, because a system can satisfy all four conditions without currently being in a circular waiting cycle. Deadlock requires both the conditions + an actual unresolvable circular wait.

---
#### **Resource Allocation Graph**
V is partitioned into two types:  
1. T = {T1, T2, ..., Tn}, the set of all the threads in the system.  
2. R = {R1, R2, ..., Rm}, the set of all resource types in the system

**Request Edge** – directed edge $T_{i} \rightarrow R_{j}$
**Assignment Edge** – directed edge $R_{j} \rightarrow T_{i}$

If graph contains no cycles -> no deadlock  
If graph contains a cycle ->
	• if only one instance per resource type, then deadlock  
	• if several instances per resource type, possibility of deadlock

**Example :**
• One instance of R1  
• Two instances of R2  
• One instance of R3  
• Three instance of R4  
• T1 holds one instance of R2, waiting for an instance of R1  
• T2 holds one instance of R1, one instance of R2, and is waiting for an instance of R3  
• T3 is holds one instance of R3
![[Screenshot 2025-10-19 at 1.34.55 PM.png|300]]



---
#### **Methods For Handling Deadlocks**

##### Deadlock Prevention
Prevent at least one of the four conditions for deadlock from ever holding.

1. **Mutual exclusion**: Make resources sharable when possible (e.g. read-only files).
2. **Hold and wait**: Require processes to request _all_ resources at once before execution (but this reduces efficiency).
3.  **No preemption**: Allow the system to take away resources if needed (e.g. preempt CPU or memory).
4. **Circular wait**: Impose an ordering on resources (R1 < R2 < R3...) — processes must request resources in that order.

**Pro:** Guarantees deadlock never occurs.
**Con:** Often inefficient — leads to low resource utilization and starvation.


##### Deadlock Avoidance
Allow requests dynamically but make decisions so the system never enters an _unsafe_ state (where deadlock _could_ happen).

**Requires:**
- Each process to declare its **maximum resource needs** in advance.
- The OS to simulate (or check) each request before granting it, using an algorithm like the **Banker’s Algorithm**.

If granting the request keeps the system in a **safe state** (i.e., there exists some sequence of process completions), the OS proceeds; otherwise, it delays the request.

**Pro:** Allows more concurrency than prevention.

**Cons:**
	Requires knowing maximum needs in advance.  
	Overhead of frequent safety checks.  
	Not always practical.


##### Deadlock Detection
Don’t try to prevent or avoid deadlocks — just let them happen and **periodically check** if one exists.

The OS maintains a **Resource Allocation Graph (RAG)** or similar structure.
For each cycle detected:
    - If there’s one resource per instance → a cycle means a deadlock.
    - If resources have multiple instances → the system uses algorithms (like Banker’s) to check deadlocks.

**Pros:** Maximum resource utilization; no restrictions on requests.  

**Cons:**  
	Requires periodic checks (CPU overhead).  
	Must handle deadlocks _after_ they occur (by recovery).


##### Recovery From Deadlock
Once a deadlock is detected, **break** it using one of these strategies:

**a) Process Termination**
- Abort **all** deadlocked processes (simple but wasteful), or
- Abort **one at a time** until the deadlock is gone, using criteria like:
    - Priority
    - How long the process has run
    - How many resources it holds

**b) Resource Preemption**
- Take resources away from some process and give them to another.
- Must handle:
    - **Victim selection** (which process to take from)
    - **Rollback** (restore a process to a safe state)
    - **Starvation** (avoid constantly preempting the same process)

**Pros:** Works after-the-fact; flexible.  

**Cons:**  
	Can cause data loss or inconsistency.  
	Rollbacks are expensive.

| Method         | When Used        | How It Works                             | Pros                      | Cons                        |
| -------------- | ---------------- | ---------------------------------------- | ------------------------- | --------------------------- |
| **Prevention** | Before execution | Disallow one or more deadlock conditions | Simple                    | Inefficient                 |
| **Avoidance**  | During execution | Check for safe state before granting     | Safer, more flexible      | Requires advance info       |
| **Detection**  | After execution  | Look for cycles in resource graph        | High resource utilization | Must recover after deadlock |
| **Recovery**   | After detection  | Kill or preempt processes                | Resolves deadlocks        | Costly and disruptive       |


##### Resource Ordering
**Resource ordering** is a deadlock prevention technique where all resources are assigned a unique global order, and processes must request resources only in ascending order. This eliminates the possibility of circular wait, which is one of the four necessary conditions for deadlock. Resource allocation graphs visualize resource usage, but resource ordering is a separate, preventive strategy.

**Hold-And-Wait Starvation**
A process must acquire _all_ resources it needs simultaneously before it can run.  
If other processes repeatedly take one or more of those resources first,  
the process may never see _all_ of them available at the same time,  
causing it to wait indefinitely.

---
#### **Banker's Algorithm**

Banker’s Algorithm is a **deadlock avoidance** algorithm.
- It **checks** whether granting a resource request will leave the system in a **safe state**.
- If it’s safe → **grant the request**.
- If it would become unsafe → **deny (or delay)** the request.

It’s called the _Banker’s_ algorithm because a banker won’t loan out money unless they know they can satisfy all customers eventually.


**Safe State**
A state where there exists **some order** in which all processes can finish.
If the system can find _any_ sequence like:
```
P2 → P1 → P3 → P4
```
where each process can eventually get its maximum resources and complete,  
then the system is **safe**.


**Unsafe State**
Not the same as deadlocked.

Unsafe means:
- You _might_ deadlock in the future.
- The OS **avoids granting** the request that leads to unsafe states.


##### The Algorithm Uses 4 Tables (Matrices)
For `n` processes and `m` resource types:
1. **Max\[i][j]**
	Maximum demand of process i for resource j.

2. **Allocation\[i][j]**
	Current allocation to process i.

3. **Need\[i][j]**
	Remaining needs (calculated):
```
Need[i] = Max[i] – Allocation[i]
```

4. **Available\[j]**
	Resources currently available (not allocated).


Unknown Max entry
- Put `x` in `Max`
- Compute `Need`
- Run safety algorithm → inequalities in `x`
- Also enforce `Need ≥ 0` (so `Max ≥ Allocation`)
- Solve for `x` (usually a range).

Checking a given sequence
- Start `Work = Available`
- For each Pi in the sequence:
    - If `Need[i] ≤ Work`, update `Work += Allocation[i]`
    - Else → not a safe sequence
- Finish all? → sequence is safe.

Unknown Available component
- Put `X` inside `Available`
- Run safety algorithm → inequalities on `X`
- Combine them → get allowed range for X.


**Deadlock Detection Problems**
Allocation[i]
Requests[i] - Current outstanding requests
Available - Free Resources

