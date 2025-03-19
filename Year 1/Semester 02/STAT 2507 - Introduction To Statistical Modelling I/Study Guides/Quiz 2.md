Section 4.8 - Chapter 7 of the assigned textbook
Chapter 4 - Part 5 to Chapter 7 - Part 2 of my lecture slides

---
#### Discrete Random Variables

A **random variable** is a numerical outcome of a random process. A **discrete random variable** is one that takes on a **countable** number of possible values (like whole numbers).

 **Key Properties**
- Values are **finite** or **countably infinite** (e.g., {0,1,2,3,...}).
- Each value has an associated **probability**.
- The sum of all probabilities must equal **1**


**Probability Mass Function (PMF)**
The **PMF** of a discrete random variable $X$, written as $P(X=x)$, gives the probability that $X$ takes on the value $x$.

Properties of PMF:
1. $P(X=x)≥0$ for all $x$ (probabilities are never negative).
2. $∑P(X=x)=1$ (the total probability of all possible outcomes equals 1).


**Expected Value (Mean) Of A Discrete Random Variable**
The **expected value** $E(X)$ (or mean) is the weighted average of all possible values of $X$, given by: $$E(X) = \sum xP(X=x)$$

**Variance and Standard Deviation**
**Variance $Var(X)$ measures how spread out the values of $X$ are: $$Var(X) = E[(X-E(X))^2] = \sum (x-E(X))^2P(X=x)$$
**Standard deviation $\sigma(X)$** is just the square root of variance: $$\sigma(X) = \sqrt{ Var(X) }$$

**Example :** Flipping Two Coins
Let $X$ represent the number of heads when flipping two coins.

Sample Space : $$S = \{TT, HT, TH, HH\}$$
Random Variable $X$: $$X = \{0, 1, 2\}$$



---
#### Common Discrete Probability Distributions

A **discrete probability distribution** describes the probabilities of all possible values of a **discrete random variable** (one that takes on countable values).


##### Bernoulli Distribution
Models a single trial with two possible outcomes: **success (1)** or **failure (0)**.

Formula : $P(X=x) = p^x(1-p)^{1-x},\; x \in \{0, 1\}$
Mean : $E(X) = p$
Variance : $Var(X) = p(1-p)$

> Example : Flipping a coin once
> - **Success** = Heads (1)
> - **Failure** = Tails (0)
> - If the probability of heads (success) is $p=0.5$, then the probability of getting heads (success) is $P(X=1) = 0.5$, and the probability of getting tails (failure) is $P(X=0) = 0.5$.



##### Binomial Distribution
Models the number of **successes** in a fixed number of **independent** Bernoulli trials. $$X \sim B(n,p)$$
Formula : $P(X = k) = \binom{n}{k}p^k(1-p)^{n-k}$
Mean : $E(X) = np$
Variance : $Var(X) = np(1-p)$ 

> Example : Tossing a fair coin 10 times and counting how many heads appear
> - **Number of trials** $n=10$
> - **Probability of success** $p=0.5$ (probability of getting heads)
> - You want to find the probability of getting exactly 6 heads in 10 flips.
> 
> For $k = 6$, $n=10$, and $p=0.5$ : $$P(X = 6) = \binom{10}{6}0.5^6(1-0.5)^{10-6} = 0.204$$


##### Geometric Distribution
Models the number of trials until the **first** success occurs.

Formula : $P(X = k) = (1-p)^{k-1}p$
Mean : $E(X) = \frac{1}{p}$
Variance : $Var(X) = \frac{1-p}{p^2}$

> **Example**: Tossing a coin repeatedly until the first heads (success) appears.
> - **Probability of success** $p=0.5$ (probability of getting heads)
> - You want to know the probability of getting the first heads on the 3rd flip.
> 
> For $k = 3$ and $p=0.5$ : $$P(X = 3) = (1-0.5)^{3-1}0.5 = 0.125$$



##### Hypergeometric Distribution
The **Hypergeometric Distribution** models the number of successes in a fixed number of trials, **without replacement**, from a finite population. $$X \sim H(N, M, n)$$
Where :
- $N$ is the total population size,
- $M$ is the number of successes in the population,
- $n$ is the number of trials (samples),
- $k$ is the number of successes you are counting.

Formula : $P(X=k) = \frac{\binom{M}{k}\binom{N-M}{n-k}}{\binom{N}{n}}$
Mean : $n\frac{M}{N}$
Variance : $n\left( \frac{M}{N} \right)\left( \frac{{N-M}}{N} \right)\left( \frac{{N-n}}{N-1} \right)$


> **Example**: A deck of 52 cards contains 26 red cards and 26 black cards. You draw 5 cards without replacement and want to know the probability that exactly 3 of them are red.
> - **Population size** $N=52$
> - **Number of red cards (successes)** $K=26$
> - **Sample size** $n=5$
> - **Number of red cards in the sample (successes)** $k=3$
> 
> For $N=52, K=26, n=5, \text{ and } k=3$ : $$P(X = 3) = \frac{\binom{26}{3}\binom{52-26}{5-3}}{\binom{52}{5}} = 0.325 $$



##### Poisson Distribution
Models the number of occurrences of an event in a fixed interval (time or space), assuming events happen at a constant average rate.

