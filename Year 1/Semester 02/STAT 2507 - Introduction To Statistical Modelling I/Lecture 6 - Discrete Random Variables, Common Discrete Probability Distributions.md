##### Discrete Random Variable

A **random variable** is a quantitative variable whose value corresponds to outcome of a random experiment.

A random variable is said to be discrete if it can assume only a finite or countably infinite number of distinct values.


---
##### DIscrete Probability Distributions

The probability distribution of a discrete random variable, X, is a table, graph, or formula that tells us  :
	▪ the values that X can assume, and  
	▪ the probability with which X assumes each of those values.  

We use the notation P(X = x), or simply p(x), to represent the probability that the discrete random variable X takes on the constant value x.

The probability distribution of a discrete random variable X must satisfy the following two conditions: $$\displaylines{a)\; 0 \leq P(X=x) \text{ for all values of x}\\
b)\; \sum P(X=x) = 1}$$
For a discrete random variable that can assume only a finite number of values, we can represent its probability distribution graphically or by using a probability table.

**Example:** 
If X represents the number of “heads” in two flips of a fair coin, then we can represent the probability distribution of X as  follows:

![[Screenshot 2025-02-10 at 9.41.40 AM.png]]


**Example :** 
A basketball player successfully makes a shot with probability 0.7 independently of each other attempt.  

The player takes three shots. Let X represent the total number of successfully made shots.  
What is the probability distribution of X?

$M$ - Made shot
$M^c$ - Miss Shot
$x$ - Number of shots made

| x   | p(x)                                           | Outcome     |
| --- | ---------------------------------------------- | ----------- |
| 0   | $0.3 \times 0.3 \times 0.3$ = 0.027            | $M^cM^cM^c$ |
| 1   | $(0.3 \times 0.3 \times 0.7) \times 3$ = 0.189 | $M^cM^cM$   |
| 2   | $(0.3 \times 0.7 \times 0.7) \times 3$ = 0.441 | $M^cMM$     |
| 3   | $0.7 \times 0.7 \times 0.7$ = 0.343            | $MMM$       |


**Example :** 
Three people go to a party and give the host their hats. At the end of the night, the host  
hands back the hats at random.  

Let X represent the number of people that get the correct hat back. What is the probability  
distribution of X?

**Solution :** 
There are 3! possible permutations of giving the hats back.

0 people got their hats back - (2, 3, 1), (3, 1, 2)
1 person got their hat back - (1, 3, 2), (3, 2, 1), (2, 1, 3)
2 people got their hat back - ()
3 people got their hat back - (1, 2, 3)

| x   | p(x)          | Outcome     |
| --- | ------------- | ----------- |
| 0   | $\frac{1}{3}$ | $H^cH^cH^c$ |
| 1   | $\frac{1}{2}$ | $HH^cH^c$   |
| 2   | 0             | $HHH^c$     |
| 3   | $\frac{1}{6}$ | $HHH$       |



---
##### Computing Probabilities with Discrete Random Variables

We are often interested in the probability that a discrete random variable X will assume a value within a specific range of values.  

To compute such probabilities, find the sum of the probabilities associated with the range of X in which we are interested.

**Example :** 
From Exercise 1, $$P(X \leq 1) = P(X=0) + P(X=1) = 0.027 + 0.189 = 0.216$$

**Example :**
A bag contains two green marbles and three red marbles. You are going to randomly select marbles from the bag without replacement until you select a green marble.  

X - Number of draws 

| X   | p(X)           |
| --- | -------------- |
| 1   | $\frac{2}{5}$  |
| 2   | $\frac{3}{10}$ |
| 3   | $\frac{1}{5}$  |
| 4   | $\frac{1}{10}$ |

What is the probability it will take you  
(a) at least two draws to select a green marble?  
$$\displaylines{P(X \geq 2) = P(X=2) + P(X=3) + P(X=4) \\= 0.3 + 0.2 + 0.1 = 0.6}$$

(b) more than two draws to select a green marble?
$$P(X > 2) =0.2 + 0.1 = 0.3 $$



---
##### The Expected Value of a Random Variable

The mean or expected value of a discrete random variable $X$ is a weighted average of the possible values of the random variable.

We calculate the expected value of X as : $$\mu_{x} = E(X) = \sum xP(X=x)$$

