**Content :**
	▪ Simple Random Samples  
	▪ Other Sampling Plans Involving Randomization  
	▪ Biased Sampling Plans  
	▪ Potential Problems After Random Selection

**Experiments :** 
	In an experiment, the researcher actively manipulates one or more variables (called independent variables) and measures the response (dependent variable). The goal is to establish **cause-and-effect** relationships.

**Observational Study :**
	In an observational study, the researcher **does not manipulate** any variables but instead observes and records data as it naturally occurs.



---
#### Simple Random Sample

A **simple random sample**, or **random sample**, is a sample in which the units included in the sample are chosen at random from the population. As a result,  
	▪ Every unit in the population has an equal chance of being included in the sample, and  
	▪ Every sample of the same size has an equal chance of being chosen.

**In order to select a random sample, use the following steps:**  
1. Identify the population of interest.  
2. Obtain the sampling frame; a list of all units in the population.  
3. Assign a number to each unit in the population.  
4. Generate random numbers to identify which units to include in the sample until the desired sample size is reached.


**Example :** 
A class contains 26 students. Seven students from this class will be selected to go on a field trip using a simple random sample.  

Selection will be done according to the following lines of randomly generated digits:  
1559 9068 9290 8303 8508 8954 1051 6677 6415  
0342 5550 6245 7313 0117 7652 5069 6354 7668  

Which seven students get to go on the field trip?




---
#### Other Sampling Plans Involving Randomization

In addition to a simple random sample, we can also consider the following sampling plans that involve randomization:  
	▪ Stratified Random Sampling  
	▪ Cluster Sampling  
	▪ 1-in-k Systematic Sampling


##### Stratified Random Sampling
A **stratified random sample** is a sampling method where a population is divided into **distinct groups (strata)** based on shared characteristics, and then a **random sample** is taken from each stratum.

**Steps :**
- **Divide the population** into **strata** based on a characteristic (e.g., age, income level, education, etc.).
- **Select a random sample** from each stratum.
- **Combine** the samples from all strata to form the final sample.


##### Cluster Sampling
The population is divided into **heterogeneous groups (clusters)**, and **entire clusters** are randomly selected instead of individuals.

**Steps :**
- **Divide** the population into **clusters** (which should represent a mix of the population).
- **Randomly select entire clusters.**
- **Survey everyone** within the selected clusters.


##### 1-in-k Systematic Sampling
Every **k-th individual** is selected from a population list.

**Steps :**
- Arrange the population in **a list**.
- Choose a **starting point** randomly.
- Select every **k-th person** (e.g., every 5th person)




---
#### Biased Sampling Plan

A sampling plan is biased if it systematically favours certain outcomes. A biased sampling method produces a sample that is not representative of the population.

**Two examples of biased samples are :**  
	▪ Voluntary Response Samples  
	▪ Convenience Samples


##### Voluntary Response Samples
A voluntary response sample is a sample consisting of people who choose themselves by responding to a general appeal.

##### Convenience Samples
A convenience sample consists of individuals that are easiest to reach. The sample only represents those who are close and convenient to the sampler.



---
#### Potential Problems After Random Sampling

A common and useful type of observational study is a sample survey; a study of individuals designed to collect information on specific subjects through the use of a questionnaire.


**Non-Response**
Some of the individuals selected for a survey may not be able or willing to participate in the survey. If the respondents differ from the non-respondents in a way that would affect  
the variable(s) of interest, then the survey will suffer from non-response.


**Undercoverage**
Undercoverage occurs when some groups in the population are left out of the process of choosing the sample.


**Wording Bias**
Wording bias occurs when questions are confusing, leading, or sensitive in nature. This results in people providing inaccurate information.




---
#### Sampling Distributions

Content :
	▪ Statistics and Sampling Distributions  
	▪ The Sampling Distribution of the Sample Mean  
	▪ The Central Limit Theorem  
	▪ The Sampling Distribution of the Sample Proportion


**Sampling Variability** 
A parameter is any numerical measure computed using a population of measurements. The value of a parameter is a constant but typically unknown.


**Sampling Distribution**
The sampling distribution of a statistic is the probability distribution of the statistic for a given sample size n.  

There are two methods we can use to obtain the sampling distribution of a statistic:  
1. Use knowledge of the probability distribution of the individual population measurements to derive it.  
2. Use repeated sampling to approximate it.


