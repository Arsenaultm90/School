(Sections 9.1, 9.2)

**Contents :**
	Statistical Hypothesis Testing  
	The Null Hypothesis and Alternative Hypothesis  
	The p-value  
	The Significance Level and Statistical Significance

**Z-score**
- The **Z-value** is a standardized score that tells you **how many standard deviations** your sample mean is from the population mean
- **Magnitude** = How far the value is from the mean
- **Sign** = Which direction from the mean

**P-value**
- The **p-value** is the **probability** of getting a test statistic **as extreme or more extreme** than the observed one **assuming the null hypothesis is true**.



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
	Neither $H_{0}$ nor $H_{a}$ can be proven to be true, they can only be shown to be plausible or implausible based on the sample evidence.




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
	 Finding how many standard deviations our sample mean is from our population mean.
Step 3 :
	$p$-value $= P(Z \ge 2.69) = P(Z < -2.69) = 0.0036$
	Finding the probability that we would get this sample mean.
Step 4 : 
	$p$-value < $\alpha$ = 0.01
	Since our $p$-value(probability of getting the sample mean) is smaller than our chosen threshold, it is more likely that the population mean is higher than reported.
	∴ Reject $H_{0}$, accept $H_{a}$ where, the true population mean is much more likely to be higher than initially stated.

At $\alpha$ = 0.01, the average volume of all bottles exceed 341mL.


**Example :** 
The manager of a customer service call centre wants to decrease the average call time of customers from the current average of 38 minutes. To do so, the automated phone menu is redesigned for easier navigation.  

After redesigning the menu, a random sample of 30 calls yields an average call time of 35 minutes. The population standard deviation is known to be 8 minutes. Was the redesign successful in reducing the average call time of customers? Test at $\alpha$ = 0.05. 

Comment on the validity of the result.

Step 1 :
	$H_{0} : \mu = 38,\; H_{a} : \mu < 38$
Step 2 : 
	$Z_{0} = \frac{35-38}{\frac{8}{\sqrt{ 30 }}} \approx -2.05$
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
	$H_{0} : \mu=880, H_{a} : \mu \ne 880$
Step 2 :
	$t_{0} = \frac{871 - 880}{\frac{18}{\sqrt{ 24 }}} = -2.45$
Step 3 :
	$p$-value = 2$P(T_{23} > -2.45)$
	0.02 < $p$-value < 0.05
Step 4 :
	Since $p$-value > 0.01, we fail to reject $H_{0}$




---
#### **A Hypothesis Test for a Population Proportion**
(Section 9.5)


For some constant value $p_{0}$, there are three basic types of hypothesis tests for $p$ : $$\displaylines{\text{Right-Tailed Test - } H_{0} : p = p_{0} \text{ vs } H_{a} : p > p_{0} \\
\text{Left-Tailed Test - } H_{0} : p = p_{0} \text{ vs } H_{a} : p < p_{0} \\
\text{Two-Tailed Test - } H_{0} : p = p_{0} \text{ vs } H_{a} : p \ne p_{0}}$$
Test Statistic : $$Z_{0} = \frac{\hat{p} - p_{0}}{\sqrt{ \left( \frac{p_{0}q_{0}}{n} \right) }}$$

NOTE :
	If $np_0 \ge 5 \text{ and } nq_{0} \ge 5$, then this test statistic will follow an approximately standard normal distribution



Example : 
It has been estimated that 65% of all Canadians consume at least one coffee-based drink per day.  A researcher at one university suspects that this percentage is lower for students at their university.  

In a random sample of 120 students, 71 indicated that they consume at least one-coffee based drink per day. 

Does the sample data support the researcher’s suspicion at the 0.05 significance level? 
Comment on the validity of the result.
$$\displaylines{n = 120 \\
\hat{ p } = \frac{71}{120} = 0.5917\\
p_{0} = 0.65  \\
q_{0} = 0.35}$$
Step 1 :
	$H_0 : p=0.65, \; H_{a} : p < 0.65$
Step 2 :
	$Z_{0} = \frac{0.5917 - 0.65}{\sqrt{ \frac{0.65 \times 0.35}{120} }} \approx -1.30$
Step 3 :
	$p$-value = $P(Z < -1.30) = 0.0968$
Step 4 :
	$p$-value > $\alpha$ = 0.05
	Fail to reject $H_0$

At $\alpha$ = 0.05, there is insufficient evidence to conclude the percentage of coffee drinkers at this university is less than 65%.

