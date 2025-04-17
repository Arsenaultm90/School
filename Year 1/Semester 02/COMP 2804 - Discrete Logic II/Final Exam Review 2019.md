Consider strings of length 85, in which each character is one of the letters a, b, c, d. How
many such strings have exactly 5 letters c?

**How To Solve :** 
	We choose exactly 5 of those letters to become 'c' and find the number of ways we can put them in a string of length 85. $$\binom{85}{5} = \frac{85!}{5!(85-5)!}$$
	We then need to find the number of ways to put the remaining characters which consists of a, b, and d. $$3^{80}$$
	$$\displaylines{\text{Our answer is :} \\
	\binom{85}{5} · 3^{80}}$$



---
Consider strings of length 85, in which each character is one of the letters a, b, c, d. How
many such strings have exactly 15 letters a and exactly 30 letters d?

**How To Solve :**
	We choose 15 characters to be letter 'a' and find the number of ways they can exists in a string of length 85. $$\binom{85}{15}$$
	We then choose 30 characters to be the letter 'd' and find the number of ways they cna exists in a string of length 70 (85 - # of letter 'a'). $$
	\binom{70}{30}$$
	We then need to fill the remaining characters with either 'c' or 'b'. $$2^{40}$$
	$$\displaylines{\text{Our answer is :} \\
	\binom{85}{15} · \binom{70}{30} · 2^{40}}$$



---
Consider a set S consisting of 25 beer bottles b1, b2, . . . , b25 and 30 cider bottles c1, c2, . . . , c30. How many 10-elements subsets of S contain at least 2 beer bottles?

**How To Solve :** 
	Here we solve by using the **Complement Rule**, where find the total number of 10-element subsets we can create with all beer and cider and then subtract the subsets that don't meet our criteria. $$\displaylines{\text{Total number of ways to choose 10-element subset from 25 beer and 30 cider :} \\
	\binom{55}{10} \\ \\
	\text{Subtract all subsets that contain no beer bottles(all cider) :} \\
	\binom{30}{10} \\ \\
	\text{Subtract all subsets that contain only a single beer bottle. 25 ways to choose a single beer bottle :} \\
	25 ·\binom{30}{9} \\ \\
	\text{Our answer is :} \\
	\binom{55}{10} - \binom{30}{10} - 25 · \binom{30}{9}}$$



---
Consider the sets A = {1, 2, . . . , 10} and B = {1, 2, . . . , 14}. Let S = {(x, y) : x ∈ A, y ∈ B}.
An element (x, y) of S is awesome, if x is even or y is even. What is the number of awesome
elements in S?

**How To Solve :**
	Use the Inclusion-Exclusion Principle. $$\displaylines{\text{When 'x' is even :} \\
	5 · 14 = 70 \\ \\
	\text{When 'y' is even :} \\
	7 · 10 = 70 \\ \\
	\text{When 'x' and 'y' are both even :} \\
	5 · 7 = 35 \\ \\
	\text{Our answer is :} \\
	70 + 70 - 35 = 105}$$



---
Let $m ≥ 2$ and $n ≥ 2$ be integers. Why does the identity $\binom{m+n}{2} = \binom{m}{2} + \binom{n}{2} + mn$ hold?

**How To Solve :** 
	Because both sides count the number of 2-element subsets of a set of size $m + n$.



---
What is the coefficient of $x^{20}y^{35}$ in the expansion of $(5^x − 3^y)^{55}$?

**How To Solve :**
	This is exactly the **Newton Binomial Theorem** : $$\displaylines{(x+y)^n = \sum^n_{k=0} \binom{n}{k} x^{n-k} y^k  \\ \\
	(5x)^{20}(-3y)^{35} \\\text{ Because the negative is to the power of an odd number we keep it in the answer.}\\ \\
	\text{Our answer is :} \\
	-\binom{55}{35}·5^{20}·3^{35}}$$



---
A string that is obtained by rearranging the letters of the word **POOPERSCOOPER**
is called cool if each occurrence of E has the letter R to its left or right, and each occurrence
of R has the letter E to its left or right. 

Thus, both **POOPERSCOOPER** and **OPRECSOOOERPP** are cool, whereas **EPOOPRSCOOPER**
is not cool. 

What is the number of cool strings?

