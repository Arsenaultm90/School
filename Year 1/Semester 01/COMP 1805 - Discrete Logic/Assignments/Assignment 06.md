COMP 1805
Matthew Arsenault
101288386

![[Pasted image 20241128123012.png]]

$$\displaylines{\sum_{i=1}^{n}(\sum_{j=1}^{n}(\sum_{k=1}^{n}(i + j))) \\ \sum_{i=1}^{n}(\sum_{j=1}^{n}n(i+j)) \\
n\sum_{i=1}^{n}(\sum_{j=1}^{n}(i+j)) \\
n\sum_{i=1}^{n}\sum_{j=1}^{n}i + n\sum_{i=1}^{n}\sum_{j=1}^{n}j \\
First\; Term:n\sum_{i=1}^{n}\sum_{j=1}^{n}i = n\sum_{i=1}^{n}i·n 
= n^2(\frac{n(n+1)}{2}) = \frac{n^3(n+1)}{2} \\
Second\; Term: n\sum_{i=1}^{n}\sum_{j=1}^{n}j = n\sum_{j=1}^{n}j·n = n^2(\frac{n(n+1)}{2}) = \frac{n^3(n+1)}{2} \\
\frac{n^3(n+1)}{2} + \frac{n^3(n+1)}{2} \\
2(\frac{n^3(n+1)}{2}) \\
n^3(n+1) \\ 
∴ \sum_{i=1}^{n}(\sum_{j=1}^{n}(\sum_{k=1}^{n}(i + j))) = n^3(n+1)}
$$


<div style="page-break-after: always;"></div>
---


![[Pasted image 20241128130355.png]]
$$\displaylines{bar: \sum_{a=1}^{n=4565}1 + \sum_{c=1}^{a}a =
n + \frac{n(n+1)}{2} \\
foo: \sum_{b=1}^{a}a + \sum_{c=1}^{a}a = \frac{n(n+1)}{2} + \frac{n(n+1)}{2} = 2(\frac{n(n+1)}{2}) = n(n+1) \\\\
∴ foo : n(n+1) = 4565(4565 + 1) = 20843790 \\ bar: n + \frac{n(n+1)}{2} = 4565 + \frac{4565(4565+1)}{2} = 10426460}$$

<div style="page-break-after: always;"></div>
---

![[Pasted image 20241128134310.png]]
$$\displaylines{14x^2 - 22x + 7 \le c·x^2 \\
14x^2 -cx^2 - 22x + 7 \le 0 \\
(14 - c)x^2 -22x + 7 \le 0 \\ 
c = 15 \\
-x^2 - 22x + 7 \le 0 \\
x^2 + 22x - 7 \ge 0 \\
Finding\; Roots: \frac {-22 \pm \sqrt{22^2 -4(1)(-7)}} {2(1)} \\
We\; get: x = 0.314, x = -22.314\\
For \; the \; inequality\; to \; hold \; true:\; x \ge 0.314\\
For\; our\; upper\; bound\; let's\; choose: k=1\\
For\; any\; x \ge k,\; the\; term\; 14x^2\; grows\; much\; faster\; than\; -22x\; and\; 7.\\
Therefore,\; there\; exists\; a\; constant\; c=15\; such\; that\; for\; any\; x \ge k: \\
f(x) = 14x^2 - 22x + 7 \le c·x^2 = 15x^2\\
We\; conclude: f(x) = 14x^2 - 22x + 7\; is\; O(x^2)\; with\; c = 15,\; k = 1 }$$
<div style="page-break-after: always;"></div>
---


![[Pasted image 20241128145145.png]]
1. $\exists c > 0, n_{0} > 0 \; \forall n > n_{0}(7n^2 + 24n + 23log(n) - 17 \in O(n))$ Assumption
2. $7n^2 + 24n + 23log(n) - 17 \in O(n)$ (1)Universal Instantiation
3. $7n^2 + 24n + 23log(n) - 17 \le c·n$ (2)Definition
4. For large $n$,  $7n^2 + 24n + 23log(n) - 17 \approx 7n^2$ (2)Simplification
5. $7n^2 \le c·n$ (3)(4)Substitution
6. $7n \le c$ (3)Division by '$n$'
7. As $n \rightarrow \infty$, $7n = \infty$, $c$ is constant, $7n \le c$ cannot hold for large $n$
8. $7n^2 + 24n + 23log(n) - 17 \le c·n$ is $False$ for large $n$
9. $7n^2 + 24n + 23log(n) - 17 \notin O(n)$
10. $7n^2 + 24n + 23log(n) - 17 \notin O(n) \land 7n^2 + 24n + 23log(n) - 17 \in O(n)$ (2)(9) Conjunction
11. False (10) Complements Law

<div style="page-break-after: always;"></div>
---


![[Pasted image 20241128163842.png]]

$i)$ $f : A \rightarrow B$
$f(t) = c,\;\ f(e) = c,\;\ f(r) = o,\;\ f(m) = u,\;\ f(s) = l$ 
Injective:
	Using the definition $\forall x \; \forall y \; f(x) = f(y) \rightarrow x = y$:
	$f(t) = f(e) = c$, but $t \neq e$ 
	∴Not Injective
Surjective:
	Using the definition $\forall b \in B \;\ \exists a \in A \;\ f(a) = b$:
	There is no $a \in A$ where $f(a) = d$
	∴Not Surjective

$ii)$ $f : A \rightarrow B$
$f(t) = c,\;\ f(e) = o,\;\ f(r) = u,\;\ f(m) = l,\;\ f(s) = d$
Based on the definitions of **Injection** and **Surjection**, it is impossible to create a function that is **Surjective** and NOT **Injective** given the two sets. 
Since they are the same cardinality, if we make a function that is **Surjective**, it must be **Injective** by necessity.
Inversely, if we make the function NOT **Injective**, it can no longer be **Surjective** since the codomain will no longer have all of its elements mapped to by the domain. 
