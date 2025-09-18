# Why Probability?  
## To Measure Uncertainty
We could predict the number on a dice roll if we knew of **every** factor that affects the outcome: the initial grip, angle it was thrown at, air condition, etc.
However, in practice, we have **limited information**. So everything is a guess, therefore probability is needed.
**Probability Theory** helps us use math to understand and measure how uncertain or likely different events are to happen. It’s like a tool that helps us figure out the chances of something happening, even if we’re not completely sure about the outcome.
## Why Probability in Machine Learning?
Core idea: Probability is essential for handling **uncertainty** and **imperfection** in machine learning.
Probabilistic Modeling:
- Goal is to **explicitly** learn a probability distribution.
- The model aims to learn either **Joint Probability Density P(x, y)** or **Conditional Probability Density P(y| x)**
	- Joint Probability Density: 
		- The probability of seeing a specific data point (x) and its label (y) together. 
		- It describes the likelihood multiple random variables occurring together. 
		- For continuous variables, it's modeled as a **joint probability density function (PDF)**, which allows you to capture relationships between variables.
		- By learning the joint distribution from real data, you can **sample new data points** that respect the statistical relationships between features (e.g., height and weight), preserving correlations and dependencies.
	- Conditional Probability Density:
		- The probability of a label (y) given an input data point (x).
		- The conditional PDF is $( f_{X|Y}(x|y) = \frac{f_{X,Y}(x,y)}{f_Y(y)} )$, where $( f_{X,Y}(x,y) )$ is the **joint PDF**, and $( f_Y(y) )$ is the **marginal PDF** of the **conditioning** variable.
Modeling Errors:
- Even for non-probabilistic/deterministic modeling we need to account for random error (𝜀).
	- Deterministic models assume a fixed outcome for given inputs, but real-world systems often have **unknown variables or errors** (e.g., measurement mistakes, environmental changes) that introduce uncertainty.
	- Accounting for probability helps capture this **uncertainty**, allowing the model to better reflect unpredictable factors or variations in the system.
- The fundamental equation: $y = f_w(x) + \varepsilon$ (Standard Regression Equation).
	- $y$: True value to predict.
	- $f_w(x)$: Model's prediction based on input $x$ and parameters $w$.
	- $\varepsilon$ (epsilon): The random error term.
		- Represents uncertainty, and captures all other factors affecting $y$ that are not included in the model.
- Causes for random error (𝜀):
	- Incomplete Features: Input data ($x$) lacks all necessary information to perfectly predict $y$.
	- Imperfect Models: The model's architecture ($f_w$) is too simple to capture the true, complex relationship. (Limited hypothesis space).
	- Noisy Data: Errors in measuring or recording the input features ($x$) or the target labels ($y$).
