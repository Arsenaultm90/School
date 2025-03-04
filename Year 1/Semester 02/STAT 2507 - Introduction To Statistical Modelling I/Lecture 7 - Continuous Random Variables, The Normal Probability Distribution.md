
---
#### Continuous Random Variable

A **continuous random variable** is a random variable that can assume any value within a continuous interval of values. Continuous random variables are used when the event of interest is measured on a continuous scale.

**Contents :**
	▪ Continuous Random Variables  
	▪ Probability Density Functions  
	▪ The Uniform Probability Distribution  
	▪ The Exponential Probability Distribution
	

---
#### Probability Density Function

We model the probability distribution of a continuous random variable with a continuous function known as a probability density function.

We consider the probability that a continuous random variable X assumes a value within an interval of values.

The function f (x) is the probability density function of the continuous random variable X if P(a < X < b) is the area under the curve f (x) over the interval [a, b].

Every probability density function f(x) must satisfy these two conditions:  
1. f (x) ≥ 0 for all values of x.  
2. The total area under the curve is equal to 1.


**Example :**
Consider the continuous probability distribution given below for some random variable X which can assume values in the interval [0, 5].  

(a) What is the height $h$ of the function?  
$$\displaylines{\text{ Area = }l \times h \\
5h = l \\
= h = \frac{1}{5}}$$

(b) What is $P(3 < X < 5)$?
$$\displaylines{(5-3) \times \frac{1}{5} = \frac{2}{5} = 0.4}$$
![[Drawing 2025-03-04 07.35.28.excalidraw]]




---
#### The Uniform Distribution

The **Uniform Distribution** is a **continuous probability distribution** where all values within a certain range are equally likely to occur. It is often referred to as a **rectangular distribution** because its probability density function (PDF) is constant over the given range.


**Definition :**
A continuous random variable $X$ follows a **Uniform Distribution** over the interval [a,b], written as: $$X \sim U(a, b)$$
This means that $X$ can take any value in the range [a,b] with equal probability.


**Probability Density Function :** 
$$\displaylines{f(x) = \begin{cases}
\frac{1}{U-L} \text{ for } L \leq x \leq U \\ \\
0, \text{ otherwise}
\end{cases}}$$
where, $$\displaylines{\mu_{x} = L+\frac{U}{2} \\
\sigma^2_{x} = \frac{(U-L)^2}{12}}$$![[Drawing 2025-03-04 08.01.26.excalidraw]]

**Example :** 
From the time you arrive to your bus stop, the amount of time you will wait for a bus to arrive  
is uniformly distributed over the next 15 minutes.  

Let X represent the amount of time you wait.  $$X \sim U(0, 15)$$

(a) What is the probability that you will be waiting for at least five minutes? 
![[Drawing 2025-03-04 08.10.20.excalidraw]] $$\displaylines{P(X \geq 5) = (15-5)\times \frac{1}{15} \\ 
=\frac{10}{15} = \frac{2}{3}}$$

(b) Suppose that you have already been waiting for five minutes. What is the probability you will have waited for no more than 10 minutes in total when the bus finally arrives? $$\displaylines{P(X \leq 10 | X \geq 5) = \frac{P(X \leq 10 \cap X \geq 5)}{P(X \geq 5)} = \frac{P(5 \leq X \leq 10)}{P(X \geq 5)} \\
P(5 \leq X \leq 10) = (10-5) \times \frac{1}{15} = \frac{5}{15} = \frac{1}{2} \\
P(X \geq 5) = \frac{10}{15} \\
\left( \frac{\frac{5}{15}}{\frac{10}{15}} \right) = \frac{5}{10} =  \frac{1}{2} = 0.5}$$



---
#### The Exponential Distribution

The **exponential distribution** is a continuous probability distribution that models the time between events in a Poisson process, meaning events occur **randomly and independently** at a constant average rate.


**Definition :** A random variable X is said to have an exponential distribution with mean $\mu$  or $$\displaylines{X \sim \exp(\mu)}$$
if it has probability density given by $$\displaylines{f(x) = \begin{cases}
\frac{1}{\mu}e^{-x/\mu} \text{    for } x \geq 0 \\
0, \text{   otherwise}
\end{cases}}$$
If $X \sim exp(\mu )$, then for any $a > 0$ it can be shown that $$P(X > a) = e^{-a/\mu}$$
In addition $$\displaylines{\mu_{x} = \mu \\ \sigma^2_{x} = \mu^2}$$


**Example :**
A company that sells computer believes the time to failure of their laptop computers can be modelled by an exponential distribution, with an average time to failure of 5.4 years.  

