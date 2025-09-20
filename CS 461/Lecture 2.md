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
Core idea: Conditional Probability is the chance of one event (A) happening given that another event (B) has already occurred.
- Written as: $P(A|B)$, the probability of A given B.
Example:
Event B+: A person has breast cancer. We know that this is rare, given: P(B+) = 0.008 (0.8%)
Event M+: A mammogram test is positive. (Suggests cancer)
Test accuracy:
- P(M+|B+) = 0.9, If a person *has* cancer, the test will correctly be positive 90% of the time. This is called **sensitivity**.
- P(M+|B-) = 0.07, If a person *does not* have cancer, the test will incorrectly be positive 7% of the time. This is the false positive rate.
Key Question: If a patient gets a positive test result (M+), what is the probability that they *actually* have cancer? Given by P(B+|M+), the probability of having cancer *given* a positive test.
- This is unintuitive as we may think that the probability of someone having cancer given a positive test is 90% (P(M+|B+)), however the actual probability is much lower (P(B+|M+)) as the disease is so rare that the false positive rate (P(M+|B-)) is higher than the true positive rate (P(B+|M+)).
## Joint Probability
Core idea: Joint Probability, $P(\text{A and B})$ or $P(A\cap B)$, is the probability of two events **both** happening.
## Chain Rule
Connects Joint Probability and Conditional Probability. 
Core idea: The probability of A **and** B happening is the probability of A happening multiplied by the probability of B happening **given that A has already happened**.
The Formulas:
- $P(A\cap B)=P(A)*P(B|A)$
- Also works the other way: $P(A\cap B)=P(B)*P(A|B)$
- For three events: $P(A ∩ B ∩ C) = P(A) * P(B | A) * P(C | A ∩ B)$
Example:
What is the probability of drawing 2 aces from a deck of cards?
- Event A: First card is an Ace. P(A) = 4/52
- Event B: Second card is an Ace. Given that the first card is also an Ace. P(B) = 3/51
- Joint Probability: $P(A\cap B) = P(A)*P(B|A)=(4/52)*(3/51)=0.00452488687=0.452$%
## Independent Events
Core idea: Two events are **independent** if the occurrence of one event **does not affect** the probability of the other event happening.
If A and B are independent then: $P(A ∩ B) = P(A) * P(B)$
Why this makes sense: 
- Look at the chain rule: $P(A ∩ B) = P(A) * P(B | A)$. 
- If A and B are independent, then knowing A happened tells us nothing about B. So, $P(B | A)$ is just the normal $P(B)$. 
- Plugging that in gives us $P(A ∩ B) = P(A) * P(B)$.
Example:
Flipping a fair coin twice.
- Event A: First flip is Heads. $P(A) = 1/2$
- Event B: Second flip is Tails. $P(B) = 1/2$
- The first flip doesn't influence the second. They are independent.
- $P(\text{A and B}) = P(\text{First Heads and Second Tails}) = (1/2) * (1/2) = 1/4$.
## Law of Total Probability (Partitioning)
Core concept: This is a method to find the probability of a complex event by **breaking the sample space into simpler, non-overlapping parts**.
The Idea: Imagine you want to know the probability it will rain tomorrow (`P(Rain)`). You could break this down:
- What if a cold front moves in? (`P(Rain | Cold Front)`)  
- What if it doesn't? (`P(Rain | No Cold Front)`)
- Now, weight these conditional probabilities by how likely each scenario (cold front or no cold front) is.
The Process (Partitioning):
1. Identify a set of events (`Ω₁, Ω₂, Ω₃, ...`) that are:
	- **Mutually Exclusive:** No two can happen at the same time.
	- **Exhaustive:** Together, they cover every single possible outcome in the sample space.
