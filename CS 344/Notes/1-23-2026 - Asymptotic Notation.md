# Example
## Finding Maximum of an Array:
Problem Statement:
- Given an array $\text{A[1:n]}$, find the largest element.
- Input: Array A of size n.
- Output: Maximum element in A.
Possible Algorithm:
1. Initialize `MAX = A[1]`
2. `For i = 2 to n:`
	1. `If A[i] > MAX, set MAX = A[i]`
3. Return `MAX`
- Time complexity: `O(n)`. It runs through the array once.
Proof of correctness:
- By Induction:
	- Base Case: `i = 1, MAX = A[1]` is correct.
	- Induction step:
		- Assume `MAX = max{A[1], ..., A[k]}`.
		- At `k+1`: Update `MAX` if `A[k+1] > MAX`.
		- Then `MAX = max{A[1], ..., A[k+1}}`.
	- Conclusion: `MAX` is the largest element in A.
## Euclid's Algorithm
```python
def gcd(a, b):
	 if b == 0:
		 return a
	else:
		return gcd(b, a % b)
```
Proof of Correctness:
- Base case:
	- if `b = 0`, the algorithm returns `a`.
	- `gcd(a,0) = a`, since any number divides 0.
		- `a mod 0 = a`
- Inductive Step:
	- To prove Euclid's Algorithm we need to use the fact that `gcd(a,b) = gcd(b, a mod b)`
	- Basically, `d` divides `a` and `b` if `d` divides `a` and `a mod b`.
		- In each recursive call, `b` becomes smaller, and the recursion continues until `b = 0`.
		- The algorithm terminates when `b = 0`, guaranteeing correctness.
# Time Complexity
How do we "measure" the running time of an algorithm?
- Experiments: Plot the run times for various input sizes.
- Experiments need actual implementation. Experiments use only limited inputs.
- Comparing 2 algorithms needs the same software and hardware.
	- Older hardware will naturally take longer to run code.
- Basically, we cannot measure the exact time an algorithm takes, like 3ms, 2ms, etc. We instead calculate the number of steps, written as big O (order of).
Measuring time as steps:
- Count the number of "primitive" operations that need to be executed in some model of computation.
- Look at the asymptotic growth rate.
- Assume worst case.
# Model of Computation
We will use the Random Access Machine (RAM) model of computation.
- A simple operation (e.g., +, $\times$, -, =, if) takes exactly one time step.
- Loops and subroutines are built from simple operations, and their runtime is the sum of the steps of those operations.
- Memory access is unlimited and takes one time step, regardless of whether the data is stored in cache, RAM, or disk.
- The running time is measured by counting the number of steps an algorithm takes for a given input.
Note that this model does not perfectly represent real computers.
## Real Computers vs Ram Model
- **Limited memory**: Access is constrained by physical memory and word sizes.
- **Hierarchical Memory**: Includes registers, L1/L2 caches, and main memory, with different access times.
- **Memory Latency**: Memory access may take multiple cycles depending on where the data is (cache or RAM).
- **Pipelining/Superscalar Execution**: Multiple instructions (1-4 or more) may be executed in a single CPU cycle.
- **Memory Bottleneck**: Data movement between registers and memory can create delays.
- **Branch Prediction**: Modern CPUs guess the outcome of branches to optimize execution.
- **Parallelism**: Modern architectures support parallel execution (multithreading, SIMD).
For example: `x=y+z`:
- This statement takes one step in RAM.
- On a real machine, the `y` and `z` will have to be loaded to the registers, added, and then stored back into `x`.
# Asymptotic Notation
- **Big-O ($O$)**: Upper bound. $f(n) = O(g(n))$ if $f(n) \leq c\times g(n)$ for some $c > 0$ and large $n$.
- **Omega ($\Omega$)**: Lower bound. $f(n) = \Omega (g(n))$ if $f(n) \geq c \times g(n)$ for some $c > 0$ and large $n$.
- **Theta ($\Theta$)**: Tight bound. $f(n) = \Theta (g(n))$ if $c_1\times g(n) \leq f(n) \leq c_2\times g(n)$ for some $c_1,c_2 > 0$ and large $n$.
	- Could think of it as Big-O AND Omega.
- **Little-O ($o$)**: Strict upper bound. $f(n)=o(g(n))$ if $\lim_{n\to \infty} \frac{f(n)}{g(n)} = \infty$
- **Little-Omega ($\omega$)**: Strict lower bound. $f(n) = \omega(g(n))$ if $\lim_{n\to\infty}\frac{f(n)}{g(n)}=\infty$
Note: $log^A(n) << n^E << c^n$
---
# Practice
## Question 1
Which of the following are true?
1. $n^2 + 10nlogn = \Theta(n^2)$
2. $\sqrt{n}=o(n^{\frac{1}{3}})$
3. $n^2logn = O(n^2)$
4. $2^n = \Omega(3^n)$
5. $log^2n = O(n^\epsilon)$ for any $\epsilon > 0$
6. $n^{logn} = O(2^n)$
## Question 2
Mark the correct relationship:

| A            | B            | $O$ | $o$ | $\Omega$ | $\omega$ | $\Theta$ |
| ------------ | ------------ | --- | --- | -------- | -------- | -------- |
| $log^kn$     | $n^\epsilon$ |     |     |          |          |          |
| $n^k$        | $c^n$        |     |     |          |          |          |
| $\sqrt{n}$   | $n^{sin(n)}$ |     |     |          |          |          |
| $2^n$        | $2^{n/2}$    |     |     |          |          |          |
| $n^{log(c)}$ | $c^{log(n)}$ |     |     |          |          |          |
| $log(n!)$    | $log(n^n)$   |     |     |          |          |          |