**How To Solve :**
	3 x P
	4 x O
	2 x ER
	1 x S
	1 x C 
	$$\displaylines{\text{Total number of blocks  = 11} \\ \\
	\text{Number of ways to place 'P'} : \\
	\binom{11}{3} \\ \\
	\text{Number of ways to place 'O' :} \\
	\binom{8}{4} \\ \\
	\text{Number of ways to place 'ER' :} \\
	\binom{4}{2} \\ \\
	\text{Number of ways to place 'S'} : \\
	\binom{2}{1} \\ \\
	\text{Number of ways to place 'C' :} \\
	\binom{1}{1} \\ \\
	\text{Since the letters 'ER' can also be placed as 'RE' we multiply by } 2 \times 2.\\ \\ \text{Our answer is : } \\
	\binom{11}{3}· \binom{8}{4}· \binom{4}{2} · \binom{2}{1} · \binom{1}{1} · 4 }$$



---
A bitstring is called 00-free, if it does not contain two 0’s next to each other. In class, we
have seen that for any $m ≥ 1$, the number of 00-free bitstrings of length $m$ is equal to the
$(m + 2)^{th}$ Fibonacci number $f_{m+2}$.

What is the number of 00-free bitstrings of length 20 that have 1 at position 11 and 0 at
position 20. (The positions are numbered 1, 2, . . . , 20.)

**How To Solve :** 
	Since we have '1' at the $11^{th}$ position, '0' at the $20^{th}$ position and this is a 00-free bitstring, there must be a '1' at the $19^{th}$ position leaving us with 17 bits remaining. 
	To show it visually : $$\underline{} \; \underline{}\; \underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{1}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{1}\;\underline{0}\;$$ Given our knowledge of using the fibonacci sequence to find the number of 00-free bitstring, we can split this into two sequences. All empty bits before the '1' and the empty bits after. 
	Since we have 10 empty position before the '1' it will be the $(m+2)^{th}$ position. $$f(12)$$
	There are 7 empty bits after the '1', therefore we know our $(m+2)^{th}$ position. $$f(9)$$
	$$\displaylines{\text{Our answer is :} \\ f(9) · f(12)}$$


---
Consider bitstrings that do not contain 011 and have 1 at every even position. (The positions
are numbered 1, 2, 3, . . .). 

Let $S_{n}$ be the number of such strings having length $n$. 
Which of the following is true for any $n ≥ 3$?

**How To Solve :**
	We have bistring in the form of : $$\underline{}\;\underline{1}\;\underline{}\;\underline{1}\;\underline{}\;\underline{1}\;\underline{}\;\underline{1}\;\underline{}$$
	If we make our first bit a '1' : $$\underline{1}\; \underline{1}\; \overbrace{\underline{}\;\underline{1}\;\underline{}\;\underline{1}\;\underline{}\;\underline{1}\;\underline{}}^{n-2} = S_{n-2}$$
	If we make our first bit a '0' : $$\displaylines{\underline{0}\;\underline{1}\;\underline{}\;\underline{1}\;\underline{}\;\underline{1}\;\underline{}\;\underline{1}\; \underline{} \\ \\
	\text{Since we cannot have a 011 sequence every odd position ends up being '0'.} \\
	\underline{0}\;\underline{1}\;\underline{0}\;\underline{1}\;\underline{0}\;\underline{1}\;\underline{0}\;\underline{1}\; \underline{0} = 1}$$
$$\displaylines{\text{Our answer is :} \\ 
S_{n} = 1 + S_{n-2}}$$


---
The function $f : N → N$ is recursively defined as follows:
	$f(0) = 2$,
	$f(n) = 3 · f (n − 1) + 1, \text{   if } n ≥ 1$.

Which of the following is true for all integers $n ≥ 0$?

(a) $f (n) = \frac{5}{2} · 3^n − 1$
(b) $f(n) = \frac{3}{2} · 3^n − \frac{1}{2}$
(c) $f(n) = \frac{5}{2} · 3^n − \frac{1}{2}$

**How To Solve :**
	Find the first few values of the recursive function : $$\displaylines{
	f(0) = 2 \\
	f(1) = 3· f(n-1) + 1 = 7 \\
	f(2) = 3· f(n-1) + 1 = 22}$$
	Now test each of the options : $$\displaylines{a)\; f(0) = \frac{5}{2} · 3^0 - 1 = \frac{3}{2} \\
	b)\; f(0) = \frac{3}{2}· 3^0 - \frac{1}{2} = \frac{1}{2} \\
	c)\; f(0) = \frac{5}{2} · 3^0 - \frac{1}{2} = \frac{4}{2} = 2 \\ \\
	\text{Our answer is : } \\
	c)\; f(n) = \frac{5}{2} · 3^n - \frac{1}{2}}$$
