RSelect finds the k-th smallest element by repeatedly partitioning around a random pivot; the number of elements smaller than the pivot determines its rank, allowing the algorithm either to return the pivot or to recurse on the only subarray that can still contain the k-th smallest.


Find the **k-th smallest element** in an unsorted list
Sorting = $O(n \log n)$
Randomized Select = **expected $O(n)$


- Pick a **random pivot** p
- Split the list into:
    - $S_{<}$​: elements smaller than p
    - $S_=$​: elements equal to p
    - $S_>$​: elements greater than p
- Compare `k` to the sizes:
    - If `k` is small → recurse left
    - If `k` hits the pivot block → return `p`
    - If `k` is large → recurse right (adjusting `k`)
- Repeat on **only one side**


RSelect(S, k) : // Returns the k-th smallest element
	if |S| = 1 : Return only element in S
	if |S| >= 2 : p = uniformly random element in S
$$\displaylines{ S_{<} \ \ \ \ S_{=} \ \ \ S_{>} \\ \boxed{\ \ p_{<} \ | \ \ p_{=} \ | \ \ p_{>}} \\ \\ if \ k \leq |S_{<}|: RSelect(S_{<}, k) \\
if \ |S_{<}| + 1 \leq k \leq |S_{<}| + |S_{=}| : \mathrm{Re}turn \ p \\
if \ k \geq |S_{<}| + |S_{=}| + 1 : RSelect(S_{>},\ k -  |S_{<}|- |S_{=}|) }$$


Phases are used to prove that the algorithm cannot remain expensive for many recursive calls, ensuring linear expected running time.

$n = |S|$
$T = Running\ Time$
Claim : $E(T) = O(n)$

for i = 0, 1, 2
Call to RSelect is in phase 'i' if:
	The length of the sequence in this call $\leq \left( \frac{3}{4} \right)^in$  and $> \left( \frac{3}{4} \right)^{i+1}n$
$$\boxed{\ Phase \ 3 \ |_{\left( \frac{3}{4} \right)^3n} \ Phase\ 2 \ |_{\left( \frac{3}{4} \right)^2n} \ Phase\ 1 \ |_{\left( \frac{3}{4} \right)^1n} Phase\ 0 \ |_{n}}$$
Consider one call in phase $i$.
m = length of sequence
	$\left( \frac{3}{4} \right)^{i+1}n < m \leq \left( \frac{3}{4} \right)^in$

Sorted Sequence
$$
\boxed{
\begin{array}{c|c|c}
\text{Bad} & \text{Good Pivots} & \text{Bad} \\
\hline
\frac{m}{4} & \frac{m}{2} & \frac{m}{4}
\end{array}
}
$$

Pr(pivot $p$ is good) = $1/2$

If pivot $p$ is good :
	Next call to RSelect :
		Length of sequence $\leq m - \frac{m}{4}$
		$= \frac{3}{4}m \leq \left( \frac{3}{4} \right)^{i+1}n$
		in phase $\geq i+1$

Random Variable $X_{i}$ = number of calls in phase $i$
Experiment :
	$Pr(Success) = \alpha$
	$Pr(Failure) = 1 - \alpha$
	$E(\text{number of times until success}) = \frac{1}{\alpha}$

$E(X_i) \leq 2$, where $\alpha = \frac{1}{2}$

Time $T = \sum_{i \geq 0} X_{i} · c\left( \frac{3}{4} \right)^in$
$E(T) = \sum_{i\geq 0} E\left( X_{i}\right) · c\left( \frac{3}{4} \right)^in$
	$E(X_{i}) \leq 2$
	$=2cn \sum^\infty_{i = 0} \left( \frac{3}{4} \right)^i$
	$=2cn· \frac{1}{1- \frac{3}{4}}$
	$=8cn$
	$= O(n)$