**Example :** 
Let X represent the number of dots that appear when we roll a fair die. What is the expected value of X?


| X   | P(X)          |
| --- | ------------- |
| 1   | $\frac{1}{6}$ |
| 2   | $\frac{1}{6}$ |
| 3   | $\frac{1}{6}$ |
| 4   | $\frac{1}{6}$ |
| 5   | $\frac{1}{6}$ |
| 6   | $\frac{1}{6}$ |
$$\displaylines{\sum xP(X=x) \\
= 1 \times \frac{1}{6} + 2 \times \frac{1}{6} + \dots+6 \times \frac{1}{6} \\
\frac{21}{6} = 3.5}$$


**Example :** 
Based on past receipts, a pizza restaurant estimated the probability a random customer orders a certain number of toppings, y, in addition to cheese as follows:

| y    | 0    | 1    | 2    | 3    | 4    | 5    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| p(y) | 0.05 | 0.10 | 0.15 | 0.35 | 0.25 | 0.10 |

Assuming this probability distribution holds for all future customers, what is the expected number of toppings ordered by each customer? $$\displaylines{\sum xP(X=x) \\ 
0 · 0.5 + 1 · 0.10 + 2 ·0.15 + 3 · 0.35 + 4 ·0.25 + 5 ·0.10 \\
= 2.95}$$


---
##### The Variance of a Discrete Random Variable

The mean describes only one aspect of the distribution of values assumed by a random variable X. We must also take into account  the amount of variation in the values of X about $\mu_{x}$.

The variance of X can be computed as : $$\displaylines{\sigma^2_{x} = V(X) = E[(X-\mu_{x})^2] = \sum(x-\mu_{x})^2P(X=x)}$$
The standard deviation of X is the positive square root of $\sigma^2_{x}$, and is denoted by $\sigma_{x}$.

An equivalent and often more computationally convenient way to compute variance is as follows:
$$\sigma^2_{x} = E(X^2) - [E(X)]^2 = E(X^2) - \mu^2_{x}$$
where, $$E(X^2) = \sum x^2P(X=x)$$


**Example :** 
Based on past receipts, a pizza restaurant estimated the probability a random customer orders a certain number of toppings, y, in addition to cheese as follows:

| y    | 0    | 1    | 2    | 3    | 4    | 5    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| p(y) | 0.05 | 0.10 | 0.15 | 0.35 | 0.25 | 0.10 |
Assuming this probability distribution holds for all future customers, what is the standard deviation of the number of toppings ordered by each customer?

| $y^2$       | 0   | 1    | 4    | 9    | 16  | 25  |
| ----------- | --- | ---- | ---- | ---- | --- | --- |
| $y^2P(Y=y)$ | 0   | 0.10 | 0.60 | 3.15 | 4   | 2.5 |
$$E(y^2) = \sum^n_{k=0}y^2P(Y=y) = 10.35$$
$$[E(y)]^2 = 2.95^2$$
$$\sigma^2_{y} = 10.35 - 2.95^2 = 1.647$$
$$\sigma_{y} = \sqrt{ 1.647 } \approx 1.2835$$



---
#### Common Discrete Probability Distributions

##### The Binomial Probability Distribution  

A binomial experiment possesses the following properties:  
1. The experiment consists of a fixed number of identical trials, $n$.  
2. Each trial results in one of two outcomes, success or failure.  
3. The trials are independent.  
4. The probability of success on each trial, $p$, remains constant from trial to trial. The probability of failure is $q = 1 – p$.  

If we let $X$ represent the total number of successes in a binomial experiment, then we say $X$ follows a binomial distribution with parameters $n$ and $p$, or $X$ ~ $B(n, p)$.

If $X$ ~ $B(n, p)$, then the probability of obtaining exactly $k$ successes is given by the function : $$P(X=k) = C^n_{k}p^kq^{n-k}$$for $k = 0, 1, ..., n$.

In addition, $\mu_{x} = np$ and $\sigma^2_{x} = npq$


**Example :** 
Suppose you are writing a multiple choice test with six questions, each question having four  
possible answers.  

Let $X$ represent the total number of correct answers
$X$ ~ $B(6, 0.25)$

If you answer each question purely by guessing,  
(a) what is the expected number of correct answers?  
$$E(X) = \mu_{x} = np = 6·0.25 = 1.5$$

