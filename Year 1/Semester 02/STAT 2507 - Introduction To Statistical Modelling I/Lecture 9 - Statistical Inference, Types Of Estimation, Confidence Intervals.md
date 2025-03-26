**Outline :**
	Statistical Inferences and Types of Estimation
	Confidence Intervals for a Population Mean


---
#### Statistical Inference and Types of Estimation  
(Sections 8.1 – 8.3)

##### Statistical Inference
Statistical inference is concerned with making decisions or predictions about population parameters.


---
##### Types Of Estimations
An **estimator** is a rule, usually expressed as a formula, that tells us how to calculate an estimate based on information in a sample.

**Point Estimation**
Point estimation is a method in statistical inference where we estimate an unknown population parameter using a single value (point estimate) derived from sample data. The goal is to provide the best possible approximation of the true parameter.

 Common Point Estimators
1. **Mean ( $\bar{X}$ )** – Estimates the population mean $\mu$.
2. **Proportion ( $\hat{P}$)** – Estimates the population proportion $p$.
3. **Variance ( $s^2$ )** – Estimates the population variance $\sigma^2$.
4. **Standard Deviation ( $s$ )** – Estimates the population standard deviation $\sigma$.

Desirable Properties of Point Estimators
1. **Unbiasedness** – The expected value of the estimator equals the true parameter value.
2. **Consistency** – As sample size increases, the estimator converges to the true parameter.
3. **Efficiency** – The estimator has the smallest variance among all unbiased estimators.
4. **Sufficiency** – The estimator captures all relevant information from the sample.

Example: 
	Suppose we wish to estimate the average starting salary of all Carleton University graduates from last year.  
	The sample mean $\bar{X}$ is a point estimator of $\mu$.  
	One random sample yields an observed sample mean of = $52,214. The value $52,214 is a point estimate of $\mu$.

The distance between an estimate and the estimated parameter is called **error of estimation**.


**Interval Estimation** 
An **interval estimator** is a method used in statistical inference to estimate a population parameter by providing a range of values, called a **confidence interval**, within which the true parameter is likely to fall. This range is determined from the sample data and has a certain level of confidence associated with it.

Key Components of Interval Estimators
- **Point Estimate**: A single value estimate (like the sample mean) from the data.
- **Margin of Error**: The range above and below the point estimate, which reflects the variability or uncertainty of the estimate.
- **Confidence Level**: The probability that the interval contains the true population parameter. Common confidence levels are 90%, 95%, and 99%.

Confidence Interval Formula (For A Mean) : 
For a population mean μ, when the sample size is large enough, the confidence interval is often calculated as:$$\displaylines{\mu \approx \bar{x} \pm z \times \frac{s}{\sqrt{ n }} }$$
Where:
- $\bar{x}$ = sample mean
- $z$ = z-value corresponding to the desired confidence level (e.g., 1.96 for 95% confidence)
- $s$ = sample standard deviation
- $n$ = sample size


**Types Of Interval Estimators**
1. **Confidence Interval for a Mean** (when population standard deviation is unknown)
- Typically uses the **t-distribution** if the sample size is small, and **z-distribution** if the sample size is large.

2. **Confidence Interval for a Proportion**
- For a population proportion $p$, the confidence interval is calculated as: $$p \approx \hat{p} \pm z \times \sqrt{ \frac{{\hat{p}(1-\hat{p})}}{n} }$$
3. **Confidence Interval for a Variance** (using the **Chi-Square** distribution).




---
#### Confidence Intervals For A Population Mean Pt. 1
(Sections 8.3, 8.4, 8.8)

**Outline :**
	Confidence Intervals  
	A Confidence Interval for a Population Mean ( known)  
	Sample Size Determination for a Desired Margin of Error


---
##### Confidence Interval

A **confidence interval** for a population parameter is an interval computed from a sample that, in repeated sampling, contains the value of the parameter a specified percentage of the time.

The long-run percentage of the time a confidence interval will contain the value of the population parameter is known as the **confidence level**.

Formula for a 95% confidence interval for a population mean : $$\mu \pm 1.96 \frac{\sigma}{\sqrt{ n }}$$

Example : 
An aluminum can filling machine is set to fill each can with 355 mL of cola. In order to ensure the machine is operating correctly, a quality control technician took a random sample of $n = 12$ cans and measured the amount of cola in each can.

The sample yielded a mean volume of 354.6 mL.  

