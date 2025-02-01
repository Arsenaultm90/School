![[Pasted image 20250131112320.png]]

Pascal : $$\binom{n+1}{k} = \binom{n}{k} + \binom{n}{k-1}$$

Vandermonde : $$\binom{n+m}{r} = \sum^{r}_{k=0}\binom{m}{k}\binom{n}{r-k}$$

Easy : $$\binom{n}{k} = \binom{n}{n-k}$$

Unknown : $$\binom{2n}{n} = \sum^{n}_{k=0}\binom{n}{k}\binom{n}{n-k} = \sum^{n}_{k=0}\binom{n}{k}^2$$


**Example :**
How many rearrangements of the string "$ROCKY$" are there?
$$5!$$

How many rearrangements of the string "$\text{SUCCESS}$" are there?
$$\frac{7!}{2!3!}$$
OR
$$\displaylines{\text{Write down 3 S's : } \binom{7}{3}\\
\text{Write down 1 U : } \binom{4}{1} \\
\text{Write down 2 C's : } \binom{3}{2} \\
\text{Write down 1 E : } \binom{1}{1} \\ \\
\binom{7}{3}\times\binom{4}{1}\times\binom{3}{2}\times\binom{1}{1}}$$


---
##### Counting Solutions To Linear (In)Equalities

**Example :** 
How many solutions to the equation $x_{1} + x_{2} + x_{3} = 11$ are there, where $x_{1},x_{2},x_{3} \geq 0$ and $x_{1},x_{2},x_{3}$ are integers?

If we view it as stars and bars : $$| * * * * * * * * * * * |$$
We have 11 stars and 2 bars. We can view the 11 stars as the sums of our three terms and the bars as the summing symbol between each term. If we move the bars between the stars in any location, the three sections it creates can then act as our $x_{1}, x_{2}, x_{3}$ terms. 

For instance : $$* * * | * * * * *| * *\; *$$
Here we have : $$\displaylines{* * * = 3 \\
* * * * * = 5 \\
* * * = 3}$$
So, here we can see the total of those stars sums up to 11. To find the number of solutions to our given problem we can use : $$\binom{n+k-1}{k-1}$$
where, $$\displaylines{n+k-1\; \text{is our selection pool plus the number of chosen terms minus 1 to represent the 'bars'. }\\
k-1\; \text{is number of 'bars' we are setting up to divide up our pool.}}$$
$$\binom{11+3-1}{3-1} = \binom{13}{2} = \frac{13!}{2!(13-2)!} = \frac{13\times 12}{2} = \frac{156}{2} = 78$$



**Example :**
How many solutions to the inequality $x_{1}+x_{2}+x_{3} \leq 11$ are there, where $x_{1},x_{2},x_{3} \geq 0$ and $x_{1}, x_{2}, x_{3}$ are integers.

There are two ways to solve this.

1. Using the Sum Rule : $$\displaylines{|S_{0}| + |S_{1}|+\dots+|S_{11}| = |A| \\
\binom{2}{2} + \binom{3}{2} +\dots+ \binom{13}{2} = |A|}$$
2. Using a binomial where we set the values we don't want to $y$. $$\displaylines{\text{Using binary values :}\\
00000000000 \\ \\
\text{Now we need to add our seperators : }\\
000100001000 \\ \\
\text{ This is the same problem as before, so to change this we need to account for values less than 11.} \\
\text{For instance :}\\
00100010100000 \\
x_{1}|x_{2}|x_{3}|y \\ \\
2 + 3 + 1 = 6 \\ \\
\text{Here the y value just repesents the remainder from 11.}\\
\text{But we can represent this in binomial form :} \\
\binom{11+4-1}{4-1}=\binom{14}{3} \\ \\
14\; \text{- for each 0 and 1 }(n+k-1) \\
3\;\text{- for the number of 1's}}$$







