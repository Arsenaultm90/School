(Sections 9.1, 9.2)

**Contents :**
	Statistical Hypothesis Testing  
	The Null Hypothesis and Alternative Hypothesis  
	The p-value  
	The Significance Level and Statistical Significance

---
#### **Hypothesis Testing**
A statistical hypothesis test is a procedure that allows a researcher to assess the credibility of a claim about a population parameter based on a random sample from that population.

A hypothesis test consists of two competing hypotheses; the null hypothesis and the alternative hypothesis.


##### **The Null Hypothesis and Alternative Hypothesis**
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



##### $p$-**Value**
The p-value for a hypothesis test is the probability of observing sample data in favour of the alternative hypothesis at least as extreme as that which was actually observed under the assumption that the null hypothesis is true.

The $p$-value represents the plausibility of $H_{0}$ . The smaller the $p$-value, the stronger the evidence against $H_{0}$ and in favour of $H_{a}$.



##### **Significance Level**
The significance level, denoted by $\alpha$, is the smallest $p$-value at which we are willing to reject the null hypothesis.

Standard values of $\alpha$ are 0.01, 0.05, and 0.10.

Rule :
	If $p$-value ≤ $\alpha$, we reject $H_{0}$ and accept $H_{a}$.
	If $p$-value > $\alpha$, we fail to reject $H_{0}$.


##### **Statistical Significance**
When we reject the null hypothesis, we say the result is **statistically significant** at the $\alpha$ level of significance. The smaller the $p$-value, the more statistically significant the result.

**Note 1:** 
	Statistical significance does not imply practical significance, and vice versa.  

**Note 2:** 
	Neither H0 nor Ha can be proven to be true, they can only be shown to be plausible or implausible based on the sample evidence.




---
#### **Hypothesis Testing For A Population Mean**
(Sections 9.3, 10.3)

For some constant value $\mu_{0}$ there are three basic types of hypothesis tests for $\mu$.

Right-Tailed Test : $H_{0} : \mu = \mu_{0} \text{ vs } H_{a} : \mu > \mu_{0}$
Left-Tailed Test : $H_{0} : \mu = \mu_{0} \text{ vs } H_{a} : \mu < \mu_{0}$
Two-Tailed Test : $H_{0} : \mu = \mu_{0} \text{ vs } H_{a} : \mu \ne \mu_{0}$

The way in which we conduct a hypothesis test for a population mean $\mu$ depends on our knowledge of the population standard deviation $\sigma$.


#### **Case 1 : $\sigma$ known**
Step 1 : State $H_0$ and $H_{a}$
Step 2 : Compute the test statistics $z_0 = \frac{\bar{x}- \mu_{0}}{\frac{\sigma}{\sqrt{ n }}}$
Step 3 : Compute the $p$-value $$\displaylines{H_{a} - > \;: P(Z > z_{0}) \\
H_{a} - < \;: P(Z < z_{o}) \\
H_{a} - \ne \; : 2P(Z>  |z_{0}|)}$$
Step 4 : Make a conclusion by comparing the $p$-value to $\alpha$.


**Example :** 
A beer supplier produces bottles advertised to contain 341 mL. A quality control technician  
suspects that, on average, the bottles are being overfilled. In order to test this suspicion, the  
technician takes a simple random sample of 24 bottles of beer and finds the mean volume to be 342.1 mL.  

Assuming that the volume per bottle is normally distributed with a population standard deviation of 2 mL, is there evidence to support the technician’s suspicion? Conduct a hypothesis test at $\alpha$ = 0.01.  

Comment on the validity of the result.

Step 1 : 
	$H_{0} : \mu = 341,\; H_{a} : \mu > 341$
 Step 2 :
	 $Z_{0} = \frac{342.1-341}{\frac{2}{\sqrt{ 24 }}} \approx 2.69$
Step 3 :
	$p$-value $= P(Z \ge 2.69) = P(Z < -2.69) = 0.0036$