Formula : $P(X=k) = \frac{\lambda^ke^{-\lambda}}{k!}$
Mean : $E(X) = \lambda$
Variance : $Var(X) = \lambda$

> **Example**: The number of customers arriving at a store per hour, where the average rate is 3 customers per hour ($\lambda = 3$).
> - You want to know the probability that exactly 4 customers arrive in the next hour.
> 
> For $k=4$ and $\lambda = 3$ : $$P(X = 4) = \frac{3^4e^{-3}}{4!} \approx 0.168$$



##### Approximations
**The Binomial Approximation To The Hypergeometric Distribution**
	Rule : This approximation will give reasonable results when $n$ < 0.05$N$.$$X \sim H(N,M,n) \implies X \sim B\left( n, \frac{M}{N} \right)$$


**The Poisson Approximation To The Binomial Distribution**
	Rule : This approximation will give reasonable results when $np$ < 7. $$X \sim B(n,p) \implies X \sim P(\mu = np, k)$$


---
#### Continuous Random Variables

A **Continuous Random Variable** is one that can take any value within a given range or interval. Unlike discrete random variables, which take specific, countable values, continuous random variables can assume an infinite number of values within any given range

##### Probability Density Function (PDF)
For continuous random variables, the PDF $f(x)$ describes the likelihood of the variable taking a value in a small range around $x$. The area under the PDF curve over a given range represents the probability that the random variable will take a value in that range. $$P(a \le X \le b) = \int^b_{a}f(x)dx $$
##### Cumulative Distribution Function (CDF)
The CDF $f(x)$ is the probability that the random variable $X$ takes a value less than or equal to $x$. It is the integral of the PDF from negative infinity to $x$: $$F(x) = P(X \le x) = \int^x_{-\infty}f(t)dt$$

##### Common Continuous Distributions
**Uniform Distribution** 
A continuous random variable $X$ is uniformly distributed over an interval [a,b] if its PDF is constant between $a$ and $b$. $$\displaylines{X \sim U(a, b) \\
f(x) = \frac{1}{b-a},\; a \le x \le b}$$

**Exponential Distribution**
The exponential distribution models the time between events in a Poisson process (a process where events happen at a constant rate). $$\displaylines{X \sim \exp(\mu) \\ f(x) = \lambda e^{-\lambda x}, \; x\ge 0}$$

**Normal Distribution (Gaussian Distribution)**
A continuous random variable $X$ is normally distributed if its PDF follows the bell-shaped curve. It is completely described by its mean $\mu$ and standard deviation $\sigma$. $$\displaylines{X \sim N(\mu, \sigma^2) \\ f(x) = \frac{1}{\sigma \sqrt{ 2\pi }}e^{-1/2(x-\mu/\sigma)^2}, \; -\infty < X < \infty}$$


---
#### The Standard Normal Probability Distribution

The **Standard Normal Distribution** is a special case of the **Normal Distribution** with the following properties:

1. **Mean (µ)** = 0
2. **Standard Deviation (σ)** = 1

In the **Standard Normal Distribution**, $\mu = 0$ and $\sigma = 1$, so the equation simplifies to: $$f(x) = \frac{1}{\sqrt{ 2\pi }}e^{- x^2/2}$$
This is a **bell-shaped curve** that is symmetric around zero, and the total area under the curve equals 1.


**Z-Score**
This represents how many standard deviations a data point is away from the mean. The formula for the Z-score is: $$Z = \frac{x-\mu}{\sigma}$$

**The Normal Approximation To The Binomial Distribution**
The **Normal Approximation to the Binomial Distribution** is a method used to approximate a **Binomial Distribution** when certain conditions are met.

If $X \sim B(n, p)$ and $np > 5$, and $n(1‒p) > 5$ and $n$ is large, then binomial is approximately normal with $μ = np$ and $σ^2 = np(1‒p)$

---
#### Sampling Plans


---
#### Sampling Distributions
A **sampling distribution** refers to the probability distribution of a **statistic** (such as the sample mean or sample proportion) obtained from repeated random sampling from a population.


**Central Limit Theorem (CLT)**
The **Central Limit Theorem** (CLT) is one of the most important concepts in the study of sampling distributions. It states that:
- Regardless of the shape of the population distribution, the sampling distribution of the sample mean will approach a **normal distribution** as the sample size $n$ becomes large.
- This holds true even if the population distribution is not normal, as long as $n$ is sufficiently large.
$$\overline{X}^{approx} \sim N\left( \mu, \frac{\sigma^2}{n} \right)$$

Steps :
1. $n \ge 30$
2. Convert to Normal Distribution of the sample means ($\overline{X}$)
3. Calculate the Z-Score 
4. Use Z-Table to find probability


**The Sampling Distribution Of The Sampling Proportion**
The **sample proportion** ($\hat{p}$​) is a statistic used to estimate the proportion of successes in a population. If we draw a sample of size $n$ from a population, the proportion of successes in the sample is denoted by $\hat{p}$. $$\displaylines{\hat{P} = \frac{X}{n} \\
\mu_{\hat{P}} = p \\
\sigma^2_{\hat{P}} = \frac{pq}{n} \\ \\
\text{If } np \geq 5,  \text{ and } nq \geq 5, \text{ then } \hat{P}^{approx} \sim N\left( p, \frac{pq}{n} \right) }$$

