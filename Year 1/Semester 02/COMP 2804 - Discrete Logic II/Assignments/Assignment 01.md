COMP 2804 B
Matthew Arsenault
101288386

1. (4 points) How many pairs, $(x, y)$, of natural numbers exist so that $1 ≤ x, y ≤ 1000$ and $x^2 + y^2$ is divisible by 5?

Possible remainders for $x^2$ :
$$\displaylines{
x \equiv 0, 1, 2, 3, 4 \; \text{(mod 5)}\\
0^2 \equiv 0\; \text{(mod 5)},\;
1^2 = 1\; \text{(mod 5)},\;
2^2 \equiv 4\; \text{(mod 5)},\;
3^2 \equiv 9 \equiv 4\; \text{(mod 5)},\;
4^2 \equiv 16 \equiv 1\; \text{(mod 5)}\\
x^2 \equiv 0, 1, 4 \text{ (mod 5)}}$$

Find number of values divisible by 5 for $x^2 \text{ and } y^2$ with remainder $0$ : $$\displaylines{1.\; (x^2 + y^2) \equiv (0, 0)\text{(mod 5) : } 200 \times 200 = 40000 \\ \\
2.\;x^2 \equiv 1\text{(mod 5)}\; |\; x \equiv 1\text{(mod 5)}, x \equiv 4\text{(mod 5)}\\ x \equiv 1\text{(mod 5)} : \frac{1000}{5} = 200,\\ x \equiv 4\text{(mod 5)} : \frac{1000}{5} = 200\\ 200 + 200 = 400 \\ \\ y^2 \equiv 4\text{(mod 5)}\; | \; y \equiv 2\text{(mod 5)},\; y \equiv 3\text{(mod 5)}\\ y \equiv 2 : \frac{1000}{5} = 200, \\ y \equiv 3\text{(mod 5)} : \frac{1000}{5} = 200 \\ 200 + 200 = 400 \\ \\(x^2 + y^2) \equiv (1, 4)\text{(mod 5) : } 400 \times 400 = 160000 \\ \\
3.\; \text{Same calculations as step 2 : }\\(x^2 + y^2) \equiv (4, 1)\text{(mod 5) : } 400 \times 400 =160000 \\ \\
∴\text{Total number of pairs divisible by 5} = 40000 + 160000 + 160000 = \boxed{360000}}$$
<div style="page-break-after: always;"></div>


2. (4 points) How many 5-digit palindrome numbers are divisible by 9? Hint: A number is divisible by 9 if the sum of its digits is divisible by 9.

Let's say : $$\displaylines{S = a+b+c+b+a = 2a + 2b + c}$$
And we need : $$\displaylines{2a + 2b + c \equiv 0\;\text{(mod 9)}}$$
Given, $$\displaylines{a = [1-9] \\
b = [0 -9] \\
c = [0-9]\\
9 * 10 = 90\; \text{combinations of (a, (b, c))}\\
c \equiv 0\;\text{(mod 9), where }c = 0, 9 \\ \\
\text{We can add 10 additional combinations for 'c' }\\
∴ \boxed{90 + 10 = 100}}$$
<div style="page-break-after: always;"></div>

3. Prove that the R(4, 2) = 4

Assuming the contrary :
	There is neither a **Monochromatic $K_{4}$** nor a **Monochromatic Independent Set Of Size 2** in the graph.

Ramsay's Number :
	$R(4,2)=4$, in any two-coloured complete graph on 4 vertices, there must be either:
		-A monochromatic $K_{4}$
		-A monochromatic independent set of size 2

If all edges cannot form a complete blue $K_{4}$, there must be at least one red edge.

If a red edge exists, this creates a monochromatic independent set, contradicting the assumption that no independent sets of size 2 exists.

If we avoid all red edges, meaning all edges are blue, we are left with a blue $K_{4}$.

∴ Our initial assumption that neither a monochromatic $K_{4}$ nor a monochromatic independent set exists is false proving that $R(4, 2) = 4$ is the smallest number where these structures appear.


<div style="page-break-after: always;"></div>


4. Three pirates, Billy, Willy, and Dilly, have found a treasure that has 80 identical doubloon coins in it. The pirates would like to split the treasure so that each pirate will have at least 15 coins. How many different splits satisfy this requirement?

Subtract the minimum number of required coins for each pirate from the total number of coins : 
$$80 - (3 \times 15) = 35$$

We can now use the new total to get the total number of ways to split the remaining coins amongst three pirates : 
$$\frac{(35+3-1)!}{35!(3-1)!} = \frac{37!}{35!2!} = \frac{37 \times 36}{2} = 666$$

$$∴ \boxed{666}$$

<div style="page-break-after: always;"></div>


5. A jolly class of 98 students is organising a New Year’s Eve Party. The organising committee of the event has to have between 5 and 7 regular members and one chair. In how many different ways can the committee be put together, if all students are capable of playing any role (member or chair) in the committee?

Choosing the chairperson : 
$$\binom{98}{1} = 98$$

Choosing the remaining 5 - 7 members :
$$\binom{97}{5} + \binom{97}{6} + \binom{97}{7} = \frac{97!}{5!92!} + \frac{97!}{6!91!} + \frac{97!}{7!90!}$$ $$= 64446024 + 988172368 + 12846240784 = 13898859176 $$

Combining the two formulas :
$$\boxed{98 \times (\binom{97}{5} + \binom{97}{6} + \binom{97}{7}) = 98 \times 13898859176 = 1.3620882e+12 }$$

<div style="page-break-after: always;"></div>


6. How many natural numbers, that are ≤ 200, are both indivisible by 5 and indivisible by 6?

Total number of values divisible by 5 : $$ 200 \div 5 = 40$$
Total number of values divisible by 6 : 
$$200 \div 6 = 33$$

Total number of values divisible by 5 and 6 : $$200 \div 30 = 6$$

We then remove duplicate counts : $$40 + 33 - 6 = 67$$
And we subtract this value from the total : $$200 - 67 = 133$$
∴ The total number of values $\leq 200$ that are both indivisible by 5 and 6 is : $$\boxed{133}$$
