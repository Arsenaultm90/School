At its core, reduction is a way of saying: **"Problem A is at least as hard as Problem B"** — by showing that if you can solve A, you can automatically solve B.

More formally: **reducing problem B to problem A** means writing an algorithm that:
1. Takes an instance of B
2. Transforms it into an instance of A
3. Solves A
4. Translates the answer back to an answer for B

If this transformation takes polynomial time, we call it a **polynomial-time reduction**, written **B ≤ₚ A** (read: "B reduces to A" or "B is poly-time reducible to A").

#### How It Is Used
Reduction lets you reason about **hardness** without re-inventing the wheel:
- If **B ≤ₚ A** and A is easy (in P) → B is also easy
- If **B ≤ₚ A** and B is hard (NP-hard) → A is _at least_ as hard as B

This is how NP-completeness works. To show a new problem X is NP-complete, you:
1. Show X is in NP (a solution can be verified in polynomial time)
2. Take a _known_ NP-complete problem and reduce it to X
![[Pasted image 20260407082059.png]]


---
## The "Oracle" Mindset

When doing reductions, imagine you have a **magic black box (oracle)** that solves problem A instantly. Your job is just to:
- Encode your problem B into A's language
- Ask the oracle
- Decode the result

You're not implementing A, you're _assuming_ it's solved, and using that to solve B.

##### **Example: 3-SAT ≤ₚ Independent Set**
This is a classic textbook reduction used to prove Independent Set is NP-complete.

**3-SAT**: Given a boolean formula in Conjunctive Normal Form with 3 literals per clause, is there an assignment making it true? 
**Independent Set**: Given a graph G and integer k, is there a set of k vertices with no two connected by an edge?

**The reduction**:
For each clause (e.g. `x₁ ∨ ¬x₂ ∨ x₃`), create a **triangle** of 3 nodes, one per literal. Then add edges between **contradictory literals** across clauses (e.g. connect node `x₁` in one clause to node `¬x₁` in another).

Set k = number of clauses.

**Why it works**:
- Picking one node per triangle = choosing one literal to be true per clause
- The "contradiction edges" ensure you never pick `x₁` and `¬x₁` simultaneously
- So an independent set of size k ↔ a satisfying assignment of the formula

This shows that if you could solve Independent Set in polynomial time, you could solve 3-SAT in polynomial time, which would mean P = NP.

![[Pasted image 20260407084315.png]]
**Step 1** — Each clause becomes a triangle. The triangle edges mean you can only pick _one_ node per triangle (any two nodes in the same triangle are adjacent).
**Step 2** — Red dashed conflict edges connect every literal to its negation across triangles. These prevent contradictory choices.
**Step 3** — The valid independent set is highlighted. Notice no two green nodes share an edge (neither a triangle edge nor a conflict edge).