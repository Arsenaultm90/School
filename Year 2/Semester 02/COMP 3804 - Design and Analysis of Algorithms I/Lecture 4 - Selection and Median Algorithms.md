Input : Sequence 'S' of 'n' numbers, integer 'k' with $1 \leq k \leq n$.
Output : k-th smallest element in 'S'. (Element in position 'k' if it were sorted)

k = 1 : Smallest
k = n : Largest
k = $\frac{n}{2}$ : Median


Select(S, k):
	if |S|  = 1 : return the only element in S
	if |S| >= 2 :
		p = any element in S (pivot)

 $\boxed{<p(S_{<}) \ | =p(S_{=}) \ | >p(S_{>})}$
 if $k \leq |S_{<}|$ : Select($S_{<}, k$)
 if $|S_{<}| + 1 \leq k \leq |S_{<}| + |S_{=}|$ : Return $p$
 if $k \geq |S_{<}| + |S_{=}| + 1$ : Select($S_{>}$, $k-|S_{<}| - |S_{=}|$)
 
 Bad pivot : smallest
	 $T(n) = O(n) + T(n-1)$
	 $T(n) = O(n^2)$

Perfect pivot : median
	$T(n) = O(n) + T\left( \frac{n}{2} \right)$




---
## Find Element of Rank 'k' in Linear Time
*1973 : Blum, Floyd, Pratt, Rivest, Tarjan*

In O(n) we can compute a pivot 'p' such that $|S_{<|} \leq \alpha n$ and $|S_{>}| \leq \alpha n$.
$$\displaylines{\boxed{<p \ \ | =p \ | \ >p} \\ \leq \alpha n \ \ \ \ \ \ \ \ \leq \alpha n}$$
$T(n) = O(n) + T(\alpha n)$
$T(n) = n + \alpha n + T(\alpha^2n)$
	$= n[1 + \alpha + \alpha^2 + \dots ] = n\left( \frac{1}{1-\alpha} \right)$
	$= O(n)$