(a) If the amount of cola per can is normally distributed with a standard deviation of = 0.4 mL, compute a 95% confidence interval for the population mean volume per can. Interpret the result.  $$\displaylines{n = 12 \\ \bar{X} = 354.6 \\ \sigma = 0.4 \\
= 354.6 \pm 1.96 \frac{0.4}{\sqrt{ 12 }}\\
=354.6 \pm 0.23}$$
We are 95% confident that the average volume per can falls between the interval [354.37mL - 354.83mL]

(b) Comment on the validity of the result in part (a).
This result is valid because :
	We took a random sample
	The volume per can is normally distributed


---
##### The Confidence Level 
We first select a confidence level of $(1 - \alpha)100\%$, where 0 < $\alpha$ < 1.

![[Screenshot 2025-03-26 at 12.31.23 PM.png|300]]

$Z_{\frac{\alpha}{2}}$ is the value of the z-distribution such that $P\left( Z > Z_{\frac{\alpha}{2}} \right) = \frac{\alpha}{2}$
The most common confidence levels are 90%, 95%, and 99%.

| Confidence<br>Level | $\alpha$ | $z_{\frac{\alpha}{2}}$ |
| ------------------- | -------- | ---------------------- |
| 90%                 | 0.10     | 1.645                  |
| 95%                 | 0.05     | 1.96                   |
| 99%                 | 0.01     | 2.576                  |

**Case 1 : $\sigma$ known**
If we take a simple random sample from a normally distributed population with standard deviation $\sigma$, then a $(1-\alpha)100\%$ confidence interval for $\mu$  is given by : $$\mu \approx \bar{X} \pm Z_{\frac{\alpha}{2}} \frac{\sigma}{\sqrt{ n }}$$where : $$\displaylines{\bar{X} - \text{Point Estimate} \\
Z_{\frac{\alpha}{2}} \frac{\sigma}{\sqrt{ n }} - \text{Margin of Error (E)}}$$
If the population is not normally distributed but the sample size is at least 30, this interval is still approximately valid as a result of the Central Limit Theorem.


Example : 
A random sample of 36 recently sold homes was taken from Ottawa. The average selling price of these homes was $431,520. Historically, the population standard deviation is known to be  
approximately $62,700.  

Compute and interpret a 99% confidence interval for the current population mean selling price of homes in Ottawa.  

Comment on the validity of the result. $$\displaylines{n = 36 \\
\bar{X} = 431,520 \\
\sigma = 62,700 \\
Z = 99\% \\ \\
\text{Confidence Interval} \\
= 431,520 \pm 2.576 \frac{62,700}{\sqrt{ 36 }} \\
= 431,520 \pm 26919}$$
We are 99% confident that the average selling price of homes falls between the interval of [404,601 - 458,439].

This result is approximately valid because :
	We have a random sample of homes
	The sample size is greater than 30, therefore the result is approximately valid due to the CLT.



---
##### The Margin Of Error
Sample size required to find a confidence interval is : $$n = \left( \frac{Z_{\frac{a}{2}}\sigma}{E} \right)^2$$
Example :
A researcher wishes to estimate the average IQ score for students at Carleton University  
to within 2 points with 99% confidence.  

Based on past results, the standard deviation of IQ scores is known to be approximately 15  
points.  

What is the minimum required sample size? $$n = (\frac{2.576 \times 15}{2})^2 \approx 374$$

---
#### Confidence Intervals For A Population Mean Pt. 2
(Sections 10.1 – 10.3)

Outline :
	The Student’s t-Distribution  
	A Confidence Interval for a Population Mean ( unknown)


---
**Case 2 : $\sigma$ Unknown**
In most real-world applications, the population standard deviation is unknown, and we need to estimate it with the sample standard deviation $s$.

**Student's $t$ Distribution**
Like the standard normal distribution, the t distribution is bell shaped and symmetric about 0.
If is $\sigma$ unknown, then we estimate it with $s$ : $$T = \frac{\bar{X}-\mu}{\frac{s}{\sqrt{ n }}}$$
We say that T follows a $t$ distribution with $n – 1$ degrees of freedom, or $df = n – 1$.
As $df \rightarrow \infty$, the $t$ distribution converges to the z distribution.


**Example :** 
	Find the value of $t$ distribution with 17 degrees of freedom that has a right-tailed area under the curve of 0.01. $$t_{a,\; n-1} = t_{0.01,\; 17} = 2.567$$

