≤ is to Numbers as "Big O" is to Functions  
≥ is to Numbers as "Big Ω" is to Functions  
= is to Numbers as "Big 𝚯" is to Functions


---

#### Big O
Big-O notation describes the **asymptotic behaviour** of a function as x→∞. It gives an upper bound on the growth rate of a function. 
##### Definition:
$f(x) ∈ O(g(x))$ means there exists $c > 0$  and $k > 0$ such that:
	$f(x) ≤ c⋅g(x)$ for all $x ≥ k$.
$k$ - Upper bound, where the behaviour of the function will be dominated by the highest degree term.
$c$ - A constant that determine how loose or tight the upper bound is.

Saying $f(x)∈O(g(x))$ means that for large $x$, f(x) grows **no faster than** $g(x)$, up to a constant factor.

Proof:
$$\displaylines{f(x) = 3x^2 + 5x + 3\\
g(x) = c·x^2\\ \\
\text{Setup}\\
3x^2 + 5x + 3 \leq c·x^2\\ \\
\text{Set Upper Bounds}\\
3x^2 + 5x + 3 \leq 3x^2 + 5x^2 + 3x^2\\ \\
\text{Factor Terms}\\
3x^2 + 5x + 3 \leq (3 +5+3)x^2\\ \\
\text{Finalize}\\
3x^2 + 5x + 3 \leq 11x^2\\ \\
c = 11,\; k\geq 1\\
f(x)\; \text{is in}\;O(x^2) }$$ 
##### Example w/ Quadratic Equation (Tighter Bounds): 
$f(x)=3x2−20x+100$
$g(x) = x^2$

We want to show: $3x^2 - 20x + 100  ≤  c ⋅ x^2$ for all $x ≥ k$.

1. Start with the inequality:
		$3x^2 - 20x + 100  ≤ c · x^2$

2. Rearrange terms:
		$3x^2 - c · x^2 - 20x + 100 ≤ 0$
		
	Factor $x^2$ to simplify:
		$(3 - c)x^2 - 20x + 100 ≤ 0$

3. Choose 'c' and solve:
	Ensure $c > 3$
	The coefficient $(3−c)$ must be negative to make $x^2$ dominated by $c⋅x^2$, so $c > 3$.

	Analyze the Remaining Terms
	For large $x$, the $−20x + 100$ terms become negligible compared to $x^2$. To ensure the inequality holds for all $x ≥ k$, choose $c > 3$. A common choice is $c = 4$, which simplifies calculations.

4. Verify $c = 4$ for large $x$:
	Substitute c=4c = 4c=4 into the inequality:
	$(3 − 4)x^2 − 20x + 100 ≤ 0$

	Simplify:
	$−x^2 − 20x + 100 ≤ 0$

	Factor out −1:
	$x^2 + 20x − 100 ≥ 0$

	From here we can use the 'Quadratic Formula' to find the roots and look at the positive values to estimate a 'k' value that will satisfy the inequality. Other option is to estimate a 'k' value and test it with the inequality.

5. Conclusion
	With $c = 4$ and $k = 10$, we have shown that:
	$f(x) = 3x^2 − 20x + 100$ is $O(x^2)$



---


#### Big Ω
Big-Omega notation is used to describe the **lower bound** of a function's growth rate, meaning it tells us the **best-case scenario** or the **minimum growth rate** of a function as the input size n becomes very large.

##### Definition:
$f(x) ∈ Ω(g(x))$ means there exists $c > 0$  and $k ≥ 0$ such that:
	$f(x) ≥ c⋅g(x)$ for all $x ≥ k$.

Proof:$$\displaylines{
f(x) = 3n^2 + 2n + 4\\
g(x) = c·n^2 \\ \\
\text{Setup}\\
3n^2 + 2n + 4 \geq c·n^2\\ \\
\text{Drop Lower Terms}\\
3n^2 + 2n + 4 \geq 3n^2 \\ \\
c = 3\\
n_{0} = 0\\ \\
∴ f(x) = 3n^2 + 2n + 4 \in \Omega(n^2)}$$

---


#### Big 𝚯
Big-Theta (Θ) notation is used to describe a function's **tight bound**. It tells us that a function f(x) grows **at the same rate** as g(x) asymptotically. In other words, f(x) is "sandwiched" between two constant multiples of g(x) for sufficiently large x.

Definition:
We say that $f(x) ∈ Θ(g(x))$ if there exist constants $c_{1}, c_{2} > 0$  and $k > 0 such that:
$c_{1}⋅g(x) ≤ f(x) ≤ c_{2}⋅g(x)$ for all $x ≥ k$

This means:
1. f(x) grows **at least as fast as g(x) (Big-Ω).
2. f(x) grows **at most as fast as g(x) (Big-O).

For some $f(x)$, prove the Ω and O to assert that $f(x) ∈ Θ(x)$.