(a) If the company offers a 1 year warranty on their laptops, what proportion of laptops will be returned for repair within the warranty period?  
$$\displaylines{X \sim \exp(\mu = 5.4) \\ P(X \leq 1) \\ \\
P(X \leq 1) = 1 - P(X>1) = 1 - e^{-1/5.4} \approx 1 - 0.831 = 0.169}$$

(b) Twenty percent of laptops last longer than how many years? $$\displaylines{P(X > x) = 0.2 \\ \\
e^{-x/5.4} = 0.2 \\
\ln e^{-x/5.4} = \ln 0.2 \\
-\frac{x}{5.4} = \ln 0.2 \
x = -5.4 \times \ln 0.2 \\
\approx 8.69 \text{ years}}$$



---
#### Normal Probability Distribution

The **normal probability distribution**, also known as the **Gaussian distribution**, describes a continuous random variable that is symmetrically distributed around its mean.

**Content :**
	▪ The Normal Distribution  
	▪ The Standard Normal Distribution  
	▪ Cumulative Probabilities for the Standard Normal Distribution  
	▪ Percentiles of a Normal Distribution  
	▪ The Normal Approximation to the Binomial Distribution


A continuous random variable X is said to follow a normal probability distribution with mean $\mu$ and variance $\sigma^2$ if the probability density function of X is given by : $$f(x) = \frac{1}{\sigma \sqrt{ 2\pi }}e^{-1/2(x-\mu/\sigma)^2} \text{ for } -\infty < X < \infty$$
Denoted by : $$X \sim N(\mu, \sigma^2)$$

---
#### The Standard Normal Probability Distribution

The standard normal random variable, denoted by Z, is a normal random variable with a mean of 0 and a variance of 1.

The probability curve for Z is given by : $$f(z) = \frac{1}{\sqrt{ 2\pi }} e^{-1/2Z^2} \text{ for } -\infty < Z < \infty$$

##### Z-Score
The z-score tells us how many standard deviations a value of $X$ is away from the mean, and in which direction.  

It allows us to restate a problem involving a normal random variable $X$ in terms of the standard normal random variable $Z$.
$$Z = \frac{X-\mu}{\sigma}$$


**Example :** 
A restaurant wishes to monitor the temperature of the coffee it serves. Coffee temperatures follow a normal distribution with a mean of 71.21°C and a standard deviation of 2.98°C.  

(a) What proportion of all cups of coffee will have temperatures greater  
than 78°C?  

Let $x$ represent the temperature of a randomly selected cup of coffee.
$$\displaylines{X \sim N(\mu=71.21, \sigma =2.98) \\ \\
P(X > 78) = P(Z > \frac{78-71.21}{2.98}) \\ 
\approx P(Z > 2.28)}$$


(b) What is the probability that a randomly selected cup of coffee has a  
temperature between 68°C and 73°C?
$$\displaylines{P(68 < X < 73) \\ \\
\text{ Change to 'Z' domain :}\\
P(\frac{68-71.21}{2.98} < Z < \frac{73 - 71.21}{2.98}) \\
\approx P(-1.08 < Z < 0.60) \\ \\
\text{Using table lookup :} \\
P(Z < 0.60) - P(Z < -1.08) \\
=0.7257 - 0.1401 \\
= 0.5856}$$



---
#### Percentiles Of A Normal Distribution

Sometimes we will encounter a situation where we are required to find the value of a normal random variable that possesses a certain area (i.e. probability) to the left or to the right of it.  

To obtain this value, we use the same steps we used to find probabilities, but essentially in the reverse order.


**Example :**
Solve for z in each case below.  
	(a) P(Z < z) = 0.7939  
	(b) P(Z < z) = 0.1469  
	(c) P(Z > z) = 0.8186  
	(d) P(– z < Z < z) = 0.95



**Example :** 
A company sells “1 kg” bags of sugar. The amount of sugar contained a bag is normally distributed with a mean of 1.0522 kg and standard deviation of 0.0201 kg.  

Let $X$ represent the weight of a bag of sugar.
$$X \sim N(\mu =1.0522, \sigma = 0.0201)$$

(a) Find the weight such that only 2.5% of all bags fall below this weight.  
$$\displaylines{P(X < x) = 0.025 \\
Z = -1.96 \text{ From table} \\ \\
Z = \frac{x-\mu}{\sigma} \\
-1.96= \frac{x - 1.0522}{0.0201} \\
x = (-1.96  \times 0.0201) + 1.0522 \\
\approx 1.013kg}$$

(b) Ten percent of all bags of sugar fall above what weight?
$$\displaylines{Z = 1.28 \text{ From table} \\
Z = \frac{x-\mu}{\sigma} \\
1.28 = \frac{x-1.0522}{0.0201} \\
x = (1.28 \times 0.0201) + 1.0522 \\
\approx 1.078kg}$$



