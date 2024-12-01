A set is countable if there is a **Bijection** between that set and the set of all **Natural Numbers** (ℕ).
	Note: Bijection meaning Injective(One-To-One) & Surjective(Onto)

**Trivially Countable**
	Finite sets of numbers being mapped to by a subset of ℕ.
	The cardinality of the subset it equal to the cardinality of the finite set for Bijectivity.

**Countably Infinite**
	Equivalent to mapping ℕ $\rightarrow$ ℝ

**Programming Analogy**
	Formal Definition: $f(n): ℕ \rightarrow S$
		$n$ : Element in the set of ℕ
	ℕ = {1, 2, 3, 4, ...}
	ℤ = {..., -3, -2, -1, 0, 1, 2, 3,...}
	
```
	def f(n):
	    if n == 1:
	        return 0  # Special case for 0
	    elif n % 2 == 0:
	        return n // 2  # For even n, map to positive integers
	    else:
	        return -(n // 2)  # For odd n, map to negative integers
```

which is equivalent to saying:
	$f(n) = \begin{cases} 0, & \text{if } n = 1 \\\frac{n}{2}, & \text{if } n \text{ is even} \\-\frac{n-1}{2}, & \text{if } n \text{ is odd and } n > 1\end{cases}$ 


---

**Uncountable Sets**
	A set is larger than ℕ(Such as ℝ)
	There is no Bijection between a set and ℕ

Example:
	The numbers between 0 - 1 (ℝ) is uncountably infinite
	The reason is that ℝ has a large infinity than ℕ due to the fact that is it infinite in both the **Cardinality** of the set and the **Density** of the real numbers.

**Cantor's Diagonalization Argument**
The essence of Cantor's argument is that even if you attempt to list all the real numbers between 0 and 1, you can always construct a new real number that is **not** in the list, thus proving that the list cannot be complete. This is done by constructing a number that differs from every number in the list at least in one decimal place.

ℝ As An Uncountable Set
	ℝ contains infinities in both the **Cardinality** and **Density**. That is to say, any list of real numbers will always be missing values because it will always have new values between the existing values. 
	$\{0.1, 0.2, 0.3, 0.4, ...\}$
	$\{0.1, 0.11, 0.12, 0.13, ...\}$
	$\{0.1, 0.111, 0.112, 0.113, ...\}$

Irrational Numbers are also uncountable sets. 

