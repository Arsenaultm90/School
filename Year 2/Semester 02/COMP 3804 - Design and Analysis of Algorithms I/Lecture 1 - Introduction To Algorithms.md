# Algorithm

Finite sequence of steps that transforms an input into an output.


We want it to :
	Terminate
	Be correct
	Be Efficient
		- Estimate running time
		- Count # of steps
		- As function of input length
	Pseudocode, no programming


Types of algorithm designs :
	Divide and Conquer
	Dynamic Programming
	Graph Algorithms
	P versus NP


**Example :**
**Fibonacci**
$$\displaylines{F_{0} = 0 \\ F_{1} = 1 \\ \text{if } n \geq 2 : F_{n} = F_{n-1} + F_{n-2}}$$

Algorithm fib(n)
```
if n <= 1 : return n
else : return 
	fib(n-1) + fib(n-2)
```

Running Time
T(n) = # of steps when running fib(n)

T(0) = 2
	Step 1 : Comparison
	Step 2 : Return value

T(1) = 2 (Same steps as T(0))

For larger values of n, there are two recursive invocations of fib1, taking time
T(n− 1) and T(n− 2), respectively, plus three computer steps (checks on the value
of n and a final addition). Therefore,
$$T(n)= T(n− 1) + T(n− 2) + 3 \text{ for n }  > 1$$

$Fn ≈ 2^{0.694n}$

To compute F(200), the fib1 algorithm executes $T(200) ≥ F(200) ≥ 2^{138}$ elementary computer steps.


### **Elementary Computer Steps**
- Assigning a variable  
    `x = 5`
- Comparing two values  
    `if (n <= 1)`
- Arithmetic on fixed-size values  
    `a + b`, `i++`
- Accessing an array element  
    `A[i]`
- Returning a value  
    `return x`



### Polynomial Algorithm
An algorithm is **polynomial-time** if its running time can be written as:
$$T(n) = O(n^k) \quad \text{for some constant } k$$

**Function fib2(n)** :
```
if n = 0: return 0

create an array f[0. . . n]
f[0]= 0, f[1]= 1

for i= 2 . . . n:
	f[i]= f[i− 1] + f[i− 2]
	
return f[n]
```

fib2 is linear with respect to n.

$O(n)$ in Unit-Cost RAM Model
$O(n^2)$ in Bit-Cost Model



---
# Big-O Notation (Asymptotic Analysis)

Asymptotic analysis is **a comparison between growth rates**.

When we write:
```
T(n) = O(n log n)
```

We are saying:
> “T(n) does not grow faster than n log n, up to a constant factor, for large n.”

So asymptotic notation is a **classification**.

#### Big O
f(n) ∈ O(g(n))

There exist constants $c>0$ and $n_{0}$ such that for all $n \ge n_0$​:
	f(n)≤c⋅g(n)

- `f` grows **no faster than** `g`
- We allow scaling by a constant
- We ignore small `n`



#### Big $\omega$
f(n) ∈ Ω(g(n))

There exist constants $c > 0$ and $n_0$ such that for all $n \ge n_0$​:
	$f(n) \ge c \cdot g(n)$

`f` grows **at least as fast as** `g`



### Theta (tight bound)
$f(n) \in \Theta(g(n))$

f(n) is both O(g(n)) **and** Ω(g(n))

So: $c_1 g(n) \le f(n) \le c_2 g(n)$



#### Bounds
Think of bounds as **growth envelopes**.
For large n, the function must lie:
- **Below** some curve → upper bound (Big-O)
- **Above** some curve → lower bound (Big-Ω)
- **Between** two curves → tight bound (Θ)

They describe **constraints on behaviour**.
> Big-O and Big-Ω differ when an algorithm’s running time cannot be tightly characterized by a single growth rate, due to input-dependent behaviour or incomplete bounds.

![[Screenshot 2026-01-24 at 11.09.26 AM.png]]



| Transition type                       | Pattern     |
| ------------------------------------- | ----------- |
| $(n \to n-1)$                         | linear      |
| $(n \to n/2)$                         | logarithmic |
| $(n \to k \in [1,n])$                 | harmonic    |
| $(n \to \text{multiple subproblems})$ | recurrence  |
- Deterministic → worst case
- Randomized → expected value

|Situation|Use|
|---|---|
|recursive split|Master Theorem|
|random jump to smaller state|harmonic expectation|
|unknown bounds|doubling + binary search|
|decreasing step sizes|amortized analysis|