(b) find the probability that you will get at least three correct answers.
$$\displaylines{P(X \geq 3) = 1 - P(X < 3) = 1 - [P(X=0)+P(X=1) +P(X=2)] \\
=1 - [C^6_{0}0.25^00.75^6 + C^6_{1}0.25^10.75^5 + C^6_{2}0.25^20.75^4] \\
= 1 - [0.1780+0.3560 + 0.2966]\\ \approx 0.169}$$


---
##### The Hypergeometric Probability Distribution  

A hypergeometric experiment possesses the following properties:  
1. A random sample of size n is selected without replacement from a population of size N.  
2. The population contains M successes and N – M failures.  

Let X represent the total number of successes in a hypergeometric experiment. Then X follows a hypergeometric distribution with parameters N, M, and n, or X ~ H(N, M, n).


If X ~ H(N, M, n) , then the probability of obtaining exactly $k$ successes is given by $$P(X=k) = \frac{C^M_{k}C^{N-M}_{n-k}}{C^N_{n}}$$
for k = 0, 1, ..., n where $x \leq M$ and $n \leq N$.

In addition, $$\displaylines{\mu_{x} = n\frac{M}{N} \\ \\
\sigma^2_{x} = n(\frac{M}{N})(\frac{N-M}{N})(\frac{N-n}{N-1})}$$

**Example :**
An urn contains 12 red balls and 18 blue balls. Six balls are drawn at random from the urn. What is the probability that at least four of the balls are blue?

Let $X$ represent the number of blue balls.
$X$~$H(N=30, M=18, n=6)$

$$\displaylines{P(X \geq 4) = P(X=4) + P(X=5) + P(X=6) \\ \\
\frac{C^{18}_{4}C^{12}_{2}}{C^{30}_{6}} + \frac{C^{18}_{5}C^{12}_{1}}{C^{30}_{6}} + \frac{C^{18}_{6}C^{12}_{0}}{C^{30}_{6}} \\ \\
\approx 0.3401 + 0.1732 + 0.0313 \\
\approx 0.545}$$




---
##### The Binomial Approximation to the Hypergeometric Distribution 

In a hypergeometric experiment, the probability of success changes with each selection from the population.  

However, when N is very large relative to n, the probability of success does not change significantly with each selection, and it is acceptable to use the binomial distribution as an approximation to the hypergeometric distribution.

If X ~ H(N, M, n) and N >> n, then X ~ B(n, M/N)

**Rule of Thumb:** This approximation will give reasonable results when n is less than 0.05N.


**Example :** 
Roll Up The Rim To Win! Suppose that Tim Hortons produces 600,000,000 cups for  
their annual contest, and that 100,000,000 of them are actually winners.  

If you buy seven cups of coffee in a week, what is the probability that you’ll win a prize at least once?


---
##### The Poisson Probability Distribution  

Consider a fixed interval of time or space in which events  
1. occur at random.  
2. have a known average rate of occurrence $\mu$.  

If we let X represent the total number of events over that fixed  
interval, then we say that X follows a Poisson distribution with  
parameter $\mu$, or X ~ Poisson($\mu$ ).


If X ~ Poisson($\mu$), then the probability of obtaining exactly x successes in the specified interval is given by $$P(X=k) = \frac{e^{-\mu}\mu^k}{k!}$$
for k = 0, 1, 2, ...

In addition, $$\mu_{x} = \sigma^2_{x} = \mu$$


**Example :** 
The number of students that arrive to my office hours follows a Poisson distribution with an average of three student every 20 minutes.  

(a) What is the probability that at least four students arrive in the next 20 minutes?  

(b) What is the probability that exactly two students arrive in the next 10 minutes?



---
##### The Poisson Approximation to the Binomial Distribution

If X ~ B(n, p) where n is very large and p is very small, then  $$X \approx \text{ Poisson}(\mu = np) $$
**Rule of Thumb:** This approximation will give reasonable results when np < 7.


**Example :** 
A producer of fireworks claims that each of their fireworks only has a 1% chance of being  
defective. Consider a random sample of 500 fireworks.  

Assuming the claim made by the producer is true, find the probability that exactly six of the  
fireworks are defective using  

(a) the binomial distribution.  

(b) the Poisson approximation to the binomial distribution.