**Example : Derive From Probability Distibution**
Your professor loves to drink coffee. He always drinks a minimum of one coffee per day, and will drink two coffees on 80% of all days. But he never drinks more than two coffees.  

Choose any two days and consider the average number of coffees consumed by your professor over those two days.  

Assuming the number of coffees he consumes is independent from day to day, find the sampling distribution of the sample mean based on a sample of two days.


Let $X$ represent the number of coffees consumed by Wayne on a random day.

| X   | P(X = x) |
| --- | -------- |
| 1   | 0.2      |
| 2   | 0.8      |

Sampling Distribution of $\overline{X}$ :

| $\overline{X}$ | P($\overline{X}$ = $\overline{x}$) |
| -------------- | ---------------------------------- |
| 1              | 0.04                               |
| 1.5            | 0.32                               |
| 2              | 0.64                               |


##### Repeated Sampling
In order to approximate the sampling distribution of a statistic through repeated sampling, we use the following steps:  
1. Take a random sample of size $n$ from the appropriate probability distribution.  
2. Compute the value of the statistic based on these $n$ observations.  
3. Repeat steps 1. and 2. a fixed number of times, denoted by $m$.


**Example : Repeated Sampling**
In Exercise 1, we were given the probability distribution for the number of coffees consumed  
by your professor on a single day.  

In this exercise, we will consider three different scenarios in which we repeat the process of taking a sample of $n = 2$ days a total of  
	(a) $m = 10$ times 
	(b) $m = 100$ times 
	(c) $m = 1000$ times.  

For each of these scenarios, we will compute m values of the sample mean. We will then compute the relative frequency for each observed value of the sample mean, and construct a histogram of these values.  


a) 10

| $\overline{X}$ | Count | Relative Frequency |
| -------------- | ----- | ------------------ |
| 1              | 1     | 0.1                |
| 1.5            | 4     | 0.4                |
| 2              | 5     | 0.5                |


b) 100

| $\overline{X}$ | Count | Relative Frequency |
| -------------- | ----- | ------------------ |
| 1              | 6     | 0.06               |
| 1.5            | 37    | 0.37               |
| 2              | 57    | 0.57               |


c) 1000

| $\overline{X}$ | Count | Relative Frequency |
| -------------- | ----- | ------------------ |
| 1              | 38    | 0.038              |
| 1.5            | 333   | 0.333              |
| 2              | 629   | 0.639              |


**Example :** 
Refer to Exercise 1.  

(a) Compute the expected value and variance of the number of coffees consumed by your professor on a single day.  $$\displaylines{E(X) = \mu_{X} = \sum xP(X=x) \\= 1(0.2) + 2(0.8) = 1.8 \\ \\
E(X^2) = \sum x^2P(X=x) \\
1^2(0.2) + 2^2(0.8) = 3.4 \\ \\
V(X) = \sigma^2_{x} = E(X^2) - [E(X)]^2 \\= 3.4-1.8^2 \\
=0.16}$$

(b) Compute the expected value and variance of the average number of coffees consumed by your professor over two days.  $$\displaylines{E(\overline{X}) = \mu_{\overline{X}} = \sum\overline{x}P(\overline{X}=\overline{x}) \\= 1(0.04) + 1.5(0.32)+2(0.64) = 1.8 \\ \\
E(X^2) = \sum\overline{x}^2P(\overline{X}=\overline{x}) \\
1^2(0.04) + 1.5^2(0.32) + 2^2(0.64) = 3.32 \\ \\
V(\overline{X}) = \sigma^2_{\overline{x}} = E(\overline{X}^2) - [E(\overline{X})]^2 \\= 3.32-1.8^2 \\
= 0.08}$$

(c) Compare your answers in (a) and (b).
$$\displaylines{a) 0.16 \\
b) 0.08 \\ \\
\text{ The means are the same.}\\
\text{Variances differ by a division of sample size } \\
\sigma^2_{\overline{x}}=\frac{\sigma^2_{x}}{n}}$$




---
#### Central Limit Theorem

When we take **many random samples** from a population and compute the **sample means**, the distribution of those sample means will **approximate a normal distribution**, regardless of the original population’s distribution—**as long as the sample size is sufficiently large (typically n≥30).** $$\overline{X}^{approx} \sim N\left( \mu, \frac{\sigma^2}{n} \right)$$



