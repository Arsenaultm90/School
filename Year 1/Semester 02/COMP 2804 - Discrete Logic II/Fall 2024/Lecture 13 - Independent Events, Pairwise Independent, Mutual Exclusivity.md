**Definition :** 
Events $A$ and $B$ are independent iff $$P(A\cap B) = P(A)·P(B)$$
If $A$ and $B$ are independent and $P(B) > 0$, then $$P(A|B) = \frac{P(A\cap B)}{P(B)} = \frac{P(A)·P(B)}{P(B)} = P(A)$$
If $P(A\cap B) \neq P(A)·P(B)$, then $A$ and $B$ are not independent.



**Example :**
Roll two six-sided dice, d1 & d2

$$\displaylines{S = \{(d_{1}, d_{2}) : d_{1},d_{2} \in \{1, 2,3, 4, 5, 6\}\} \\|S| = 36}$$
$A$ = "$d_{1} = 6$" = $$\displaylines{\{(6, 1), (6, 2), (6, 3), (6, 4), (6, 5), (6, 6)\} \\
P(A) = \frac{|A|}{|S|} = \frac{6}{36} = \frac{1}{6}}$$
$B$ = "$d_{2} = 4$" = $$\displaylines{\{(1, 4), (2, 4),(3, 4), (4, 4), (5, 4), (6, 4)\} \\
P(B) = \frac{|A|}{|S|} = \frac{6}{36} = \frac{1}{6}}$$
$$\displaylines{A\cap B = \{(6, 4)\} \\ (A\cap B) =  \frac{|A\cap B|}{|S|} = \frac{1}{36}}$$

Test independence : $$\displaylines{P(A\cap B) = P(A)·P(B) = \frac{1}{6}·\frac{1}{6} = \frac{1}{36}}$$
∴ $A$ and $B$ are independent.




**Example :** 
Roll two six-sided dice, d1 & d2

$$\displaylines{S = \{(d_{1}, d_{2}) : d_{1},d_{2} \in \{1, 2,3, 4, 5, 6\}\} \\|S| = 36}$$

$A$ = "$d_{1} + d_{2} = 7$"

$B$ = "$d_{1} = 4$"

A and B are independent. 



---
**Claim :**
	If $A$ and $B$ are independent, then $A$ and $\overline{B}$ are independent. $$P(A\cap \overline{B}) = P(A)·(1-P(B))$$


---
#### Pairwise Independence
**Definition :**
A sequence of events $A_{1}, \dots, A_{n}$ are pairwise independent if for every $i, j \in \{1, \dots, n\} i \neq j$
$$P(A_{i}\cap A_{j}) = P(A_{i})·P(A_{j})$$

Definition : 
$A_{1}, \dots, A_{n}$ are mutually independent for every sequence of integers. $$\displaylines{1 \leq i_{1} < i_{2} < \dots < i_{t} \leq n \\
P(A_{i_{1}}\cap\dots\cap A_{i_{n}}) = P(A_{i_{1}}\times  \dots \times A_{i_{n}})}$$

**Example :**
$b_{1}, b_{2}$ is a random bitstring of length 2.
$$\displaylines{S=\{00, 01, 10, 11\} \\
A = \text{"}b_{1} = 1\text{"} = \{10, 11\} \\
B= \text{"}b_{2}=1\text{"} = \{01, 11\} \\
C = \text{"}(b_{1}+b_{2} \text{ mod 2} = 1)\text{"} = \text{"}b_{1}\neq b_{2}\text{"} = \{01, 10\}. \;
P(C) = \frac{2}{4}=\frac{1}{2} }$$
$$\displaylines{P(A\cap B) = \{11\} = \frac{1}{4} = P(A)·P(B)\; \rightarrow \text{A and B are independent} \\
P(B\cap C) = \{01\} = \frac{1}{4} = P(B)·P(C) \rightarrow \text{B and C are independent} \\
P(A\cap C) = \{10\} = \frac{1}{4} = P(A)·P(B) \rightarrow \text{A and C are independent} }$$
∴ A, B, and C are pairwise independent.

$$P(A\cap B\cap C) = P(0) = 0 \neq \frac{1}{8} = P(A)·P(B)·P(C)$$

∴ A, B, and C are not mutually independent.




**Example :** 
**Scenario 1** :
Annie, Boris, and Charlie write a 1-question multiple choice exam.

A = "Annie gets the right answer" = $P(A) = P(B) = 0.9 = \frac{9}{10}$
B = "Boris get the right answer"
C = "Charlie gets the right answer" = $P(C) = 0.6 = \frac{6}{10}$

What is the probability that at least two students get the answer right?
$$\displaylines{P((A\cap B)\cup(A\cap C)\cup(B\cup C)) \\
= P(A\cap B) + P(A\cap C) + P(B\cap C) - 2·P(A\cap B\cap C) \\
=P(A)·P(B) + P(A) ·P(C) + P(B)·P(C) - 2·P(A) ·P(B)·P(C)  \\
=\frac{9}{10}· \frac{9}{10} + \frac{9}{10} · \frac{6}{10} + \frac{9}{10} · \frac{6}{10} - 2 · \frac{9}{10} · \frac{9}{10} · \frac{6}{10} \\
\frac{459}{500} = 0.918}$$


**Scenario 2 : Charlie copies Annie's answer**
What is the probability that at least two students get the answer right?
$$\displaylines{P\left( A \right) = \frac{9}{10} = 0.9}$$