---
#### The Normal Approximation To The Binomial Distribution

The **Normal Approximation to the Binomial Distribution** is a method used to approximate a **Binomial Distribution** when certain conditions are met.

The Normal Approximation is appropriate when :
1. The sample size $n$ is large enough.
2. The probability $p$ of success is not too close to 0 or 1.

A common rule of thumb for when to use the normal approximation is when both $np≥5$ and $n(1-p) \geq 5$. This ensures that the distribution is sufficiently symmetric and the approximation will be reasonably accurate.


**Parameters : $$\displaylines{\text{Mean }\mu : \\
\mu = np \\ \\
\text{Standard Deviation }\sigma: \\
\sigma = \sqrt{ np(1-p) }}$$

**Steps :**
1. Check if we meet the conditions for rule of thumb
2. Perform continuity correction on our 'x' value
3. Convert from X-domain to Z-domain
4. Use lookup table to find probability values for 'Z'
5. Subtract the smaller values from the large value if within an interval


**Example :** 
Suppose you flip a fair coin 10 times and count the total number of heads that appear. 

Let $x$ represent the number of heads. $$X \sim B(10, 0.5)$$
Check that the question meets the rule of thumb : $$\displaylines{np \geq 5 \\
10 \times 0.5 = 5 \geq 5 \\ \\
nq \geq 5 \\
nq = 10 \times 0.5 = 5 \geq 5 \\ \\
∴ X^{approx} \sim N(\mu=np = 5, \sigma^2 = npq = 2.5) }$$

Approximate the probability that you observe  :
	(a) at most 7 heads.  $$\displaylines{\text{Change to Z-Domain : } \\
	P(X \leq 7) = P(Z \leq \frac{7-5}{\sqrt{ 2.5 }}) \\ 
	\approx P(Z \leq 1.26) \\
	= 0.8962}$$
	This isn't an accurate answer as we omit data when estimating continuous probability with a discrete distribution. To correct this, we can add 0.5 to out upper range to give us a closer estimate.
	$$\displaylines{\text{Change to Z-Domain : } \\
	P(X \leq 7.5) = P(Z \leq \frac{7.5-5}{\sqrt{ 2.5 }}) \\ 
	\approx P(Z \leq 1.58) \\
	= 0.9453}$$
	(b) less than 7 heads.  $$\displaylines{P(X < 7) =^{cc}P(X < 6.5) = P(Z < \frac{6.5-5}{\sqrt{ 2.5 }}) \\
	\approx P(Z < 0.95) \\
	=0.8289}$$
	(c) between 1 and 3 heads, inclusive. $$\displaylines{P(1 \leq X \leq 3) =^{cc} P(0.5 \leq X \leq 3.5) \\
	P(\frac{0.5-5}{\sqrt{ 2.5 }} \leq Z \leq \frac{3.5-5}{\sqrt{ 2.5 }}) \\
	P(-2.85 \leq Z \le -0.95) \\ \\
	=P(Z \le -0.95) - P(Z \le -2.85) \\
	=0.1711 - 0.0022 = 0.1689}$$


In practice, to get a more accurate solution, 
	If $P(X \le x)$ or $P(X > x)$, add 0.5 to $x$.
	If $P(X \ge x)$ or $P(X < x)$, subtract 0.5 from $x$.



**Example :** 
A premature birth is a birth that takes place more than three weeks before the baby’s estimated due date. In Canada, it is estimated that 8% of all births are premature. Consider a random sample of 500 live births in Canada.  

Let $x$ represent the number of premature births. $$X \sim B(500,0.08)$$
Rule of thumb : $$\displaylines{np = 500 \times 0.8 = 40 \\
nq = 460 \\
\ge 5 \\ \\
∴X \sim N(\mu = np = 40, \sigma^2 = npq = 36.8)}$$

(a) Estimate the probability that at least 45 of these births are premature.  $$\displaylines{P(X \ge 45) =^{cc} P(X \ge 44.5) = P(Z \ge \frac{44.5-40}{\sqrt{ 36.8 }}) \\
\approx P(Z \ge 0.74) = 1-P(Z < 0.74) = 1 - 0.7704 = 0.2296}$$

(b) Estimate the probability that the number of premature births is between 40 and 50, inclusive.$$\displaylines{P(40 \le X \le 50) =^{cc} P(39.5 \le X \le 40.5) \\
\approx P(-0.08 \le Z \le 1.73) = P(Z < 1.73) - P(Z < 0.08) \\
=0.9582 - 0.4681 \\
= 0.4901}$$
