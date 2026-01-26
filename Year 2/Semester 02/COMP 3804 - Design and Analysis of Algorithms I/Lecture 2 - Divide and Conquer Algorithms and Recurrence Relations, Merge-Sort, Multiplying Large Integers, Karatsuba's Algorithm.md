
## Divide and Conquer

To solve problems of size 'n':
1. Divide into subproblems of size < n
2. Recursively solve subproblems
3. Combine solutions to subproblems

Note: Base case


#### Merge-Sort
Input sequence of length n.
	$\boxed{a_{1}, a_{2}, \dots, a_{n}}$
	$\boxed{a_{1}, a_{2},| \dots, a_{n}} = \boxed{\frac{n}{2} | \frac{n}{2}}$
	$\boxed{a_{1},| a_{2},| \dots,| a_{n}} = \boxed{\frac{n}{4} | \frac{n}{4} | \frac{n}{4} | \frac{n}{4} }$
	Divide until we reach the base case.
	Merge sorted arrays.

$T(n) = O(n logn)$
1. O(n)
2.  2 * T(n/2)
3. O(n)

$$T(n) \le \begin{cases}
c \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \text{ if n = 1} \\
cn + 2 * T\left( \frac{n}{2} \right) \ \ \text{ if n} \ge 2
\end{cases}$$
$$n = 2^k$$
Solve by **UNFOLDING**: Goal is to get rid of $T(n/2)$ on RHS
$T(n) \le n + 2\left[ \frac{n}{2} + 2* T\left( \frac{n}{4} \right) \right]$
$T(n) \le 2n + 2^2 * T\left( \frac{n}{2^2} \right)$
$T(n) \le 2n + 2^2\left[ \frac{n}{4} + 2 * T\left( \frac{n}{8} \right) \right]$
$T(n) \leq 3n + 2^3 * T\left( \frac{n}{2^3} \right)$
$\therefore T(n) \leq kn + 2^k * T\left( \frac{n}{2^k} \right)$

$T(n) \leq kn + n * T(1)$
	$n = 2^k, k = \log_{2}n$
	$T(1) = 1$
$T(n) \leq n \log n + n$




---
## Multiply Large Integers

$x, y$ : integers, n digits
$x + y : O(n)$
$10^n · x : O(n)$
$xy : O(n^2)$

$x, y$ : integers, in binary, n bits
$x = \boxed{ \frac{n}{2} | \frac{n}{2}} = 2^{n/2} · X_{L} + X_{R}$
$y = \boxed{\frac{n}{ 2} | \frac{n}{2}} = 2^{n/2} · Y_{L} + Y_{R}$

$xy = 2^n · X_{L}Y_{L} + 2^{n/2}[X_{L}Y_{R} + X_{R}Y_{L}] + X_{R}Y_{R}$
4 Subproblems:
$X_{L}Y_{L}$
$X_{L}Y_{R}$
$X_{R}Y_{L}$
$X_{R}Y_{R}$

 $T(n) =$ # of bit operations
$T(n) = O(n) + 4 · T\left( \frac{n}{2} \right) + O(n)$
$T(1) \leq c$

Unfolding:
$$T(n) \le \begin{cases}
1 \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \text{ if n = 1} \\
cn + 4 * T\left( \frac{n}{2} \right) \ \ \text{ if n} \ge 2
\end{cases}$$
$n = 2^k$

$T(n) \leq n + 4\left[ \frac{n}{2} + 4 · T\left( \frac{n}{4} \right) \right]$
	$T(n) \leq (1+2)n + 4^2 · T\left( \frac{n}{2^2} \right)$
$T(n) \leq 3n + 4^2\left[ \frac{n}{4} + 4 · T\left( \frac{n}{2^3} \right) \right]$
	$T(n) \leq (1+2+2^2)n + 4^3 · T\left( \frac{n}{2^3} \right)$
$T(n) \leq (1+2+2^2)n + 4^3\left[ \frac{n}{8} + 4 · T\left( \frac{n}{2^4} \right) \right]$
	$T(n) \leq (1 + 2 + 2^2 + 2^3)n + 4^4 · T\left( \frac{n}{2^4} \right)$
$T(n) \leq (1 + 2 + 2^2 + \dots + 2^{k-1})n + 4^k · T\left( \frac{n}{2^k} \right)$
	$T\left( \frac{n}{2^k} \right) = 1$
	$4^k = (2^k)^{2} = n^2$
	$(1 + 2 + 2^2 + \dots + 2^{k-1}) = 2^k -1$

$∴ T(n) \leq (n-1)n + n^2$
	$\leq 2n^2 = O(n^2)$




---
## Karatsuba's Algorithm

Karatsuba reduces integer multiplication from 4 recursive multiplications to 3 by using algebraic rearrangement, giving sub-quadratic time.

Karatsuba computes:
$$\begin{equation}
\begin{aligned}
& A = X_{L}Y_{L} \\
& B = X_{R}Y_{R} \\
& C = (X_{L} + X_{R})(Y_{L}+Y_{R})
\end{aligned}
\end{equation} $$
Then:
$$X_{L}Y_{R} + X_{R}Y_{L} = C - A - B$$
Combined:
$$xy = 2^nA + 2^{n/2}[C-A-B] + B$$
Runtime Recurrence:
$$T(n) = 3T(\frac{n}{2}) + O(n)$$


$xy = 2^n · X_{L}Y_{L} + 2^{n/2}[X_{L}Y_{R} + X_{R}Y_{L}] + X_{R}Y_{R}$
$xy = 2^n · X_{L}X_{L} + 2^{n/2}[(X_{L}+X_{R})(Y_{L}+Y_{R}) - X_{L}Y_{L} - Y_{R}X_{R})] + X_{R}Y_{R}$

3 Recursive Calls:
	$X_{L}Y_{L}$
	$X_{R}Y_{R}$
	$(X_{L}+X_{R})(Y_{R}+Y_{L})$

$$T(n) \le \begin{cases}
1 & \text{ if n = 1} \\
n + 3 * T\left( \frac{n}{2} \right) & \text{ if n} \ge 1
\end{cases}$$
$$n = 2^k$$

$T(n) \leq \left[ 1 + \frac{3}{2} + \left( \frac{3}{2} \right)^2 + \dots + \left( \frac{3}{2} \right)^{k-1}  \right]n + 3^k · T\left( \frac{n}{2^k} \right)$
	$T(n/2^k) = T(1) \leq 1$
	$3^k = 3^{\log n} = n^{\log 3}$
	$\left[ 1 + \frac{3}{2} + \left( \frac{3}{2} \right)^2 + \dots + \left( \frac{3}{2} \right)^{k-1}  \right] = \frac{x^k-1}{x-1} = 2 · 3^k = 2n^{\log 3}$

$T(n) \leq 3 · n^{\log 3}$
$= O(n^{log 3})$

Faster when $n >= 500$