!!HOW TO SOLVE BY PROOF OF INDUCTION!!


---
You flip a fair coin 6 times; the flips are independent of each other. 
What is the probability that in these 6 coin flips, the coin comes up heads exactly 3 times?

**How To Solve :** 
	Method 1 : Using the Binomial Distribution $$\displaylines{P(X = k) = \binom{6}{3}p^k(1-p)^{x-k} \\ P(X = 3) = \binom{6}{3}·0.5^3 ·0.5^3 = 0.3125 = \frac{5}{16}}$$
	Method 2 : Using Foundations $$\displaylines{\text{Total \# of possibilities : }|S| = 2^6 = 64 \\
	\text{\# of ways to choose 3 heads from 6 flips :} \binom{6}{3} = 20 \\ \\
	\text{Our answer is :} \\
	\frac{\binom{6}{3}}{64} = \frac{20}{64} = \frac{5}{16}}$$



---
In a standard deck of 52 cards, each card has a suit and a rank. There are four suits (spades
♠, hearts ♥, clubs ♣, and diamonds ♦), and 13 ranks (Ace, 2, 3, 4, 5, 6, 7, 8, 9, 10, Jack,
Queen, and King).

Assume you get a uniformly random hand consisting of 5 cards. What is the probability
that the 5 cards in this hand consist of 3 Aces and 2 Queens?

**How To Solve :** 
	Multivariate Hypergeometric Distribution
	N = 52
	M = 4
	n = 5
	x = 3

$$\displaylines{P(X = 3) = \frac{\binom{4}{3} \binom{4}{2}}{\binom{52}{5}} = \frac{24}{\binom{52}{5}}}$$



---
You flip a fair coin 6 times; the flips are independent of each other. Consider the events
	A = “exactly 3 flips result in heads”,
	B = “at least 2 flips result in heads”.

What is $P(A | B)$?

**How To Solve :** 
	$$\displaylines{P(A|B) = \frac{P(A \cap B)}{ P(B)} \\ \\
	P(0) = \binom{6}{0}0.5^0 · 0.5^6 = \frac{1}{2^6} \\
	P(1) = \binom{6}{1}0.5^1 · 0.5^5 = \frac{6}{2^6} \\ \\
P(B) = 1 - [P(0) + P(1)] \\
	P(B) = 1 - \frac{1}{2^6} - \frac{6}{2^6} = \frac{57}{64} \\ \\
	\text{Event 'A' implies 'B' : } P(A \cap B) = P(A) \\ \\
	P(A|B) = \frac{P(A)}{P(B)} = \frac{\frac{5}{16}}{\frac{57}{64}} = \frac{5\times64}{16 \times 57} = \frac{320}{912} = \frac{20}{57}}$$




---
Let $n$ and $k$ be integers with $0 ≤ k ≤ n$.
You are given two bitstrings a1, a2, . . . , an and b1, b2, . . . , bn, both of length $n$. 
In both bitstrings, each bit is $0$ with probability $\frac{1}{2}$, and 1 with probability $\frac{1}{2}$ (independent of all
other bits).

For each $i$ with $1 ≤ i ≤ n$, let $c_{i} = a_{i} − b_{i}$. Consider the set $$\displaylines{P = \{i : 1 ≤ i ≤ n \text{ and } c_{i} ≥ 0\} \\ 
\text{P is the set of all indices i, where i ranges from 1 to n, such that } c_{i} \text{ is greater than or equal to zero.}}$$
What is the probability that the size of the set $P$ is equal to $k$?


**How To Solve :** 
	If $c_{i} = a_{i} - b_{i}$ and $c_{i} \ge 0$, then $c_{i} \ge 0 \Longleftrightarrow a_{i} \ge b_{i}$
	So the probability of $a_{i} \ge b_{i}$ is as follows : 

| a   | b   |
| --- | --- |
| 0   | 0   |
| 0   | 1   |
| 1   | 0   |
| 1   | 1   |
	There is a $\frac{3}{4}$ chance that $a_i \ge b_{i}$.
	$$\displaylines{\text{Our answer is :} \\
	\binom{n}{k}· \frac{3}{4}^k · \frac{1}{4}^{n-k}}$$



---
Consider a uniformly random permutation $a_{1}, a_{2}, a_{3}, a_{4}, a_{5}$ of the set {1, 2, 3, 4, 5}. 
Consider the events -
	A = “$a_{1}$ is odd”,
	B = “$a_{5}$ is even”.

Which of the following is correct?

(a) The events $A$ and $B$ are independent.
(b) The events $A$ and $B$ are not independent.

Where events are independent if : $$P(A \cap B) = P(A) \times P(B)$$
**How To Solve :** 
	We have three things to calculate : $$\displaylines{
	P(A) = \frac{3}{5} \\ P(B) = \frac{2}{5} \\ \\
	P(A) \times P(B) = \frac{3}{5} \times \frac{2}{5} = \frac{6}{25} \\ \\
	\text{For the first digit, there are 3 ways to be odd.} \\
	\text{For the last digit, there are 2 ways to be even.}\\
	\text{The remaining 3 digits can be chosen } 3! \text{ ways.} \\
	\underline{3}\;\underline{}\;\underline{}\;\underline{}\;\underline{2}\; \\ \\
	 P(A \cap B) = \frac{3! \times 3 \times 2}{5!} = \frac{6}{20} \\}$$
	 ∴ These events are not independent since $$\displaylines{P(A \cap B) \ne P(A) \times P(B) \\
	 \frac{6}{20} \ne \frac{6}{25}}$$



---
You roll a fair red die once and you roll a fair blue die once. These two rolls are independent.
Consider the events
	A = “the sum of the red die and the blue die is 5”,
	B = “the result of the red die is even”.
	
Which of the following is correct?

(a) The events A and B are independent.
(b) The events A and B are not independent.

Where events are independent if : $$P(A \cap B) = P(A) \times P(B)$$
**How To Solve :** 
	$$\displaylines{P(A) = \frac{4}{36} = \frac{1}{9} \\
	P(B) = \frac{1}{2} \\
	P(A \cap B) = \frac{2}{36} = \frac{1}{18} \\ \\
	P(A \cap B) = P(A) \times P(B) \\
	\frac{1}{18} = \frac{1}{9} \times \frac{1}{2}}$$
	∴ The events are independent.



---
Let $n ≥ 8$ be an integer. Consider a uniformly random permutation $a_{1}, a_{2}, . . . , a_{n}$ of the set
{1, 2, . . . , n}. 
Consider the events :
	A = “a7 is the minimum of a1, a2, . . . , a7”,
	B = “a6 is the minimum of a1, a2, . . . , a6”.

Which of the following is correct?

(a) The events A and B are independent.
(b) The events A and B are not independent.

**How To Solve :**
	$$\displaylines{P(A) = \frac{1}{7} \\
	P(B) = \frac{1}{6} \\ \\
	\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{}\;\underline{2nd\; min}\;\underline{min}\; \\ \\
	P(A \cap B) = \frac{5!}{7!} = \frac{1}{6·5} = \frac{1}{6} · \frac{1}{5}}$$
	∴ The events are independent.



---
Let $A$ and $B$ be two independent events in some sample space $S$. Recall that $\bar{B}$ denotes the
complement of $B$. 

You are given that $P(A) = \frac{1}{4}$ and $P(\bar{B}) = \frac{2}{3}$. What is $P(A ∪ B)$?

Where, $$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$
Therefore, $$\displaylines{P(A) = \frac{1}{4} \\
P(B) = \frac{1}{3} \\P(A \cap B) = \frac{1}{4} · \frac{1}{3} = \frac{1}{12} \\ \\
P(A \cup B) = \frac{1}{4} + \frac{1}{3} - \frac{1}{12} \\=\frac{7}{12} - \frac{1}{12}
=\frac{6}{12} = \frac{1}{2}}$$


---
A red box contains the numbers 0, 1, and 2; a blue box contains the numbers 0 and 1; and
a green box contains the numbers 1 and 2. Consider the following two steps:
	Step 1: 
		Choose a uniformly random number from the red box, and denote it by x.
	Step 2:
		• If x = 0 or x = 2, then choose a uniformly random number from the green box, and
		denote it by y.
		• Otherwise (i.e., if x = 1), choose a uniformly random number from the blue box, and
		denote it by y.
		
Consider the random variables 
	X = the number x you choose in Step 1,
	Y = the number y you choose in Step 2,
	Z = max(X, Y ).

What is the expected value E(Z) of the random variable Z?
$$E(Z) = \sum_{k} k·P(Z = k)$$

