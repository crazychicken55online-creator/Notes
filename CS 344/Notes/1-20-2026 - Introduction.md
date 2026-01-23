# What is an algorithm?
- An algorithm is a set of instructions aimed to solve a specific problem. 
# Multiplication
## Lattice Multiplication
- Lattice multiplication is a multiplication algorithm which organizes a multiplication problem around a grid based on the digits' place value.
- It then uses the distributive property of multiplication, and, following several well-defined steps to find the product.
- E.g., Solve $48\times 36$ using lattice multiplication:
	- First you need to draw a 2 x 2 lattice box, as 48 has 2 digits and 36 has 2 digits.
	- Then you draw diagonals from the top right to the bottom left.
	- Write one of the factors across the top and then write the other one down the right side.
	- ![[Lattice Multiplication Example.png]]
	- For each number combination (8 and 3, 4 and 6, etc.) find the box where the intersect and record the resulting multiplication.
	- ![[lattice multiplication example 2.png]]
	- This tells us that there are 8 ones, 4+4+4 = 12 tens which will end up being 2 tens with a carry, 2+2+2 = 6 hundreds but you need to add the one from the carry so it's 7 hundreds, and 1 thousands.
	- Therefore, via lattice multiplication, we know that the digits are 1,7,2,8 so $48\times 36 = 1728$
	

# Bad Example
## Martin's Algorithm:
```text
BeAMillionaireAndNeverPayTaxes():
Get a million dollars.
If the tax man comes to your door and says, "You have never paid taxes!"
	Say "I forgot."
```
- This is not an algorithm, even though it is pretty simple, as the first step is non-trivial.
- For most people getting a million dollars is ambiguous and impossible.
- This is an example of **reduction**, it *reduces* the problem of being a millionaire and never paying taxes to the "easier" problem of acquiring a million dollars.
- If you know how to solve the "easier" problem of being a millionaire then reduction tells you how to solve the "harder" problem of tax evasion.
# Describing Algorithms
- We need to know certain things in order to effectively **design** and **analyze** algorithms.
	- This needs us to know how to **describe** algorithms.
- Any Algorithm has four components:
	- **What**: What is the problem that the algorithm is trying to solve.
	- **How**: How does the algorithm work.
	- **Why**: Why does the algorithm work (a proof that it does what it is supposed to).
	- **How Fast**: An analysis of the running time of the algorithm (Big O).
## Breadth First Search (BFS)
## Numerical Algorithms
- Numerical algorithms solve mathematical problems through numerical approximation.
- Numerical algorithms are common in scientific computing, engineering and finance.
- E.g., Root finding, Numerical integration, and solving differential equations.
- E.g. 2, Computing $\pi$: 
	- *Note that $\pi$ is the area of a circle when radius = 1*
	- You could use the *Monte Carlo* Method:
		- You generate random points in a unit square.
		- Count said points inside the circle.
		- Estimate $\pi$ as $4\times \text{(points in circle/total points)}$
	- You could use the *Leibniz Formula*.
	- You could use *Ramanujan's Formula*.
## RSA Cryptosystem
- RSA stands for Rivest-Shamir-Adleman.
- An RSA Algorithm is a security algorithm based on the hardness of factoring large n.
- It works via asymmetric encryption, as the RSA cryptosystem requires both a public key and a private key, unlike symmetric systems which only use one key.
- The public key (shared with everyone) is used to encrypt data and the private key (secret) is used to decrypt data.
- It works based off of the difficulty of factoring the product of two large prime numbers, also known as the *prime factorization problem*.
## Euclid's Algorithm
- Developed by ancient Greek mathematician Euclid around 300 BC to find the Greatest Common Divisor (GCD) of two integers.
```python
def function gcd(a, b):
	if b == 0:
		return a
	else:
		return gcd(b, a % b)
```
## Linear Programming
- In Linear Programming you must first determine the best possible outcome (such as maximum profit or lowest cost).
- You must find the **Objective Function**: A linear function that is to be maximized or minimized.
- You must find the **Constraints**: Linear inequalities or equations that restrict the values of the variables.
- Linear Programming is widely used in industries for resource allocation, production scheduling, transportation, and logistics.
# Design Techniques
## Divide and Conquer
- Break a problem into smaller sub-problems, solve each independently, and combine their solutions.
- E.g., Merge Sort
## Greedy Algorithms
- Make the best local choice at each step with the hope of finding a global optimum.
- E.g., Activity Selection Problem
	- Goal: Select the maximum number of non-overlapping activities.
	- Greedy Approach: Always pick the activity that finishes the earliest.
## Dynamic Programming
- Break down a problem into overlapping subproblems, solve each just once, and store their solutions.
- Has recursive and iterative approach (top-down versus bottom-up).
Unoptimized, not dynamic programming solution for Fibonacci:
```python
def fib(n):
	if n <= 1:
		return n
	return fib(n-1) + fib(n-2)
```
- A lot of repeat calculations, ends up being O(2^n), which is not ideal.
```python
def fib(n):
	if n == 0:
		return 0
	prev = 1
	sum = 1
	for i in range(2, n+1):
		temp = sum
		sum += prev
		prev = temp
	return sum
```
Optimized, O(n), iterative solution. Less elegant but much faster.