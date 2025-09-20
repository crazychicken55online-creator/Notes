# Why Linear Algebra
- Data representation/transformation in a vector space (high dimensional)  
- Provides tools to understand the geometric shape of high dimensional data (decorrelation: whitening & data compression: PCA)  
- A linear regression problem can be translated into solving a linear system.  
- Linear Algebra plays a role in every stage of machine learning from (1) data preprocessing to (2) modeling and learning.
## Linear Regression
Linear Regression Model: $𝑎𝑋_1 + 𝑏𝑋_2 + 𝑐𝑋_3 = 𝑌$
𝑎, 𝑏, 𝑐 can be found by solving the linear system below
![[Linear Regression Image 1.png]]
# Linear Algebra 101
## Vector Space and Subspace
A vector space ($ℝ^{𝑁}$) is a set of vectors that is closed by linear combinations.
- Linear combinations are vector addition and multiplication by real number
Vector Addition and Multiplication by a real number follows 8 rules.
1. $x+y=y+x$
2. $x+(y+z)=(x+y)+z$
3. There is a unique zero vector such that $x+0=x$ for all $x$
4. For each $x$ there is a unique vector $-x$ such that $x+(-x)=0$
	- 3. and 4. are additive identities.
5. $1x=x$
6. $(c_1*c_2)x=c_1(c_2*x)$
7. $c(x+y)=cx+cy$
8. $(c_1+c_2)x=c_1x+c_2x$
