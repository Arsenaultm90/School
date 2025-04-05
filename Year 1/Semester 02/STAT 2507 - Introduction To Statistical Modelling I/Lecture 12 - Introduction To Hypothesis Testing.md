(Sections 9.1, 9.2)

**Contents :**
	Statistical Hypothesis Testing  
	The Null Hypothesis and Alternative Hypothesis  
	The p-value  
	The Significance Level and Statistical Significance


---
#### Hypothesis Testing

A statistical hypothesis test is a procedure that allows a researcher to assess the credibility of a claim about a population parameter based on a random sample from that population.

A hypothesis test consists of two competing hypotheses; the null hypothesis and the alternative hypothesis.


---
#### The Null Hypothesis and Alternative Hypothesis

The **null hypothesis**, denoted by $H_0$ , is the claim we assume is true until we find sufficient evidence to the contrary.

The **alternative hypothesis**, denoted by $H_{a}$, contradicts the statement made by the null hypothesis.

The hypothesis test is designed to assess the strength of the evidence against the null hypothesis and in favour of the alternative hypothesis.



**Example :** 
A beer supplier produces bottles advertised to contain 341 mL. A quality control technician  
suspects that, on average, the bottles are being overfilled. In order to test this suspicion, the  
technician takes a random sample of 24 bottles of beer and finds the mean volume to be 342.1 mL.  

Assuming that the volume per bottle is normally distributed with a population standard deviation of 2 mL, is there strong evidence to support the technician’s suspicion?  

In other words, if the true mean volume is 341 mL, how likely are we to observe a sample mean volume as large, or larger, than 342.1 mL?
$$\displaylines{X \sim N(\mu = 341, \sigma = 2) \rightarrow \bar{X} \sim N\left( \mu_{\bar{X}} = 341, \sigma_{\bar{X}} = \frac{2}{\sqrt{ 24 }} \right) \\
P(\bar{X} \ge 342.1)  = P\left( Z \ge \frac{342.1-341}{\frac{2}{\sqrt{ 24 }}} \right) \approx P(Z \ge 2.69) = 1 - P(Z < 2.69) \\ \\
p-value = 0.00357}$$

We can conclude only one of two things from this result : 
1. We observed a very unlikely sample
2. The true mean volume is greater than 341mL



---
#### $p$-Value

The p-value for a hypothesis test is the probability of observing sample data in favour of the alternative hypothesis at least as extreme as that which was actually observed under the assumption that the null hypothesis is true.

The $p$-value represents the plausibility of $H_{0}$ . The smaller the $p$-value, the stronger the evidence against $H_{0}$ and in favour of $H_{a}$.



---
#### Significance Level

The significance level, denoted by $\alpha$, is the smallest $p$-value at which we are willing to reject the null hypothesis.

Standard values of $\alpha$ are 0.01, 0.05, and 0.10.

Rule :
	If $p$-value ≤ $\alpha$, we reject $H_{0}$ and accept $H_{a}$.
	If $p$-value > $\alpha$, we fail to reject $H_{0}$.



---
#### Statistical Significance

When we reject the null hypothesis, we say the result is **statistically significant** at the $\alpha$ level of significance. The smaller the $p$-value, the more statistically significant the result.

**Note 1:** 
	Statistical significance does not imply practical significance, and vice versa.  

**Note 2:** 
	Neither H0 nor Ha can be proven to be true, they can only be shown to be plausible or implausible based on the sample evidence.
