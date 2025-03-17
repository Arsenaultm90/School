Matthew Arsenault
101288386

1. (4 points) A box contains N balls. M of them are white and the rest (N − M balls) are black. n ≤ N times a random ball is taken out of the box and inspected. Given a number m (m ≤ n and m ≤ M), for each of the additional conditions below, find the probability that exactly m times out of n the removed ball will be white.

(a)  The balls are taken from the box without replacement. That is, once the ball is taken out of the box, it stays out.$$\displaylines{\text{Hypergeometric Distribution} \\ P(X=m)= \frac{\binom{M}{n}\binom{N-M}{n-m}}{\binom{N}{n}}}$$

(b)  The balls are taken from the box with replacement. That is, a ball is taken from the box, inspected, and then put back into the box.$$\displaylines{\text{Binomial Distribution} \\ P(X = m) = \binom{n}{m}\frac{M}{N}^m(1-\frac{M}{N})^{n-m}}$$
<div style='page-break-after: always;'></div>


2. (3 points) An 8-digit number is chosen at random. Find the probability that 4 digits of the number would be the same, while the other digits will be different from these 4 and from each other.
 $$\displaylines{\text{10 choices for the repeating digits} \\ \\
\text{Number of combinations for the positions of repeated number} \\
\binom{8}{4} \\ \\
\text{Number of ways to choose remaining unique values} \\
\binom{9}{4} \\ \\
\text{Number of combinations for the positions of unique numbers} \\
4! \\ \\
\text{Calculations}\\
=10 \times \binom{8}{4} \times \binom{9}{4} \times 4! \\
=10 \times \frac{8!}{4!3!} \times \frac{9!}{4!5!} \times 4! \\
=10 \times 70 \times 126 \times 24 \\
\boxed{
=2116800}}$$
Total number of combinations : $$\displaylines{10^8}$$
Probability : $$\displaylines{\frac{2116800}{100000000} = 0.021168 \\ \\
∴ \boxed{\text{The probability of getting 4 repeated numbers and 4 unique number is 2.12\%}}}$$
<div style='page-break-after: always;'></div>

3. (5 points) A number $X$ is chosen at random from the set {1,2,3,4,5,6,7,...,24}. Consider the following three events:

A: $X$ is divisible by 3. 
B: $X$ is even  
C: 7 ≤ $X$ ≤ 18

Determine whether the events A, B and C are: 
(a) pairwise independent $$\displaylines{P(A \cap B) = P(A)·P(B) \\ \\
P(A) = \{3, 6, 9, 12, 15, 18, 21, 24\} = \frac{8}{24} = \frac{1}{3} \\
P(B) = \{2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24\} = \frac{12}{24} = \frac{1}{2}\\
P(A \cap B) = \{6, 12, 18, 24\} = \frac{4}{24} = \frac{1}{6} \\ \\
P(A)·P(B) = \frac{8}{24} · \frac{12}{24} = \frac{1}{3} · \frac{1}{2} = \frac{1}{6} = \frac{1}{6}  = P(A \cap B) \\ \\
∴ \boxed{\text{A and B are Independent}} \\}$$


$$\displaylines{P(A \cap C) = P(A)·(C) \\ \\
P(A) = \{3, 6, 9, 12, 15, 18, 21, 24\} = \frac{8}{24} =\frac{1}{3} \\
P(C) = \{7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18\} = \frac{12}{24} = \frac{1}{2} \\
P(A\cap C) = \{9, 12, 15, 18\} = \frac{4}{24} = \frac{1}{6}  \\ \\
P(A) ·P(B) = \frac{1}{3} · \frac{1}{2} = \frac{1}{6} = \frac{1}{6} = P(A \cap C) \\ \\
∴ \boxed{\text{A and C are Independent}}}$$



$$\displaylines{P(B \cap C) = P(B) · P(C) \\ \\
P(B) = \{2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24\} = \frac{12}{24} = \frac{1}{2} \\
P(C) = \{7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18\} = \frac{12}{24} = \frac{1}{2} \\
P(B \cap C) = \{8, 10, 12, 14, 16, 1 8\} = \frac{6}{24} = \frac{1}{4} \\ \\
P(B) · P(C) = \frac{1}{2} · \frac{1}{2} = \frac{1}{4} = \frac{1}{4} = P(A \cap C)  \\ \\
∴ \boxed{\text{B and C are Independent}}}$$

