An **Algorithm** is a sequence of steps that was designed to accomplish a specific task.
Computer programming is a representation of these algorithms.
Algorithms can inform a choice of programming language.

Example: Quicksort
	Quicksort algorithm is a "**Divide-And-Conquer**" problem solving heuristic.


---

##### **Greedy Algorithms**
Greedy algorithms always choose the next step by what looks best from the current state.
	In Overview, the Steps to a Greedy Algorithm are:  
	1. Selection Procedure  
	2. Feasibility Test  
	3. Solution Check  
	
i.e., the Greedy Algorithm Chooses (as a Next Step) the  First Thing it Can Consider that Does Not invalidate  the solution, and stops as early as it can.

The **Greedy** approach is often not Ideal because it only considers what it can "Achieve" immediately, and not what will happen in the future greedy algorithms remain useful because they can often be used to find a "viable" Solution...  
	...Even if it is Not the "Best" Solution


---

##### **Hill Climbing Algorithms**
The **hill climber algorithm** is a **heuristic optimization algorithm** inspired by the idea of climbing uphill to find the highest peak. It's a simple, iterative algorithm used to solve optimization problems by incrementally improving the current solution. Hill climbing is particularly useful for problems where the search space is large and finding the global optimum is computationally expensive.

**Key Concepts**
1. **State Space**: The set of all possible solutions to the problem.
2. **Objective Function**: A function that evaluates how "good" a particular solution is (e.g., height of the hill). The goal is to maximize (or minimize) this function.
3. **Neighboring Solutions**: Slightly modified versions of the current solution, often generated by making small changes to it.

**How It Works**
1. **Start with an initial solution** (often randomly chosen).
2. **Evaluate the solution** using the objective function.
3. **Generate neighboring solutions** by making small changes to the current solution.
4. **Select the best neighboring solution**.
    - If it improves the objective function, move to that solution and repeat the process.
    - If no improvement is possible, stop (you've reached a local optimum).

**Example**
Suppose you want to maximize the function $f(x) = -x^2 + 4x + 6$.

1. **Initial Solution**: Start at $x=0,\; f(0)=6$.
2. **Generate Neighbours**: Try $x=1 (f(1)=9)$ and $x=−1 (f(−1)=3)$.
3. **Choose the Best Neighbour**: Move to $x=1$ since $f(1)=9$.
4. **Repeat**: Evaluate neighbours of $x=1$, e.g., $x=2$, and continue until no improvement is found.