Step 4 : 
	$p$-value < $\alpha$ = 0.01
	∴ Reject $H_{0}$, accept $H_{a}$

At $\alpha$ = 0.01, the average volume of all bottles exceed 341mL.


**Example :** 
The manager of a customer service call centre wants to decrease the average call time of customers from the current average of 38 minutes. To do so, the automated phone menu is redesigned for easier navigation.  

After redesigning the menu, a random sample of 30 calls yields an average call time of 35 minutes. The population standard deviation is known to be 8 minutes. Was the redesign successful in reducing the average call time of customers? Test at $\alpha$ = 0.05. 

Comment on the validity of the result.

Step 1 :
	$H_{0} : \mu = 38,\; H_{a} : \mu < 38$
Step 2 : 
	$Z_{0} = \frac{38-35}{\frac{8}{\sqrt{ 30 }}} \approx -2.05$
Step 3 : 
	$p$-value = $P(Z \le -2.05) = 0.0202$
Step 4 :
	$p$-value < $\alpha$ = 0.05
	∴ Reject $H_{0}$, Accept $H_{a}$

At $\alpha$ = 0.05, the average call time has been reduced.



#### **Case 2 : $\sigma$ unkown**
Step 1 :
	State $H_{0}$ and $H_{a}$
Step 2 :
	Compute the test statistic $t_{0} = \frac{\bar{X} - \mu_{0}}{\frac{s}{\sqrt{ n }}}$
Step 3 :
	Compute the $p$-value $$\displaylines{H_{a} - > \;:\; P(T_{n-1} > t_{0}) \\
	H_{a} - < \;:\; P(T_{n-1} < t_{0}) \\
	H_{a} - \ne \;: \; 2P(T_{n-1} > |t_{0}|)}$$
Step 4 :
	Make a conclusion by comparing the $p$-value to $\alpha$.


**Example :**
A new process for producing synthetic diamonds can be operated at a profitable level only if the average weight of the diamonds is greater than 0.5 carats. To evaluate the profitability of the  
process, six diamonds were generated. 

The weights, in carats, were recorded as follows:  0.48, 0.63, 0.54, 0.50, 0.59, 0.56  

At a 10% significance level, do the six measurements present sufficient evidence to indicate that the average weight of the diamonds produced by the process is in excess of 0.5 carats? 

You may assume that the weights of all such diamonds are normally distributed.$$\displaylines{\bar{X} = \frac{\sum x}{n} = \frac{3.3}{6} = 0.55 \\
s^2 = \frac{\left( \sum x^2  - \frac{\left( \sum x \right)^2}{n}\right)}{n-1} = \frac{\left( 1.8306 - \frac{3.3^2}{6} \right)}{6-1} = 0.00312}$$

Step 1 :
	$H_{0} : \mu = 0.5, \; H_{a} : \mu > 0.5$
Step 2 :
	$t_{0} = \frac{0.55 - 0.5}{\frac{\sqrt{  0.00312}}{\sqrt{ 6 }}} \approx 2.193$
Step 3 :
	$p$-value $= P(T_{n-1} > t_{0}) = P(T_{5} > 2.193)$
	∴ 0.025 < $p$-value < 0.05
Step 4 :
	$p$-value < $\alpha = 0.10$
	Reject $H_{0}$, Accept $H_a$

At $\alpha$ = 0.10, the average weight of the diamonds exceeds 0.5 carats.



**Example :** 
The daily yield for a chemical plant has averaged 880 tonnes for the last several years. The quality control manager would like to know whether this average has changed during the past 6 months.  

A random sample of 24 recorded days produces a mean of 871 tonnes and a standard deviation of 18 tonnes.  

Is there evidence that the average daily yield has changed over the past 6 months? 
Conduct an appropriate test at the 1% level of significance.
Under what conditions is this result valid? $$\displaylines{\bar{X} = 871 \\ s = 18}$$
Step 1 : 
	$H_{0} : \mu=880, H_{a} : \mu < 880$
Step 2 :





---
#### **A Hypothesis Test for a Population Proportion**

