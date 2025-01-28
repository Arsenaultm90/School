##### The Algebra Of Events
There are three algebraic operations we can perform with events. We can take  
	▪ The intersection of two or more events,  
	▪ The union of two or more events, and  
	▪ The complement of an event.


**Venn Diagram**
**Venn diagrams** give us a way to visualize our events in relation to the sample space and each other.

**Example :** 
If we roll a fair die and observe the number of dots, then $$\displaylines{S = \{1, 2, 3, 4, 5, 6\} \\
A = \{1, 3, 5\} \\
B = \{2, 3, 6\}}$$
![[Screenshot 2025-01-28 at 9.26.00 AM.png|300]]



**The Intersection Of Two Events**
The **intersection** of two events A and B, denoted by $A \cap B$, is the set of all outcomes that are common to both $A$ and $B$.

$P(A \cap B)$ is the probability that events $A$ and $B$ occur simultaneously.

![[Screenshot 2025-01-28 at 9.27.44 AM.png|300]]



**Mutually Exclusive Events**
Two events A and B are mutually exclusive if they have no outcomes in common. That is, $$A \cap B = \{ \}$$
If A and B are mutually exclusive, then $$P(A \cap B) = 0$$
![[Screenshot 2025-01-28 at 9.30.06 AM.png|300]]



**The Union of Two Events**
The **union** of two events A and B, denoted by A ∪ B, is the set of all the outcomes that are in A or B, or both.

$P(A \cup B)$ is the probability that at least one of the two events occurs.

![[Screenshot 2025-01-28 at 9.34.06 AM.png|300]]



**The Addition Rule**
If A and B are events defined on the same sample space, then $$P(A\cup B) = P(A) + P(B) - P(A \cap B)$$
If A and B are mutually exclusive events, then $$P(A \cup B) = P(A) + P(B)$$



**The Complement Of An Event**
The **complement** of an event $A$, denoted by $A^c$, is an event that contains all outcomes in the sample space that are not in $A$.

$P(A^c)$ is the probability that $A$ does not occur.

![[Screenshot 2025-01-28 at 9.32.15 AM.png|300]]



**The Subtraction Rule**
If $A$ is any event defined on a sample space, then it follows $$\displaylines{A \cap A^c = \{\} \\ A \cup A^c = S}$$
Together, these two facts imply that $$P(A) + P(A^c) = 1 $$
Therefore, for any event A, $$P(A) = 1 - P(A^c)$$

---
##### Counting Rules

**The Fundamental Counting Principle (The Product Rule)**
Consider an experiment with $k$ number of stages.

If the first stage has $n_{1}$ possible outcomes, the second stage has $n_2$ possible outcomes, and so on, then the total number of outcomes for the entire experiment is given as $$n_{1} \times n_{2}\times \dots \times n_{k}$$
**Example :**
Consider a two-stage experiment. First, we roll a six-sided die and observe the number of dots. Next, we draw a card from a deck of cards and observe the suit. 
There are 6 × 4 = 24 possible outcomes. (Cartesian product of the two sets)


**Example :** 
Standard issue Ontario licence plates consist of 7 characters; 4 letters followed by 3 numbers.  

(a) How many such licence plates are possible?  
	$26^4 \times 10^3 = 456, 976, 000$

(b) How many of these licence plates won’t have any repeated letters or numbers?  
	$\frac{26!}{22!} \times \frac{10!}{7!} = 258, 336, 000$

(c) If I generate a standard issue licence plate at random, what is the probability that the plate won’t have any repeated letters or numbers?
	$P(A) = \frac{n(A)}{n(S)} = \frac{258,336,000}{456,976,000} \approx 0.5653$


**Example :**
Suppose we want to select three cards with replacement from a standard deck of 52 cards.  
What is the probability that at least one of the cards we select will be a face card (i.e. King, Queen, or Jack)?