This results is approximately valid because :
1. We took a random sample
2.  $np_{0} \text{ and } nq_{0} \ge 5$ and therefore approximately follows a normal distribution.




---
#### **The Critical Value Method**
(Sections 9.2, 9.3, 9.5, 10.3)

When conducting hypothesis tests, such as testing whether a sample mean is significantly different from a population mean, the critical value method helps determine whether to reject the null hypothesis. The critical value is compared with the test statistic (like Z-score or T-score) to make this decision.

Does my test statistic fall in the **critical region** — a region so extreme that it would be unlikely to occur if the null hypothesis were true?

##### **One-Tailed Z-Test**
Step 1 :
	State $H_0$ and $H_{a}$
Step 2 :
	Compute the test statistic $Z_{0}$
Step 3 :
	Find the critical value $Z_a$
Step 4 :
	Make decision by comparing $Z_{0}$ to $Z_{a}$ $$\displaylines{H_{a} :\; >,\; Z_{0} \ge Z_{a} \\
	H_{a} :\; <, \; Z_{0} \le Z_{a}}$$


**Example :** 
It has been estimated that 65% of all Canadians consume at least one coffee-based drink per day. A researcher at one university suspects that this percentage is lower for students at their university.  

In a random sample of 120 students, 71 indicated that they consume at least one-coffee based drink per day. Does the sample data support the researcher’s suspicion at the 0.05 significance  
level? 

Test using the critical value method.

Step 1 :
	$H_{0} : p = 0.65,\; H_{a} : p < 0.65$
Step 2 :
	$Z_{0}$ = -1.30
Step 3 :
	$Z_{a} = Z_{0.05}$ = -1.645
	This value is from the t-table at 0.05 with $\infty$ degrees of freedom.
Step 4 :
	![[Drawing 2025-04-06 10.44.12.excalidraw.png|500]]

If we follow the chart, we can compare directly with the $Z_{0.05}$ but then must use the absolute value of $Z_{0}$ as we are then comparing it as a right-tailed test.

∴ Since $Z_a$ = -1.645 < $Z_{0}$ = -1.3, we fail to reject $H_{0}$


**Example :** 
A new process for producing synthetic diamonds can be operated at a profitable level only if the average weight of the diamonds is greater than 0.5 carats. To evaluate the profitability of the  
process, six diamonds were generated. 

The weights, in carats, were recorded as follows: 0.48, 0.63, 0.54, 0.50, 0.59, 0.56  

At a 10% significance level, do the six measurements present sufficient evidence to indicate that the average weight of the diamonds produced by the process is in excess of 0.5 carats? 

Test using the critical value method.

Step 1 : 
	$H_0$  : $p$ = 0.5, $H_{a}$ : $p$ > 0.5
Step 2 : 
	$t_{0}$ = 2.193, $df$ = 5
Step 3 :
	Critical Value : $t_{\alpha, n-1}$ = $t_{0.10, 5}$ = 1.476
Step 4 : 
	Since $|t_{0}| = |2.193| > 1.476$, we reject $H_{0}$, accept $H_{a}$ 





##### **Two-Tailed Test**
Step 1 :
	State $H_{0}$ and $H_{a}$
Step 2 :
	Compute the test statistic for $Z_0$
Step 3 :
	Find the critical value $Z_{\frac{\alpha}{2}}$
Step 4 :
	Make a decision comparing $Z_{0}$ to $Z_{\frac{\alpha}{2}}$ $$H_{a} :\; \ne,\; |Z_{0}| \ge Z_{\frac{\alpha}{2}} $$


**Example :** 
The daily yield for a chemical plant has averaged 880 tonnes for the last several years. The quality control manager would like to know whether this average has changed during the past 6 months.  

A random sample of 24 recorded days produces a mean of 871 tonnes and a standard deviation of 18 tonnes.  

Is there evidence that the average daily yield has changed over the past 6 months? Conduct an appropriate test at the 1% level of significance. 

Under what conditions is this result valid? $$\displaylines{\mu = 880 \\
n = 24 \\
\bar{X} = 871 \\
\sigma = 18 \\
\alpha =0.01}$$
Step 1 : 
	$H_{0}$ : $\mu = 880$, $H_{a} \ne 880$
Step 2 :
	$t_{0} \approx -2.449$, $df = n-1 = 23$
Step 3 :
	Critical Value : $t_{\frac{\alpha}{2}, df} = t_{0.005,23} = 2.807$
Step 4 :
	 Since $|t_{0}| = 2.449 < 2.807$, we fail to reject $H_0$.

