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



**The Complement Of An Event**
The **complement** of an event $A$, denoted by $A^c$, is an event that contains all outcomes in the sample space that are not in $A$.

$P(A^c)$ is the probability that $A$ does not occur.

![[Screenshot 2025-01-28 at 9.32.15 AM.png|300]]


**The Addition Rule**
If A and B are events defined on the same sample space, then $$P(A\cup B) = P(A) + P(B) - P(A \cap B)$$
If A and B are mutually exclusive events, then $$P(A \cup B) = P(A) + P(B)$$

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
6 × 6 × 6 = 216 possible outcomes.  

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


**Example :** 
Suppose we are playing Texas Hold’em and we are dealt two cards, both of which hearts. What  
is the probability that the next 3 cards are all hearts? That is, what is the probability we “flop”  
a flush?

Let $S$ represent the set of all 3-card combinations. $$n(S) = \frac{50!}{3!47!} = 19,600$$
Let $H$ represent the event that all 3 cards are hearts. $$\frac{11!}{3!8!} = 165$$
$$∴\; P(H) = \frac{n(H)}{n(S)} = \frac{165}{19,600} = 0.0084$$



---
##### Conditional Probability

A **conditional probability** is the probability of one event under the the condition that another event has occurred.

If A and B are events defined on the same sample space, then the conditional probability of the event $A$ given that event $B$ has occurred is denoted by $P(A | B)$.$$P(A|B) = \frac{P(A\cap B)}{P(B)}$$


**Example :**
A research company produced the following data about campus food preferences from a sample of 100 university students.


|               | Hamburger | Salad | Pizza |
| ------------- | --------- | ----- | ----- |
| Undergraduate | 10        | 40    | 20    |
| Graduate      | 15        | 10    | 5     |

A person is selected at random from this group. What is the probability the person... 
Let $S$ be the set of all 100 students.

(a) is an undergraduate student?  
$$P(U) = \frac{n(U)}{n(S)} = \frac{70}{100} = 70\% \text{ chance of an undergraduate student.}$$

(b) is an undergraduate student given that they prefer hamburgers?
$$P(U|H) = \frac{n(U\cap H)}{n(H)} = \frac{P(U\cap H)}{P(H)} =\frac{10}{25} = 40\%$$


**Example :** 
At one university, 46% of all students have a Netflix subscription, 34% have an Amazon  
Prime subscription, and 18% have subscriptions to both services.  

A student is chosen at random. If the student has an Amazon Prime subscription, what is the probability that  

(a) they also have a Netflix subscription?  $$P(N|A) = \frac{P(N\cap A)}{P(A)} = \frac{0.18}{0.34} \approx 0.5294$$

(b) they don’t have a Netflix subscription? $$P(N^c|A) = \frac{P(N^c\cap A)}{P(A)} = \frac{P(A) - P(A\cap N)}{P(A)} = \frac{0.34 - 0.18}{0.34} \approx 0.4706
$$$$P(N^c|A) = 1 -P(N|A) = 1 - 0.5294 \approx 0.4706$$
![[Screenshot 2025-01-29 at 8.26.08 AM.png]]



---
##### The Multiplication Rule

If $A$ and $B$ are events defined on the same sample space, then $$P(A\cap B) = P(B)P(A|B) = P(A)P(B|A)$$

**Example :** 
In a certain region, 79% of people have brown eyes and 31% of people have brown hair.  
In addition, it is known that 48% of people with brown hair also have brown eyes.  

If a person is selected at random, what is the probability they have brown eyes and brown hair?$$\displaylines{P(E) = 079 \\ P(H) = 0.31 \\ P(E|H) = 0.48 \\ P(E\cap H) = P(H)P(E|H) = 0.31 \times 0.48 = 0.1488}$$

---
##### Independent Events

Let $A$ and $B$ be events which are defined on the same sample space.  
$A$ and $B$ are said to be independent events if and only if the occurrence of B does not affect the probability of $A$, and vice versa. $$\displaylines{P(A|B) = P(A)\\\text{and} \\P(B|A) = P(B)}$$
**Multiplication Rule for Independent Events**
$A$ and $B$ are said to be independent events **if and only if** $$P(A\cap B) = P(A) \times P(B)$$
NOTE :
	Mutually Exclusive events are always dependent.