Let $S$ be the set of all three card sequences. $$\displaylines{n(S) = 52 \times 52 \times 52 = 140, 608 \\
n(F^c) = 40 \times 40 \times 40 = 64,000 \\ \\
∴P(F) = 1 - P(F^c) = 1 - \frac{n(F^c)}{n(S)} = 1 - \frac{64,000}{140,608} \approx 0.5448}$$


---
##### Sampling With Replacement

Suppose we want to take a sample of $k$ objects with replacement from a group of $n$ distinct objects.$$n^k$$
**Example :** 
If we roll a six-sided die three times and observe the number of dots each time, then there are 
6 × 6 × 6 = 63 = 216 possible outcomes.  

Note that (5, 2, 2) would be considered a different outcome than (2, 5, 2) or (2, 2, 5).



---
##### Sampling Without Replacement

**Linear Permutation**
A **Linear Permutation** of a set of distinct objects is an arrangement or ordering of the objects in a linear sequence.

The number of linear permutations of $n$ distinct objects is given by $$n! = (n) \times (n-1) \times \dots \times 1$$

**Example :** 
Five students – Ahmed, Brandon, Carlos,  Daniela, and Ethan – are waiting in line at Tim Hortons to buy coffee before class.  

(a) In how many ways can I rearrange these students in a straight line?  
	$5! = 120$

(b) In how many ways can I rearrange these students in a straight line if Ahmed and Carlos must be standing next to each other?
	$2 \times 4! = 48$



---
##### Sampling Without Replacement - Permutations

Suppose we want to take a sample of $r$ objects without replacement from a population of $n$ distinct objects, and that the order of selection is relevant.$$P \binom{n}{r} = \frac{n!}{(n-r)!}$$

**Example :**
Suppose I want to create a six digit passcode for my phone using the numbers 0, 1, ..., and 9.  
In how many ways can we do this if  

(a) repeated numbers are permitted?  
	$10^6 = 1,000,000$

(b) repeated numbers are not permitted?
	$\frac{10!}{4!} = 151,200$


**Example :** 
A charity is holding a lottery in which they are giving out 20 different prizes, each worth a  
different amount of money. If 1000 tickets are sold and no ticket is allowed to win more than one prize, then in how many ways can the prizes be awarded?

$$\frac{1000!}{980!} = 8.26 \times 10^{29}$$


---
##### Sampling Without Replacement - Combinations

Suppose we want to take a sample of $r$ objects without replacement from a group of $n$ distinct objects, and that the order of selection is not relevant.$$C\binom{n}{r} = \frac{n!}{r!(n-r)!}$$

**Example :** 
To buy a Lotto MAX ticket, you must select seven numbers from the numbers 1, 2, ..., 50.  
A single ticket contains three distinct sets of seven numbers; the set you selected and two sets which are generated at random. The actual order of the numbers is irrelevant.  

(a) In how many ways can you do this?  
	$\frac{50!}{7!43!} = \frac{50 \times 49 \times 48 \times 47 \times 46 \times 45 \times 44}{7 \times 6 \times 5 \times 4 \times 3 \times 2 \times 1} = 99, 884, 400$

(b) If you buy a single ticket, what is the probability you win?
	$n(W) = 3,\; P(W) = \frac{n(W)}{n(S)} = \frac{3}{99,884,400} = 0.00000003$



**Example :** 
A psychologist wishes to conduct an experiment to investigate differences in problem solving between the sexes. All subjects will be required to solve the same problem.  

There are 15 females and 11 males available from which to select the subjects. In order to complete the experiment, the psychologist needs 3 female and 3 male subjects. In how many ways can the subjects be selected?
$$\frac{15!}{3!12!} \times \frac{11!}{3!8!} = 455 \times 165 = 75, 075$$

Let $S$ represent the set of all 3-card combinations. $$n(S) = \frac{50!}{3!47!} = 19,600$$
Let $H$ represent the event that all 3 cards are hearts. $$\frac{11!}{3!8!} = 165$$
$$∴\; P(H) = \frac{n(H)}{n(S)} = \frac{165}{19,600} = 0.0084$$



---
##### Conditional Probability