2. The probability of any other event (**A**) is the **weighted sum** of its probabilities under each scenario.
The Formula:
- $P(A) = P(A | Ω₁)P(Ω₁) + P(A | Ω₂)P(Ω₂) + P(A | Ω₃)P(Ω₃) + ...$
# Bayes Rules  
Core Concept:
- Bayes' Theorem is a formal, mathematical rule for **updating your beliefs** (probabilities) in the face of **new evidence**.
	- It allows you to "reverse" conditional probabilities. If you know $P(B | A)$, you can find $P(A | B)$
The Formula:
- $P(Ω₁ | A) = [ P(A | Ω₁) * P(Ω₁) ] / [ P(A | Ω₁)P(Ω₁) + P(A | Ω₂)P(Ω₂) + ... ]$
- This is the general form shown on the slide, where $Ω₁, Ω₂,...$ are different scenarios (a partition 
The Components (Using the Plant Example):
- **Posterior Probability ($P(Ω₁ | A)$):** This is what we want to find. It's our **updated belief** about a scenario ($Ω₁$) _after_ we see the evidence ($A$). 
- _Example: The probability your friend forgot to water ($F$)_ after _you see the dead plant ($D$). $P(F | D)$._ 
- **Likelihood ($P(A | Ω₁)$):** The probability of observing the evidence **if** the scenario were true.
	- _Example: The probability the plant dies **if** your friend forgot. `P(D | F)`._    
- **Prior Probability (`P(Ω₁)`):** Our **initial belief** about the scenario _before_ seeing any new evidence.
	- _Example: The probability your friend would forget to water in the first place. `P(F)`._     
	- **Total Probability of Evidence (`P(A)`):** The denominator is the total probability of seeing the evidence, calculated using the **Law of Total Probability** (from Slide 31). It acts as a normalizing constant.
# Important Statistics: mean & variance (random scalar & vectors)  
## Expected Value (Mean) - $\text{E[X]}$
- What it is: The long-run average value of a random variable. It represents the "center of mass" or the central tendency of its probability distribution.
- Why it matters: In ML, the expected value is used to define a model's prediction (e.g., the mean of a predicted distribution) and is the foundation for other concepts like bias and variance.
- Calculation:
    - Discrete RVs: $E[X] = Σ (x_i * P(X = x_i))$ for all possible values $x_i$.
        - _Example: For a fair die, $\text{E[X]} = (1*1/6) + (2*1/6) + ... + (6*1/6) = 3.5$._
    - Continuous RVs: `E[X] = ∫ x * f(x) dx` over all `x`.
        - _This is the continuous equivalent of a weighted average, where `f(x)` is the weighting function (the PDF)._
- Key Property - Linearity of Expectation: This is an incredibly powerful and often non-intuitive property.
    - $\text{E[aX + bY + c] = aE[X] + bE[Y] + c}$
    - **Crucially,** this holds **whether or not $X$ and $Y$ are independent.** This makes it much easier to work with than variance.
## Variance - $\text{Var(X)}$
- What it is: A measure of how much the values of the random variable **deviate from the mean**. It quantifies the spread, scatter, or variability of the distribution. Low variance means data points are clustered near the mean; high variance means they are spread out.
- Why it matters: In ML, variance is a core component of model evaluation and optimization. A model with high variance may overfit to the training data. It's also essential for understanding uncertainty in predictions.
- Calculation:
    - $\text{Var(X)} = \text{E}[ (\text{X} - \text{E[X]})^{2} ]$
    - This formula means: "Find the average of the squared distances of each value from the mean."
- Computational Formula (Simplifies Calculation):
    - $\text{Var(X)} = \text{E[}X^{2}\text{]} - \text{(E[}X\text{])}^{2}$
    - _Derivation:_
        - $\text{Var(X)} = E[(X - μ)²] = E[X^{2} - 2Xμ + μ^{2}]$
        - $= E[X^{2}] - 2μE[X] + E[μ^{2}]$ (by linearity of expectation)
        - $= E[X^{2}] - 2μ * μ + μ^{2}$ (because $E[X] = μ$ and $E[μ²] = μ^{2}$)
        - $= E[X^{2}] - μ^{2}$
- Example: If a random variable $X$ has $E[X] = 2$ and $Var(X) = 7$, what is $E[X^{2}]$?
    - $7 = E[X^{2}] - (2)^{2}$
    - $E[X^{2}] = 7 + 4 = 11$
## Standard Deviation - $\text{σ}$ (sigma)
- What it is: Simply the square root of the variance: $\text{σ} = \sqrt{\text{Var(X)}}$.
- Why it matters: While variance is a mathematically convenient measure, it is in squared units. Standard deviation is in the original units of the data, making it much more interpretable.
    - _Example: If $\text{X}$ is in meters, $\text{Var(X)}$ is in meters², but $\text{σ}$ is back in meters._
## Covariance - $\text{Cov(X, Y)}$
- What it is: Measures the **direction of the linear relationship** between two random variables.  
- Why it matters: It's the building block for the covariance matrix, which is essential for understanding multivariate data and algorithms like Principal Component Analysis (PCA).
- Interpretation:
    - $\text{Cov(X, Y) > 0}$: $X$ and $Y$ tend to move in the same direction (i.e., when $X$ is above its mean, $Y$ tends to be above its mean).
    - $\text{Cov(X, Y) < 0}$: $X$ and $Y$ tend to move in opposite directions.
    - $\text{Cov(X, Y)} ≈ 0$:** No linear relationship. (_Note: They could have a non-linear relationship!_)
- Calculation:
    - $\text{Cov(X, Y) = E[ (X - E[X]) * (Y - E[Y]) ]}$
## Correlation - $ρ$ (rho)
- What it is: A **normalized** version of covariance. It measures both the **strength** and **direction** of a linear relationship.
- Why it matters: Covariance's magnitude is hard to interpret because it depends on the units of $X$ and `Y`. Correlation solves this by being a dimensionless quantity between -1 and 1.
- Calculation:
    - $\rho = \text{Cov}(X, Y) / (\sigma_X * \sigma_Y)$
- Interpretation:
    - $ρ = 1$: Perfect positive linear relationship.
    - $ρ = -1$: Perfect negative linear relationship.
    - $ρ = 0$: No linear relationship.
    - Important Note: Correlation does not imply causation. It also only captures linear relationships; two variables could be perfectly related in a non-linear way (e.g., a parabola) and still have $ρ = 0$.
## Variance of a Sum
- **What it is:** The formula for the variance of a linear combination of two random variables.
- **Why it matters:** This is crucial for analyzing the behavior of combined signals or errors in models.
- **Calculation:**
    - $\text{Var(aX + bY)} = a^{2}\text{Var(X)} + b^{2}\text{Var(Y)} + \text{2ab} \text{Cov(X, Y)}$
    - **If X and Y are independent,** $\text{Cov(X, Y) = 0}$, and the formula simplifies to $\text{Var(aX + bY)} = a^{2}\text{Var(X)} + b^{2}\text{Var(Y)}$.
## Mean Vector - $μ$
- **What it is:** The natural extension of the mean to higher dimensions. It is a `D`-dimensional vector where each element is the mean of one feature.
- **Calculation:**
    - $\mu = E[X] = [E[X_1], E[X_2], ..., E[X_D]]^{T}$
- **Why it matters:** It pinpoints the center of the entire multi-dimensional data cloud.
## Covariance Matrix - $\Sigma$ (Sigma)
- **What it is:** The most important structure for understanding multi-dimensional data. It is a $D\times D$ matrix that captures the variances and covariances between all pairs of features.
- **Calculation:**
    - $Σ = E[ (X - μ) (X - μ)^T ]$
    - The $\text{(i, j)}$-th entry of this matrix is $\Sigma_ij = \text{Cov}(X_i, X_j)$.
    - The $\text{(i, i)}$-th entry (the diagonal) is $\Sigma_ii = \text{Cov}(X_i, X_i) = \text{Var}(X_i)$.
# Gaussian Density (defined by mean and variance)  
# Maximum Likelihood Estimation (MLE)  
# Sample mean and Sample Variance