**Example :** 
Suppose we plan to draw a card at random from a standard deck of 52 playing cards.  
Let K represent the event that we draw a king.  
Let D represent the event that we draw a diamond.  

Are K and D independent events?$$\displaylines{P(K) = \frac{4}{52} = \frac{1}{13} \\
P(K|D) = \frac{P(K\cap D)}{P(D)} = \frac{1 \div 52}{13 \div 52} = \frac{1}{13} \\ \\
∴ \text{K and D are independent events}}$$

**Example :** 
Let $A$ and $B$ be events defined on the same sample space such that  $P(B) = 0.6$ and $P(A ∪ B) = 0.8$. Find $P(A)$ separately under each of the following conditions.  

(a) $A$ and $B$ are mutually exclusive events.  $$\displaylines{P(A\cup B) = P(A) + P(B) - P(A\cap B) \\
0.8 = P(A) + 0.6 - 0 \\
0.8 - 0.6 = P(A) \\
∴ P(A) = 0.2}$$ 


(b) $A$ and $B$ are independent events. $$\displaylines{P(A\cup B) = P(A) + P(B) - P(A\cap B) \\
0.8 = P(A) + 0.6 - (P(A)\times P(B|A)) \\
0.8 = P(A) + 0.6 - (P(A) \times 0.6) \\
0.2 = 0.4P(A) \\ \\
∴ P(A) = 0.5}$$

**Example :** 
Consider the system of 3 components as illustrated below. Suppose that each component functions correctly 90% of the time independently of each other component.

![[Screenshot 2025-01-29 at 10.10.26 AM.png]]

What is the probability there is a functioning path from point A to point B?

Let $E_{i}$ represent the event that component $i$ functions, where $i = 1, 2, 3$ $$\displaylines{P[E_{1}\cup(E_{2}\cap E_{3})] = P(E_{1}) + P(E_{2}\cap E_{3}) - P(E_{1}\cap(E_{2}\cap E_{3}))\\
=P(E_{1}) + P(E_{2})P(E_{3}) - P(E_{1})P(E_{2})P(E_{3}) \\
=0.9 + (0.9\times 0.9) - (0.9\times 0.9\times 0.9) \\
=0.98}$$

---
##### The Total Law Of Probability

A sequence of events $S_{1}, S_{2}, ..., S_{n}$ form a partition of a sample space $S$ if and only if the following two conditions are satisfied : $$\displaylines{1.\; S = S_{1} \cup S_{2} \cup \dots \cup S_{n} \\
2.\; S_{i} \cap S_{j} = \{\}, \text{ for } i\neq j}$$

Let $S_{1}, S_{2}, ..., S_{n}$ be a sequence of events that partition the sample space.

![[Screenshot 2025-01-29 at 11.05.50 AM.png]]

The probability of any event A can be expressed as $$P(A) = P(A\cap S_{1}) + P(A\cap S_{2}) + \dots + P(A\cap S_{n})$$
For each event $S_{i} , i = 1, 2, ..., n$, the multiplication rule tells us that $$P(A\cap S_{i}) = P(S_{i})P(A|S_{i})$$
As a result, we can rewrite the formula as $$P(A) = P(S_{1})P(A|S_{1}) + P(S_{2})P(A|S_{2}) + \dots + P(S_{n})P(A|S_{n})$$
This formula is known as **the law of total probability**.


**Example :** 
A company that manufactures smartphones produces 50% of the phones at plant A, 30%  
at plant B, and 20% at plant C. The percentages of defective smartphones at plants A, B, and C are 3%, 4%, and 12%, respectively.  

What is the probability that a randomly chosen phone will be defective?

$$\displaylines{P(A) = 0.5,\; P(D|A) = 0.03 \\ 
P(B) = 0.3,\; P(D|B) = 0.04 \\
P(C) = 0.2,\; P(D|C) = 0.12 \\ \\
P(D) = (0.5 \times 0.03) + (0.3 \times 0.04) + (0.2 \times 0.12) = 0.051}$$


---
##### Baye's Rule

