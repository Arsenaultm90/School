**Probability** is a value between 0 and 1, inclusive, that represents relative likelihood of an event.
The probability of an event is the long-term proportion of the time that the event will occur. 

**Odds in favour** of an event is the ratio of the probability the event will occur to the probability the event will not occur.

Example : Roll a fair six-sided die

The **probability** of rolling a 3 is $\frac{1}{6}$.
The **odds in favour** of rolling a 3 is $\frac{1}{6}$ : $\frac{5}{6}$, or $\frac{1}{5}$.


---
##### Random Experiment
A **random experiment** is any process that has at least two possible outcomes, and where the outcome is not known in advance. It is the process by which a measurement is obtained.

**Examples :** 
	Flip a coin and observe the resulting face.
	Count the number of defective parts in a shipment of 100 parts.
	Measure how long you can hold your breath.



---
##### Sample Space
The **sample space** of an experiment, denoted by $S$, is the set of all possible outcomes of the experiment.

The outcomes included in the sample space must be :
	Mutually exclusive; that is, no two outcomes may occur simultaneously
	Exhaustive; that is, the experiment must result in one of the outcomes in $S$.


**Examples :** 
	If we draw a card from a standard deck of 52 cards and observe the suit of the card, then the set of all possible outcomes is : $$\displaylines{\text{Qualitative}  \\S = \{\spadesuit,\heartsuit, \clubsuit, \diamondsuit \}}$$
	If we roll a standard six-sided die and observe the number of dots on the top face, then the set of all possible outcomes is : $$\displaylines{\text{Quantitative Discrete} \\ S = \{1, 2, 3, 4, 5, 6\}}$$
	If we record the amount of time, in minutes, that a single student spends writing a 2-hour midterm exam, then the set of all possible outcomes is : $$\displaylines{\text{Quantitative Continuous} \\ S = [0, 120]}$$


---
##### The Probability Of An Outcome

Consider a finite sample space $$S = \{E_{1}, E_{2}, \dots, E_{n}\}$$
where $$n \geq 2$$
To each outcome, $E$,  in the sample space, we assign probability, $P(E)$, such that $$\displaylines{0 \leq P(E_{i}) \leq 1 \text{, for } i = 1, 2, \dots, n \\ \\
P(E_{1}) + P(E_{2}) +\dots+ P(E_{n}) = 1}$$
For a given experiment, the **probability of an outcome** is the proportion of the time we would expect the outcome to occur if we were to repeat the experiment ad infinitum.


**Example :** 
A person given a new drug will have one of the following reactions either experience a complete recovery, a decrease in symptoms, no change in symptoms, or an adverse reaction. 

The probability of a complete recovery is the same as that of no change in symptoms. The probability of a decrease in symptoms is 5 times more likely than the probability of a complete  
recovery. The probability of an adverse reaction is one-tenth as likely as that of a complete recovery. 

Determine the probability of each of these four possible reactions to  
the new drug.

Outcomes : $$S = \{C, D, N, A\}$$
$$\displaylines{P(C) = P(N) \\ P(D) = 5P(C) \\ P(A) = \frac{1}{10}P(C) \\ \\
P(C) + P(D) + P(N) + P(A) = 1 \\
P(C) + 5P(C) + P(C) + \frac{1}{10}P(C)= 1 \\
10P(C) + 50P(C) +10P(C) + P(C) = 10 \\
P(C) = \frac{10}{71} \\ \\
∴ P(N) = \frac{10}{71}\\
P(D) = 5\times\frac{10}{71} = \frac{50}{71} \\
P(A) = \frac{1}{10}\times \frac{10}{71} = \frac{1}{71}}$$


---
##### Methods Of Assignment Probability To An Outcome

**Classical Method**
The **Classical Method** assigns probability to each outcome based on the assumption that the sample space is equiprobable, that is, all of the outcomes in the sample space are equally as likely.

For an equiprobable sample space with $n$ outcomes, each outcome is assigned a probability of $\frac{1}{n}$.

**Examples :**
	1. If we flip a fair coin and observe the resulting face, then $$S = \{H, T\}$$
	Since the coin is fair, the classical method sets $$P(H) = P(T) = \frac{1}{2}$$
	2. If we draw a card a random from a 52 card deck and observe the suit, then $$S = \{\spadesuit, \heartsuit, \clubsuit, \diamondsuit\}$$
	The classical outcomes would assign a probability of $\frac{1}{4}$.



**Relative Frequency Method**
The **Relative Frequency Method** estimates the probability of an outcome with the relative frequency of that outcome as obtained through repeated experiment.

If we repeat the experiment $n$ times and observe the outcome of interest $k$ times, then the estimated probability of the outcome is $\frac{k}{n}$.

**Example :** 
In a random sample of 5000 registered voters in Ontario, 1085 say they will vote for the NDP during the next provincial election. Based on this, we estimate that the probability the next  
randomly selected voter will vote NDP is 1085/5000 or 0.217.



---
##### The Law of Large Numbers
**The law of large numbers** states that as the number of independent trials of an experiment approach infinity, the relative frequency of an outcome will approach the actual probability of that outcome.

**Example :**
Flip a fair coin. Estimate the probability of obtaining “heads” by using the relative frequency method with n = 10, 100, 1000, and 10,000.


---
##### Events
An **Event** is any subset of a sample space $S$.

Example : 
If we flip a coin two times and observe the resulting face, then the sample space is given by $$S = \{HH, HT, TH, TT\}$$

**The Probability Of An Event**
For any finite sample space $S$, the probability of an event $A$, denoted by $P(A)$, is the sum of the probabilities of the individual outcomes contained within $A$.

It follows that $0 ≤ P(A) ≤ 1$ for any event $A$.


**Events and Equiprobable Sample Spaces**
If $S$ is an equiprobable sample space and $A$ is an event on $S$, then $$P(A) = \frac{n(A)}{n(S)}$$
where $n(A)$ and $n(S)$ represent the number of outcomes in $A$ and $S$, respectively.


**Example :** 
A person given a new drug will have one of the following reactions either experience a complete  
recovery, a decrease in symptoms, no change in symptoms, or an adverse reaction.

For a randomly selected patient, we have that  $$\displaylines{S = \{C ,D, N, A\} \\
P(C) = P(N) = \frac{10}{71} \\
P(D) = \frac{50}{71} \\
P(A) = \frac{1}{71}}$$
Let $H$ represent the event that the new drug is at least somewhat helpful. Find $P(H)$. $$\displaylines{H = \{C, D\} \\ P(H) = P(C) + P(D) = \frac{10}{71} + \frac{50}{71} = \frac{60}{71}}$$


**Example :** 
Consider the experiment where we roll a fair die once and observe the number of dots that appear on the top face of the die.  

Let A be the event that we roll an even number of dots. Find P(A). $$\displaylines{S = \{1, 2, 3, 4, 5, 6\} \\ 
A = \{2, 4, 6\} \\ \\
P(A) = \frac{n(A)}{n(S)} = \frac{3}{6} = \frac{1}{2}}$$
This method only works because the events are **Equiprobable**. If the events are not equiprobable we can use $$P(A) = P(2) + P(4) + P(6) = \frac{1}{6} + \frac{1}{6} + \frac{1}{6} = \frac{1}{2}$$