If we take a simple random sample from a normally distributed population, then a $(1-\alpha)100\%$ confidence interval for $\mu$ is given by : $$\bar{X} \pm t_{\frac{\alpha}{2},n-1} \frac{s}{\sqrt{ n }}$$
where $t_{\frac{\alpha}{2}, n-1}$ is the value of the $t$-distribution with $n-1$ degrees of freedom that has a right-tailed area of $\frac{\alpha}{2}$.


**Example :** 
	Wayne is interested in the average amount of time he spends on each walk with Molly.  
	A sample of 8 walks produced an average of 41.4 minutes with a standard deviation of  
	1.3 minutes.  $$\displaylines{n = 8 \\
\bar{X} = 41.4 \\
s = 1.3 \\
t_{0.005,\; 7} = 3.499}$$
(a) Compute and interpret a 99% confidence interval for the mean time of all walks with Molly.
$$\bar{X} \pm t_{\frac{a}{2},\; n-1} \frac{s}{\sqrt{ n }} = 41.4 \pm 3.499 \frac{1.3}{\sqrt{ 8 }} = \boxed{41.4 \pm 1.6} $$
We are 99% confident the mean time of all walks with Molly is between the interval of [39.8 - 43.0] minutes

(b) Under what conditions is this result valid?
For this result to be valid :
	Our sample must be a random sample
	Walk times are normally distributed


**Example :** 
A researcher wishes to estimate the average number of hours that high school students  
spend using social media apps each week.  

For a single week, a random sample of 50 high school students yielded a mean of 16.2  
hours and a standard deviation of 5.1 hours.  

Compute and interpret a 90% confidence interval for the average number of hours high school students spend using social media apps each week.
$$\displaylines{n = 50 \\ s = 5.1 \\ \bar{X} = 16.2 \\ t_{0.05,\; 49} = 1.645 \\ \\
= 16.2 \pm 1.645 \frac{5.1}{\sqrt{ 50 }} \\
= 16.2 \pm 1.2 }$$
We are 90% confident that the average time students spend on social media apps each week is between the interval of [15.0 - 17.4] hours.

For this to be valid :
	Our sample must be a random sample
	Time is approximately normally distributed due to the sample size $n = 50$ according to the CLT.



---
#### Summary
The goal of a confidence interval is to estimate the **range** in which the true **population mean (μ)** is likely to be, based on a sample. Since we typically can't measure an entire population, we use **sample data** to make an **inference** about the population.

**Steps :**
1. **We take a sample** from the population and calculate its mean (xˉ\bar{x}xˉ).
    
2. **We account for variability** by considering the standard deviation (either known or estimated from the sample).
    
3. **We choose a confidence level** (e.g., 95%) that represents how confident we are that the interval contains the true mean.
    
4. **We calculate the confidence interval** using either the **Z-distribution** (if σ is known) or the **T-distribution** (if σ is unknown).
    
5. **Interpretation:** If we repeated this process many times, 95% of the calculated intervals would contain the true population mean.

**Key Takeaways:**
- **The wider the confidence interval, the more uncertainty** there is in the estimate.
- **Larger samples lead to narrower confidence intervals** because they reduce variability.
- **Higher confidence levels (e.g., 99%) create wider intervals** since they require more certainty.


 **1. Confidence Interval Formula (Standard Deviation Known)**
If the population standard deviation (σ) is **known**, use the **Z-distribution**: $$\mu \approx \bar{X} \pm Z \times \frac{\sigma}{\sqrt{ n }}$$
Where :
$\bar{X} = \text{Sample Mean}$
$\sigma = \text{Population Standard Deviation}$
$n = \text{Sample Size}$
$Z = \text{z-score corresponding to the confidence level}$

| Confidence<br>Level | $\alpha$ | $z_{\frac{\alpha}{2}}$ |
| ------------------- | -------- | ---------------------- |
| 90%                 | 0.10     | 1.645                  |
| 95%                 | 0.05     | 1.96                   |
| 99%                 | 0.01     | 2.576                  |


**2. Confidence Interval Formula (Standard Deviation Unknown)**
If the population standard deviation (σ) is **unknown**, use the **T-distribution**: $$\mu \approx \bar{X} \pm t_{\frac{\alpha}{2},\; n-1} \times \frac{s}{\sqrt{ n }}$$
Where :
- $s$ = sample standard deviation (used instead of σ)
- $t$ = t-score from the **t-distribution table** with **n−1 degrees of freedom**
- $\alpha$ = 1 - Confidence Level

The **T-distribution** is used instead of the normal (Z) distribution when the sample size is small 
($n<30$) because it accounts for the additional uncertainty in estimating σ from the sample.