# Two Interpretation of Probability: Frequentist vs Bayesian 
## Simple Breakdown
Frequentist: Probability = long-run **frequency**. (Objective)
Bayesian: Probability = Degree of **belief**/**uncertainty**. (Subjective)
## Difference in Approach
Imagine we want to know if a coin is fair.
### Frequentist Approach
Goal: Analyze the data in front of you. Determine if what you see is likely or unlikely **assuming a specific truth** (e.g., The coin is fair).
Probability is: The relative frequency of an event happening if you could repeat an experiment an infinite number of times.
- e.g., "The probability of heads is 50%" means if I flip the coin forever, half the flips will be heads.
Parameters (e.g., the coin's fairness): Are **fixed**, unknown numbers. They are **not** random. There is **one** true value.
The Process:
- **Assume** a null hypothesis (e.g., "The coin is fair").
	- A null hypothesis is the assumption that there is no significant effect or relationship between variables, and any observed differences are due to random chance.
- Collect data (e.g., flip the coin 100 times, get 60 heads).
- Ask: "Given my hypothesis is true, how likely is it to see this data?" (e.g., "If the coin is fair, how likely am I to get 60+ heads?")
	- Frequentist Probability is given by: $P(A) = \frac{f_A}{n}$
	- Where: 
		- $P(A)$ is the probability of event $A$ occurring
		- $f_A$ is the number of times event $A$ occurred (the frequency of $A$)
		- $n$ is the total number of trials or observations.
	- In English: $P(A) = \frac{\text{Number of times event } A \text{ occurs}}{\text{Total number of trials}}$
- If the result is very unlikely (e.g., p-value < 0.05), you **reject** your initial hypothesis.
Key Idea: It's about the probability of the **data**, given a fixed model.
### Bayesian Approach
Goal: Update your beliefs about the world based on new evidence.
Probability is: A measure of your belief or certainty about an event. It's personal and can be updated.
- e.g., "I am 90% sure this coin is biased" based on what I've seen.
Parameters (e.g., the coin's fairness): Are unknown and are treated as **random variables** themselves. They have a probability distribution (called a prior).
The Process:
- Start with a "Prior", which is your initial belief about the parameter (e.g., "I think most coins are fair").
- Collect data (e.g., flip the coin 100 times, get 60 heads).
- Update your belief using Bayes' Theorem. Combine your prior belief with the new data to form a "Posterior" belief.
	- Bayes' Theorem: $P(A|B) = \frac{P(B|A) P(A)}{P(B)}$
		- $P(A|B)$ is the probability of event $A$ given event $B$,  
		- $P(B|A)$ is the probability of event $B$ given event $A$,  
		- $P(A)$ is the prior probability of event $A$,  
		- $P(B)$ is the prior probability of event $B$.
			- Prior probability is the initial likelihood of an event occurring, based on existing knowledge or assumptions, before considering any new data or evidence.
		- In English: Updated Belief = ( Initial Belief × Strength of New Evidence ) / Normalization
			- Normalization makes sure the final probabilities add up to 1. It adjusts the "weight" of the new evidence so that the total probability remains consistent and doesn't go over 100%.
			- Given by the equation $P(B) = \sum_{i} P(B|A_i) P(A_i)$	
			- Where:
				- $P(B|A_i)$ is the likelihood of the new evidence given each possible hypothesis $A_i$,
				- $P(A_i)$ is the prior probability of each hypothesis $A_i$,
				- The sum over all possible hypotheses $i$ gives the total probability of the evidence $B$.
- The posterior is your new, updated probability distribution for the parameter (e.g., "Now I believe there's a 70% chance the coin is biased").
Key idea: It's about the probability of the **model** (or hypothesis), given the data.
## Simple Takeaway
- Use **Frequentist** methods when you want a strict, objective analysis of an experiment's result.
- Use **Bayesian** methods when you want to incorporate existing knowledge and explicitly update your beliefs with new data.
# Probability 101
## Probability Space
- Experiment: Any process of obtaining or generating an observation. (e.g., Inspecting if an item is defective or non-defective.)
- Sample Space ($\Omega$, omega): A set of all possible outcomes. (e.g., $\Omega$={$\text{{non-defective, defective}}$})
- Events Set ($A\subset\Omega$ or $A\in2^{||\Omega||}$) (A subset of omega or A belongs in 2 to the power of the size of $\Omega$) (Power set of omega): A set of all possible subsets of $\Omega$. (e.g., $2^{||\Omega||}=${$\emptyset$,{$\text{non-defective}$},{$\text{defective}$},$\Omega$)
- Probability Measure $\text{P[E]}$: A function that assigns each event a probability between 0 and 1. i.e., A function $\text{P}$:$2^{||\Omega||}\rightarrow\text{[0,1]}$
## Probability Axioms
Probability Measure follows the below 3 axioms.
- Non-negativity: Probability can never be negative. i.e., $P[A]\geq0$
- Total Probability: The probability of *something* happening is 1. i.e., $P(\Omega)=1$ where $\Omega$ is the set of all possible outcomes).
- Additivity: If two events **cannot** happen at the same time (e.g., getting both heads and tails on one coin flip), the probability of *either* happening is the sum of their probabilities. i.e., If $A∩B=\emptyset$, then $P(A∪B)=P(A)+P(B)$.
	- Equation from lecture: $A_i \cap A_j = \varnothing \;\; \text{if } i \neq j \Rightarrow P\!\left[\bigcup_k A_k \right] = \sum_k P[A_k]$
## Probability Corollaries
$P[A^{c}]=1-P[A]$ by countable additivity and total probability, $P[A^{c}\cup A]=P[A]+P[A^{c}]=1$
$P[\emptyset]=1-P[\Omega]=0$
# Random Variables/Random Vectors
A random variable exists to handle **numerical** outcomes/events.
A random variable X is a function that **assigns a real number** to each of outcome $\omega$ in the same space $\Omega$ of a random experiment.
- e.g., Let X be 1 if a coin flip is heads, and 0 if tails. X is a random variable in this case.
## Bernoulli Random Variable
A Bernoulli random variable is the simplest kind of random variable. It can only take on two values, 1 and 0. It takes on a 1 if an experiment with probability $p$ resulted in success and 0 otherwise.
## Binomial Random Variable
A Binomial random variable is a random variable that represents the number of successes in $n$ successive independent rials of a Bernoulli experiment.
## Cumulative Distribution Function (CDF)
The CDF is a function which takes in a number and returns the probability that a random variable takes on a value less than that number.
For a continuous random variable X the Cumulative Distribution Function, written $F(a)$ is:
$F_X(a)=P(X\leq a) = \int_{-\infty}^{a}f(x)dx$
Problems that can be solved using CDF:

| Probability Query | Solution    | Explanation           |
| ----------------- | ----------- | --------------------- |
| $P(X<a)$          | $F(a)$      | The definition of CDF |
| $P(X\leq a)$      | $F(a)$      | $P(X=a)=0$            |
| $P(X>a)$          | $1-F(a)$    | $P(X<a)+P(X>a)=1$     |
| $P(a<X<b)$        | $F(b)-F(a)$ | $F(a)+P(a<X<b)=F(b)$  |
From lecture:
- The cumulative distribution function (CDF) of a R.V (random variable) X is defined as the probability of the event {$X\leq x$}
- $F_X(x)=P[X\leq x]$ for $-\infty\leq x \leq +\infty$
## Probability Density Function (PDF)
The Probability Density Function defines the likelihood that a random variable takes on a particular value.
The PDF of R.V X is defined as the derivative of $f_X(x)$:
- $f_X(X) = \frac{dF_x(x)}{dx}$, $f_XY(x,y)=\frac{\partial ^{2}}{\partial xy}F_XY(x,y)$
## Probability Mass Function (PMF)
For discrete R.Vs, the PMF is simply the probability that X equals a specific value. i.e., $P(X=x)$
## Random Vectors
A list of multiple random variables. $X=(X_1,X_2,…,X_n)$.
This is how multi-dimensional data points are represented. 
- e.g., a patient’s age, height, and weight.
# Computing Probability: Joint & Conditional Probabilities/Marginalization  
## Equally Likely Outcomes
As equally likely outcomes, $P[A]$ becomes a counting problem.
- $P[A]=\frac{||A||}{||\Omega||}$
e.g., When tossing a **fair** coin N times, compute P (k times H)
$\text{P[k times H]} = \binom Nk\frac{1}{2^{N}}$
- $||\Omega||$ = choose H or T, N times: $2^{N}$
- $||A||$ = choose k among different N without order (??)
## Biased Outcomes
The core idea is that to find the probability of any event, you just need to add up the probabilities of all the individual outcomes that make that event happen.
Therefore:
- $P[A]=\sum_{\omega_k\in A}P[${$\omega_k$}$]$
- The equation says to list all the specific, single ways the event (A) can happen.
- Find the probability of *each* of those single outcomes.
- Add them all together.
## Conditional Probability
# Bayes Rules  
# Important Statistics: mean & variance (random scalar & vectors)  
# Gaussian Density (defined by mean and variance)  
# Maximum Likelihood Estimation (MLE)  
# Sample mean and Sample Variance