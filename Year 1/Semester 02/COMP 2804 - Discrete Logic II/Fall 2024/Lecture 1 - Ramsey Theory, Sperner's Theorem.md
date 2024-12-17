##### Ramsay Theory
Ramsey Theory posits that if you partition or organize a large enough set, you will always find a subset that exhibits a particular property or structure.

**Ramsey Number**
This is the smallest number $R(m,n)$ such that any graph with $R(m,n)$ vertices, where every edge is either red or blue, contains:

- A **Red Clique** : A complete subgraph of size $m$(All edges connected), or
- A **Blue Independent Set** : An independent subgraph of size $n$(Edges not connected).

Example:
- $R(3,3)=6$, meaning that in any group of 6 people, there will always be either 3 people who all know each other (a "red clique") or 3 people who are all strangers to each other (a "blue clique").


---
##### Sperner's Theorem
**Sperner's Theorem** is a fundamental result in **combinatorics** about subsets of a finite set. It states:
	In a finite set $S$ with $n$ elements, the largest collection of subsets of $S$ in which no subset is contained within another (called a **Sperner family** or an **antichain**) has size $\left(\begin{array}{c}n\\ \frac{n}{2}\end{array}\right)$.

Here:
-  $\left(\begin{array}{c}n\\ k\end{array}\right)$ is the binomial coefficient, which counts the number of ways to choose $k$ elements from a set of $n$ elements.
- $[\frac{n}{2}]$ is the largest integer less than or equal to $\frac{n}{2}$, corresponding to subsets of size approximately $\frac{n}{2}$, which maximize the binomial coefficient.

When $n$ is odd:
Calculate for $\frac{n}{2} \pm 1$ to get the **Sperner Family** of a given set. For odd $n$, the number of subsets will be equal whether you choose greater or lesser than $\frac{n}{2}$


Example:
Let $S={1,2,3,4}$, so $n=4$.

1. **All subsets of $S$:** The power set of $S$ has $2^n=16$ subsets, including:
    
    - Subsets of size 0: $∅$
    - Subsets of size 1: $\{1\},\{2\},\{3\},\{4\}$
    - Subsets of size 2: $\{1,2\},\{1,3\},\{1,4\},\{2,3\},\{2,4\},\{3,4\}$
    - Subsets of size 3: $\{1,2,3\},\{1,2,4\},\{1,3,4\},\{2,3,4\}$
    - Subsets of size 4: $\{1,2,3,4\}$
    
2. **A Sperner family:** A Sperner family is a collection of subsets where no subset is contained within another. For $n=4$, **Sperner's Theorem** says the largest such family has $\left(\begin{array}{c}4\\ 2\end{array}\right) = 6$ subsets.
    
    Example:
    $\{\{1,2\},\{1,3\},\{1,4\},\{2,3\},\{2,4\},\{3,4\}\}$
    
    Here, all subsets have size 2, so no subset is contained within another.


**Binomial Coefficient**
It counts the number of ways to choose $k$ elements from a set of $n$ elements.
$$\displaylines{\left(\begin{array}{c}n\\ k\end{array}\right) = \frac{n!}{k!(n-k)!}}$$
Example:
$\left(\begin{array}{c}5\\ 2\end{array}\right)$ is read as **"5 choose 2"**.
It means: "How many ways can I choose 2 elements from a set of 5?"

For $\left(\begin{array}{c}n\\ k\end{array}\right)$: $$\left(\begin{array}{c}5\\ 2\end{array}\right) = \frac{5!}{2!(5-2)!} = 10$$
