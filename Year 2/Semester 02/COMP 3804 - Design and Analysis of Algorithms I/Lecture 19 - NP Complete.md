A problem X is **NP-complete** if it satisfies _both_ of the following conditions simultaneously:

**Condition 1: X is in NP**
This means: given a _candidate solution_, you can **verify** it is correct in polynomial time.

Note this is about verification, not solving. You're not claiming you can _find_ a solution quickly — just that if someone hands you one, you can check it quickly. The "witness" or "certificate" is the candidate solution.

For example, with Independent Set: if someone gives you a set S of vertices, you can verify in polynomial time that no two vertices in S share an edge. You just check every pair in S — that's O(k²) work.


**Condition 2: X is NP-hard**
This means: **every problem in NP reduces to X in polynomial time.**

Formally: for every problem Y in NP, Y ≤ₚ X.

This is saying X is at least as hard as _every single problem_ in NP. If you could solve X efficiently, you could solve all of NP efficiently.

**NP-complete = NP ∩ NP-hard**
In other words, NP-complete problems are the **hardest problems inside NP** — they're in NP (solutions are checkable), and everything else in NP reduces to them (so they're as hard as anything in NP could possibly be).


#### How You Actually Prove NP-Completeness in Practice
Because reduction is **transitive** — if A ≤ₚ B and B ≤ₚ C, then A ≤ₚ C — you only need to reduce _one_ known NP-complete problem to X. That single reduction chains back through the entire web to everything else.

So in practice the proof has exactly two steps:
1. Show X ∈ NP (describe a poly-time verifier)
2. Show Y ≤ₚ X for some already-known NP-complete problem Y

That's it. The transitivity of reductions handles the rest.



---
## Properties of Polynomial-Time Reductions

There are three core properties that make polynomial-time reductions well-behaved and useful. These are what allow the whole NP-completeness framework to hold together.

#### Property 1: Reflexivity
> Every problem reduces to itself: **A ≤ₚ A**

This is trivial but important for the framework to be logically consistent. The "reduction" is just the identity, pass the input straight through unchanged. It costs O(1) time, which is certainly polynomial.

#### Property 2: Transitivity
> If **A ≤ₚ B** and **B ≤ₚ C**, then **A ≤ₚ C**

This is the most important property in practice. It's what makes the entire NP-completeness web work.

If you can transform A into B in polynomial time, and transform B into C in polynomial time, then you can chain those two transformations together, first convert A to B, then convert that to C. The total time is polynomial + polynomial, which is still polynomial.

This is exactly why you don't need to reduce _every_ NP problem directly to your new problem X to prove NP-hardness. You just need one link in the chain, the transitivity property propagates hardness all the way back through the web automatically.

#### Property 3: Preservation of Hardness (the Contrapositive)
This one is less a standalone property and more the logical consequence that gives reductions their teeth. It comes in two directions:

**Forward direction (easiness transfers upward):**
> If **A ≤ₚ B** and B ∈ P, then A ∈ P

If B is easy and A reduces to B, then A is easy too — you just run the reduction and then run B's algorithm. Total time is still polynomial.

**Contrapositive (hardness transfers downward):**
> If **A ≤ₚ B** and A is NP-hard, then B is NP-hard

If A is hard and A reduces to B, then B must be at least as hard as A. This is the direction used in NP-completeness proofs, you take a known hard problem and reduce it _to_ your new problem, forcing your new problem to inherit the hardness.



---
## Circuit SAT

A **boolean circuit** is a directed acyclic graph (DAG) where:
- **Input nodes**: hold boolean values (true/false), these are your variables
- **Gate nodes**: compute logical operations on their inputs:
    - AND gate: outputs true only if all inputs are true
    - OR gate: outputs true if at least one input is true
    - NOT gate: flips its single input
- **One output node**: the final gate whose value is the circuit's result

Data flows in one direction from inputs through gates to the output. No cycles.

#### What is Circuit-SAT?
**Circuit Satisfiability (Circuit-SAT)** asks:
> Given a boolean circuit, is there an assignment of true/false to the input nodes that makes the output node evaluate to true?

That's it. You have a circuit, and you want to know if there's any combination of inputs that makes it output 1.

### Why Circuit-SAT Matters
Circuit-SAT is important for one key reason: **boolean circuits are essentially a model of computation itself.**

Any algorithm running on a computer is ultimately executing boolean operations on bits. A circuit is just a frozen, hardware-like snapshot of that computation. This means:
- Any problem whose solution can be _verified_ in polynomial time can be encoded as a polynomial-size boolean circuit
- That encoding is the key insight behind why Circuit-SAT is NP-complete.

#### Circuit-SAT is NP-Complete
This is the **Cook-Levin theorem** (1971), and it's the foundational result that the entire NP-completeness framework rests on. Every other NP-completeness proof ultimately traces back to this one.

Remember the two conditions needed:
1. Circuit-SAT ∈ NP
2. Circuit-SAT is NP-hard (every problem in NP reduces to it)

#### Condition 1: Circuit-SAT is in NP
This is the easy direction. Given a circuit and a candidate input assignment, you just:
- Feed each input its assigned value
- Propagate the signals forward through every gate in topological order
- Check whether the output is 1

Each gate is a constant-time operation, and a polynomial-size circuit has polynomially many gates. So verification runs in polynomial time.

#### Condition 2: Circuit-SAT is NP-hard
This is the hard direction, and the deep insight. We need to show that **every problem Y in NP reduces to Circuit-SAT in polynomial time.**

We can't do this one problem at a time, there are infinitely many problems in NP. Instead we use a single sweeping argument about what NP _means_.

#### The Core Argument
Pick any arbitrary problem Y in NP. Since Y ∈ NP, by definition there exists a polynomial-time **verifier** V such that:
> For any input x, x is a yes-instance of Y if and only if there exists a witness w where V(x, w) = 1

In other words, V is an algorithm that takes the input x and a candidate solution w, and outputs 1 if w is a valid solution.

Now here's the key move. V is an algorithm, it runs on a computer, and any computation that runs in polynomial time can be **simulated by a polynomial-size boolean circuit.** This is a standard result from computational theory: every step of a computation maps to a layer of gates, and polynomial steps means polynomial layers means polynomial circuit size.

So we can mechanically convert V into a circuit C where:
- The inputs to C are the bits of x (the problem instance) and the bits of w (the candidate witness)
- C outputs 1 exactly when V(x, w) = 1

Now fix x (the specific instance of Y you want to solve) and hardwire those bits into the circuit. What remains are the w input bits, the witness, which are free variables.

**The circuit C with x hardwired is satisfiable if and only if there exists a valid witness w, which is exactly when x is a yes-instance of Y.**

So we've reduced Y to Circuit-SAT. The construction of C from V takes polynomial time, and this works for _any_ Y in NP. Therefore Circuit-SAT is NP-hard.

![[Pasted image 20260409080516.png]]

