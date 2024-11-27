≤ is to Numbers as "Big O" is to Functions  
≥ is to Numbers as "Big Ω" is to Functions  
= is to Numbers as "Big 𝚯" is to Functions


---

#### Big O
Big-O notation describes the **asymptotic behaviour** of a function as x→∞. It gives an upper bound on the growth rate of a function. For f(x), the goal is to find a simple expression that grows at least as fast as f(x) for large x.

##### Definition:
$f(x) ∈ O(g(x))$ means there exists $c > 0$  and $k > 0$ such that:
	$f(x) ≤ c⋅g(x)$ for all $x ≥ k$.

##### Example: 
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

##### Example:
 $f(x) = x^2−2x+1$
 $g(x)=x^2$

We need to show: $x^2 − 2x + 1 ≥ c⋅x^2$ for all $x ≥ k.$

 1. Start with the inequality:
	$x^2−2x+1≥c⋅x^2$

 2. Rearrange terms:
	Bring all terms to one side:
	$x^2 − 2x + 1 − c⋅x^2 ≥ 0$
	
	Factor $x^2$ to simplify:
	$(1 − c) x^2 − 2x + 1 ≥ 0$

3. Focus on $(1 - c)x^2$:

	For the inequality to hold, $(1 − c)x^2$ must dominate the other terms $(−2x + 1)$ as $x → ∞$. 
	
	This happens if $c$ is chosen such that $1 − c > 0$, meaning:
	$c < 1$

4. Choose $c = 0.8$:

	Let $c = 0.8$ (a constant less than 1). Substitute this value:
	$(1−0.8)x^2 − 2x + 1 ≥ 0$
	
	Simplify:
	$0.2x − 2x + 1 ≥ 0$

5. Verify the inequality for large x:

	Factor x out of $0.2x^2−2x$ to better understand the growth:
	$x(0.2x−2) + 1 ≥ 0$
	
	For $x ≥ 10$, calculate:
	$0.2(10) − 2 = 2 − 2 = 0$
	
	When $x > 10$, $0.2x − 2 > 0$, so the term $0.2x^2$ dominates $−2x + 1$, making the inequality true.

6. Conclusion

	Since $0.2x^2 − 2x + 1 ≥ 0$ when $x ≥ 10$, we have shown that:
	$f(x) ≥ 0.8x^2$ for all $x ≥ 10$
	
	Therefore:
	$f(x) ∈ Ω(x^2)$ with $c = 0.8$ and $k = 10$.

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