$\boxed{\text{The events A, B, and C are Pairwise Independent}}$

(b) mutually independent$$\displaylines{P(A \cap B \cap C) = P(A) · P(B) · P(C) \\ \\
P(A \cap B \cap C) = \{12, 18\} = \frac{2}{24} = \frac{1}{12}\\
P(A) · P(B) · P(C) = \frac{1}{3} · \frac{1}{2} · \frac{1}{2} = \frac{1}{12} = \frac{1}{12} = P(A \cap B \cap C) \\ \\
∴ \boxed{\text{A, B, and C are Mutually Independent}}}$$

<div style='page-break-after: always;'></div>

4. (4 points) A hunter came back from a hunt with lots of ferrets, which where kept in 10 identical boxes. One box contained 6 ferrets (5 white and one black), while each of the other nine boxes 4 ferrets (2 black and 2 white, to be precise). Just before the hunter went to bed he saw a white ferret escaping and running away. What is the probability that it escaped from the box that had 5 white ferrets.

**Events**
A : The white ferret came from the box with 5 white ferrets.
B :  The white ferret escaped.

$$\displaylines{\text{Bayes Theorem} \\
P(A|B) = \frac{P(B|A)P(A)}{P(B)} \\
P(B|A) = \frac{5}{6} \\
P(A) = \frac{1}{10} \\
P(B) = P(A)P(B|A) + P(\overline{A})P(B|\overline{A}) = \left( \frac{1}{10}· \frac{5}{6} \right) + \left( \frac{9}{10} · \frac{1}{2} \right) = \frac{5}{60} + \frac{27}{60} = \frac{8}{15} \\ \\
P(A|B) = \frac{\frac{5}{6}\times \frac{1}{10}}{\frac{8}{15}} = \frac{5}{60} · \frac{15}{8} = \frac{75}{480} = \frac{5}{32} \\ \\
∴ \boxed {\text{The probability of a white ferret escaping and coming from the box with 5 white ferrets is } \frac{5}{32}}}$$

<div style='page-break-after: always;'></div>


5. Out of 30 snipers in the service of CIA, 12 sharpshooters of Unit-A hit their target with the first shot with probability 0.6, 8 of the Unit-B – with probability 0.5, and, finally, 10 people from Unit-C – with probability 0.7. For Mission Impossible 77, sniper X was chosen at random. X managed to hit the target with the first shot. To which of the Units (A, B, or C) X belongs with the highest probability?

**Events**
A : Sniper X is from Unit-A
B : Sniper X is from Unit-B
C : Sniper X is from Unit-C
H : Sniper X hits the target on the first shot

**Probabilities**
$P(A) = \frac{12}{30}$
$P(B) = \frac{8}{30}$
$P(C) = \frac{10}{30}$
$P(H|A) = 0.6$
$P(H|B) = 0.5$
$P(H|C) = 0.7$
$$\displaylines{\text{Total probability of hitting the target} \\
P(H) = P(H|A)P(A) + P(H|B)P(B) +P(H|C)P(C) \\
=(0.6)\left( \frac{12}{30} \right) + (0.5)\left( \frac{8}{30} \right)+(0.7)\left( \frac{10}{30} \right) \\
=0.24 + 0.13 + 0.23 \\
=0.6 \\}$$


$$\displaylines{\text{Bayes Theorem} \\
P(A|B) = \frac{P(B|A)P(A)}{P(B)}}$$
$$\displaylines{P(A|H) = \frac{P(H|A)P(A)}{P(H)}
=\frac{0.24}{0.6}
=0.4 \\P(B|H) = \frac{P(H|B)P(B)}{P(H)} = \frac{0.13}{0.6} = 0.22 \\
P(C|H) = \frac{P(H|C)P(C)}{P(H)} = \frac{0.23}{0.6} = 0.38 \\ \\
∴ \boxed{\text{Sniper X most likely belongs to Unit-A with a probabiliy of 40\%}}}$$