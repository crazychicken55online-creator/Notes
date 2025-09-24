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
### Closure
Closure means that if you take any vectors v1 and v2 from the space and any real numbers a and b, the new vector $a*\text{v1}+b*\text{v2}$ must also be a space.
### Subspace
Vector Subspaces are smaller vector space within the larger space. It **must** contain the zero vector and be closed under addition and scalar multiplication.
## Rank & Column, Row, and Null Spaces
A matrix is a rectangular grid of numbers, as such it can be thought of as a set of column vectors or row vectors.
### Rank
The number of **linearly independent** vectors in its column (or row) space. Independent vectors are those that can't be created by combining the others. 
The rank tells you the true "dimension" of the column/row space. 
Note: **The dimension of the row space always equals the dimension of the column space.**
### Column Space
The set of all possible vectors you can create by taking linear combinations of the matrix's column vectors. It shows you all possible outputs of the matrix.
### Row Space
The set of all possible vectors you can create from the matrix's row spaces.
### Null Space
The set of all vectors $x$ that, when multiplied by the matrix $\text{A}$, give the zero vector ($\text{Ax} = 0$). It contains the "hidden" solutions that get squashed to zero by the matrix. The null space is always perpendicular (orthogonal) to the row space.
