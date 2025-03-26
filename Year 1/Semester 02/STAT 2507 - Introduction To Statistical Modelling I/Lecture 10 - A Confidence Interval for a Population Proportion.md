(Section 8.4)

**Outline :**
	A Confidence Interval for a Population Proportion  
	Sample Size Determination for a Desired Margin of Error


---
#### A Confidence Interval for a Population Proportion

The confidence interval for $p$ is given by : $$\hat{p} \pm Z_{\frac{\alpha}{2}}\sqrt{ \frac{\hat{p}\hat{q}}{n} }$$
This approximation is reasonable as long as $n \hat{p} \ge 5 \text{ and } n \hat{q} \ge 5$.
In other words, this approximation is reasonable as long as our sample contains at least 5 “successes” and 5 “failures”.

**Example :** 
In a random sample of 75 people, 24 of them said they have a pet dog.  
Estimate the proportion of all people who have a pet dog with 95% confidence.
$$\displaylines{n = 75 \\
\hat{p} = \frac{24}{75} = 0.32 \\
\hat{ q} = \frac{51}{75} = 0.68 \\
\alpha = 0.05 \\ \\
=0.32 \pm 1.96 \times \sqrt{ \frac{0.32 \times 0.68}{75} } \\
= 0.32 \pm 0.11}$$
∴ We are 95% confident that the proportion of all people with a pet dog is in the interval of [0.21 - 0.43].

The results are reasonable because $n \hat{p} \ge 5 \text{ and } n \hat{q} \ge 5$.



---
#### Sample Size for a Desired Margin of Error

In the confidence interval for a population proportion, the margin of error is : $$E = Z_{\frac{\alpha}{2}} \sqrt{ \frac{pq}{n} }$$
We can select a sample size n that will yield a desire margin of error.  
Solving for $n$ in the above equation, we obtain : $$n = \left( \frac{Z_{\frac{\alpha}{2}}}{E} \right)^2pq$$
We can make an educated guess at the value of p. This educated guess, denoted by p*, is typically based on previous information.  
The formula for computing sample size is now : $$n = \left( \frac{Z_{\frac{\alpha}{2}}}{E} \right)^2p^*q^*$$
If we have no previous information on which to base p*, we set p* = 0.5.  This value of p* will give us the maximum possible sample size we would require to to guarantee the desired margin of error.


**Example :** 
Suppose we wish to estimate the percentage of people who plan to vote for a certain  
political party. We want our estimate to be accurate to within 3 percentage points with  
95% confidence. 

How many people should we include in our sample if  
	(a) We have no previous information.  
		Set $p^*$ = 0.5$$n = \left( \frac{1.96}{0.03} \right)^2 (0.5 \times 0.5) \approx 1068$$
	(b) No more than 35% of people have voted for this party in any election. $$n = \left( \frac{1.96}{0.03} \right)^2(0.35 \times 0.65) \approx 972$$

