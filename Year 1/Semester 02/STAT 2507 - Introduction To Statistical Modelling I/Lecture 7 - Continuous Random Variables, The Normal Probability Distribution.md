Contents :
	▪ Continuous Random Variables  
	▪ Probability Density Functions  
	▪ The Uniform Probability Distribution  
	▪ The Exponential Probability Distribution



---
#### Continuous Random Variable

A **continuous random variable** is a random variable that can assume any value within a continuous interval of values. Continuous random variables are used when the event of interest is measured on a continuous scale.



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
\sigma^2_{x} = \frac{(U-L)^2}{12}}$$
