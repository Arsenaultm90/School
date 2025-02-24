Matthew Arsenault
101288386

1. (4 points) A grasshopper sits on the first stone of a hopscotch path that begins there and continues to infinity. The grasshopper hops along the path in jumps of 1 or 2 stones. In how many different jump patterns can the grasshopper reach the n’th stone?

One Stone - $f(n-1)$
Two Stones - $f(n-2)$
Recurrence Relation - $f(n) = f(n-1) +f(n-2)$

Base Cases :
$f(1) = 1$
$f(2) = 2$

For $f(n) = f(n-1) +f(n-2)$, where $n > 2$
$f(3) = f(2) + f(1) = 2 + 1 = 3$
$f(4) = f(3) + f(2) = 3 + 2 = 5$

The values of $n$ onto infinity will give results equal to the Fibonacci sequence of the function $$f(n) = F(n+1)$$
∴ The function to find the total number of patterns to the $n^{th}$ stone is $$\boxed{f(n) = f(n-1) + f(n-2)}$$ 

<div style='page-break-after: always;'></div>

2. (4 points) Given 8 distinct natural numbers, none of which are greater than 14. Consider all pair-wise (absolute) differences of those 8 numbers. Prove that there are 3 equal pair-wise differences.
Hint: $n$ numbers create $\frac{n(n−1)}{2}$ pairs. E.g., if you have 3 numbers: 5, 7, 2, then you will have 3 (absolute)differences: $|5−7|=2, |5−2|=3, |7−2|=5.$

$$\displaylines{\frac{n(n-1)}{2} = \frac{8(8-1)}{2} = \frac{56}{2} = 28\\28 \text{ Distinct Pairwise Differences}  \\ \\
x_{1}, x_{2}, \dots, x_{8} \text{ where each }x_{i\; \in } \{1, 2, \dots, 14\} \\ \\
\text{Find the largest difference :}\\
|x_{i} - x_{j}| = |14-1| = 13 \\
13 \text{ Distinct Pairwise Difference Values}
\\ \\
\text{Set of Pairwise Differences } = \{1, 2, \dots, 13\}}$$

By the Pigeonhole Principle, if we have 28 distinct pairwise differences, and 13 possible values, then at least one of the difference values appears 3 times. Given by the equation :
$$\boxed{\left\lceil  \frac{28}{13}  \right\rceil  = 3}$$



<div style='page-break-after: always;'></div>


3. Given the following recurrence: $\begin{cases}f(0) = 1 \\ f(1) = 8 \\ f(n) = f(n-1) +6f(n-2),\; n \geq 2\end{cases}$

A) Find the closed form expression for f(n).
Given that the expression is a linear recurrence relation, I can expect it to be in the form of : $$f(n) = Ar^n_{1}+Br^n_{2}$$
Characteristic Equation : $$r^2 - r - 6 = 0$$
Finding the roots : $$\displaylines{r = \frac{-(-1)\pm \sqrt{ (-1)^2-4(1)(-6) }}{2(1)} \\ 
=\frac{1 \pm \sqrt{ 25 }}{2} \\ \\
r_{1} = 3,\; r_{2} = -2}$$
Solve for A and B : 
$$\displaylines{f(0) = A·3^0 + B·(-2)^0 \\
1=A+B \\ \\
f(1) = A·3^1 + B(-2)^1 \\
8 = 3A -2B \\ \\
B = 1-A \\ \\
8 = 3A - 2(1-A) \\
8=3A -2+2A \\
5A = 10 \\
A = 2 \\ \\

B = 1-A \\
B = -1}$$
Closed-Form Expression : 
$$\boxed{f(n) = 2·3^n-2^n}$$

<div style='page-break-after: always;'></div>



B) Prove by induction that your closed form solution is correct.

For $n = 2$ : $$\displaylines{ f(n) = 2·3^n-2^n\\=2·3^2 - 2^2 \\
=2·9 - 4 \\
\boxed{= 14}}$$
$$\displaylines{f(n) = f(n-1) + 6f(n-2) \\
=8 + 6(1) \\
\boxed{= 14}}$$


<div style='page-break-after: always;'></div>



4. (4 points) In a study group there are 17 people who speak English, 14 who speak Chinese, and 10 who speak Arabic. 16 people in the group speak exactly two languages, while only 1 person speaks all 3 languages. How many people are in the study group overall?

Let's assume one of the two languages the 16 people can speak is English. 
Let's remove 13 from the set of people who can speak Chinese and leave one for the person who can speak 3 languages.
Remove 3 more from the set of people who can speak Arabic to make up the 16 bilingual people.

We now have : $$\displaylines{English - 1\\
Chinese - 1 \\
Arabic - 7}$$
Remove 1 from each set for the person who can speak 3 languages.
We are now left with 6 people. 
$$\displaylines{\text{Total number of people in the study group :} \\
\boxed{16 + 1 + 6 = 23}}$$


<div style='page-break-after: always;'></div>


5. (4 points) Find the number of all bit-strings of length n that satisfy all three of the following conditions: begin with "0", end with "0", and do not contain a substring "11".

Let $a_{n}$ = the size of the set $f(n)$

$f(0) = \{\}$
$f(1) = \{0\}$
$f(2) = \{00\}$
$f(3) = \{000, 010\}$

For $n \geq 4 :$
The bit-string starts with a $0$ followed by any string in $f(n-1)$
The bit-string starts with a $01$ followed by any string in $f(n-2)$

$a_{4} = a_{3} + a_{2}$
$a_2 = 1$
$a_3 = 2$
$a_{4} = 3$
$$f(4) = \{0000, 0010, 0100\}$$
$$\boxed{a_{n} = a_{n-1} + a_{n-2}}$$