Let $\{S_{1}, S_{2}, ..., S_n\}$ be a partition of a sample space.  
$P(S_{i})$ is the prior probability that $S_{i}$ occurs, $i = 1, 2, ..., n$.  

If another event $A$ occurs in the same sample space, then $P(S_{i} | A)$ is the posterior probability that $S_{i}$ occurs given that $A$ has occurred.  

We compute $P(S_{i} | A)$ using Bayes’ Rule: $$P(S_{i}|A) = \frac{P(S_{i})P(A|S_{i})}{P(S_{1})P(A|S_{1}) + P(S_{2})P(A|S_{2})+\dots+P(S_{n})P(A|S_{n})}$$

**Example :** 
A company that manufactures smartphones produces 50% of the phones at plant A, 30%  
at plant B, and 20% at plant C.  The percentage of defective smartphones at plants A, B, and C is 3%, 4%, and 12% respectively.  

If a randomly selected phone is found to be defective, what is the probability it came from plant A? $$P(A|D) = \frac{0.5 \times 0.03}{(0.5 \times 0.03) + (0.3 \times 0.04) + (0.2 \times 0.12)} = \frac{0.15}{0.051} \approx 0.2941$$

**Example :**
Suppose that 3% of a population has a specific viral infection. A test for this virus will correctly  
detect the virus 98% of the time. However, the test will indicate the presence of the virus in 1% of cases where it is actually absent.  

(a) If the test says a person has the virus, what is the probability that they actually do not have the virus?  $$\displaylines{P(V) = 0.03 \\
P(T|V) = 0.98 \\
P(T|V^c) = 0.01\\ \\
P(V^c | T) = \frac{P(V^c \cap T)}{P(T)} = \frac{P(T)P(T|V^c)}{P(V)P(T|V)+P(V^c)P(T|V^c)} \\ \\
P(V^c) = 1 - P(V) = 1 - 0.03 = 0.97 \\ \\
P(V^c|T) = \frac{0.97(0.01)}{0.03(0.98) + 0.97(.01)} = \frac{0.0097}{0.0391} \approx 0.2481
}$$

(b) If the test says a person doesn’t have the virus, what is the probability they actually do have the virus? $$\displaylines{P(V|T^c) = \frac{P(V \cap T^c)}{P(T^c)} = \frac{P(V)P(T^c|V)}{1-P(T)} \\ \\ 
P(T^c|V) = 1- P(T|V) = 1-0.98 = 0.02 \\ \\
\frac{0.03(0.02)}{1-0.0392} \approx 0.0006}$$

---
##### Probability Trees

Tree diagrams are very useful in visualizing the various sequences of  
outcomes in an experiment. A tree with appropriate probabilities and conditional probabilities  
written on the branches is called a probability tree.

![[Screenshot 2025-01-29 at 12.06.53 PM.png]]


**Example :** 
![[Pasted image 20250129121718.png]]

$$\displaylines{P(V^c|T) = \frac{P(V^c \cap T)}{P(T)} = \frac{0.0097}{0.0294 + 0.0097} \approx  0.2481}$$



**Example :** 
Suppose you have a standard deck of 52 playing cards.

(a) If you draw a card at random, what is the probability that you draw the Ace of Spades?  
$$P(A) = \frac{1}{52}$$

(b) Suppose your friend first draws a card at random and doesn’t show you the card. You now draw a card from the remaining 51 cards. What is the probability you draw the Ace of Spades?
![[Pasted image 20250129123210.png]]

$$P(Y) = 0 + \frac{1}{52} = \frac{1}{52}$$



**Example :** 
Monty Hall 3-Door Problem

Monty, the host of Let’s Make a Deal, gives a contestant a choice of three doors. Behind one of the doors is a new car. Behind the other two doors are “joke” prizes.  

The contestant picks Door #1. Monty asks, “Do you feel good about your choice? Let me help you out.” Monty then opens Door #3 to reveal a pair of dirty socks and asks, “Do you want to keep Door #1 or switch to Door #2?”  

Should the contestant keep Door #1 or switch to Door #2? Explain.

![[Pasted image 20250129124457.png]]


$$\displaylines{P(W) = \frac{1}{3} + \frac{1}{3} = \frac{2}{3} \\
P(L) = \frac{1}{3}}$$
