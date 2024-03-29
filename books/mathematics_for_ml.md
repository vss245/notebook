# Mathematics for machine learning

## Chapter 1 - Intro

- goals of the book: formalizing intuitive concepts, linking to practical problems
- other references
  - methods: Bishop 2006, Barber 2012, Murphy 2012
  - programming: Müller and Guido 2016, Raschka 2017
- machine learning is about extracting valuable information from data
  - to achieve this, we degisn models that are related to the process of generating data
  - e.g. regression is a function that maps inputs to outputs
  - goal: find a model that generalizes well
  - learning: oprimizing parameters to find patters and structure
- words for intuition:
  - concepts can be slippery - "algorithms" can be both predictors/models and training of the predictor
- **data** is most commonly represented as a numerical vector (a vector can be an array in CS, an arrow in mathematics and an object in physics)
- a **model** is a process for generating data similar to the dataset at hand (like a simplified version of the real process) - if it's good, it can predict the output of the real process well
- **learning** - using the available data to optimize parameters using a function that evaluates how good the prediction is
  - e.g. climbing a hill to reach the peak
  - but also looking out for overfitting
- ML algorithms discussed: regression, dimensionality reduction, density estimation and classification
- math concepts used: linear algebra to operate on data (in vector and matrix form; matrix decomposition for data representation), analytic geometry (distances to formalize similarity between vectors), probability theory (quantifying uncertainty and the value of the prediction), vector calculus (gradients for optimization)

## Chapter 2 - Linear algebra

- formalizing intuitive concepts involves making a set of a objects (symbols) and rules for manipulating them (= algebra)
- LA studies vectors and ways to manipulate them
- *properties of vectors*: objects that can be added together and multiplied by scalars to produce objects of the same kind
  - geometric vectors (directed line segments)
  - polynomials (match the properties, but are very different from geometric vectors)
  - audio signals (series of numbers)
  - elements of $\R^n$ are vectors - tuples of n real numbers
- what is the set of things that can result from a small set of vectors being added and scaled? **vector space**

### Systems of linear equations

- e.g. a company produces products $N_1..N_n$ with required resources $R_1..R_m$. To produce a unit of product $N_j$, we need $a_{ij}$ units (i = 1..m, j = 1..n) of resource $R_i$. We need to find an optimal production plan of how many units $x_j$ of product $N_j$ if a total of $b_i$ units of resource $R_i$ are available and no resources are left over.
- total units of resource $R_i$: $a_{i1}x_1+...+a_{in}x_n$
- an optimal plan will have to satisfy:
  - $a_{11}x_1+...+a_{1n}x_n=b_1$
  - $a_{m1}x_1+...+a_{in}x_n = b_m$

- solutions to a system of linear equations:
  - some systems have no solution - e.g. if adding two of them contradicts the third
  - we can have a unique solution 
  - or a set of solutions with a free variable (infinite solutions)
- the solution space of two linear equations with two varibles will be an intersection of lines
  - for three variables, same but in three dimensions - we can obtain a solution that is a plane, a line, a point or empty 
- to solve equestions, we can collect the coefficients into a matrix and rewrite the equation as Ax=b

### Matrices

- matrices can represent systems of equations or linear mappings
- a matrix A is an m x n tuple of elements with m rows and n columns

  - we can also represent it by stacking it into a m x n, 1 vector
- **sum of matrices**: element-wise sum
- **product of matrices**: 
  - computed by multiplying ith row with the jth column and summing (a.k.a the dot product of the corresponding row and column)
  - it is **not** an element-wise operation $c_{ij}=a_{ij}b_{ij}$ - this is called a Hadamard product
  - code: C = np.einsum('il,lj', A, B)
  - **dot product between two vectors:** $a^Tb$
  - inner dimensions have to match for multiplication
  - matrix multiplication is not commutative
- **identity matrix: ** 1 on the diagonal, 0 everywhere else
- **properties of matrices:**
  - Associativity: (AB)C = A(BC)
  - Distributivity = (A+B)C = AC + BC
  - Identity multiplication: IA = A
- **inverse:**
  - if A is a square matrix n x n, then B is a square matrix n x n with the property that AB = I = BA => $B = A^{-1}$
  - not every matrix has an inverse (is invertible/regular/non-singular)
  - if it does not have an inverse, it's called singular/non-invertible
  - an inverse is unique
  - for a 2x2 matrix [a b; c d], the inverse is 1/det \* [d -b; -c a]
  - $(AB)^{-1}=B^{-1}A^{-1}$
  - $(A+B)^{-1}\not=A^{-1}+B^{-1}$
- **transpose:**
- rotate the matrix from m x n to n x m
  - $(A^T)^T=A$
  - $(A+B)^T=A^T+B^T$
  
- $(AB)^T=B^TA^T$
- **symmetric matrix:**
  - a matrix is symmetric if $A = A^T$
  - only square matrices can be symmetric
  - the sum of symmetric matrices is always symmetric, but the product isn't
- **scalar multiplication**:
  - scales each element
  - associative and distributive
- a system of linear equations can be rewritten as $Ax = b$
- x's will be a column vector where x1 will scale the first column in A, x2 the second etc
- **solving systems:**
  - $1x_1+0x_2+8x_3-4x_4=42$
  - $0x_1+1x_2+2x_3+12x_4=8$
  - since we have 2 equations and 4 unknowns, we would have infinitely many solutions
  - we want to find scalars such that $x_ic_i=b$, where c is each column of the matrix
  - one particular solution would be [42, 8, 0, 0] - because we can just express the other terms as 0
  - we can express the third column [8;2] using the first two = [8;2]=8[1;0]+2[0;1]
    - so that x's = 8, 2, -1, 0
    - after multiplication, it is 8+2-8-2+0=0
  - we can also express the 4th column using the first two = -4 12 0 -1, which is -4+12+0+4-12=0
  - therefore, we obtain a set of solutions: x = [42 8 0 0]+L1[8 2 -1 0]+L2[-4+12+0-1] where L1 and L2 is in R (the L's are there because the solutions can be scaled)
  - we do this because finding solutions to Ax=0 helps us find all the solutions to Ax=b (the 0 solutions are a subset of all solutions)
  - the solution of Ax=0 is also called the kernel
  - we can solve them using Gaussian elimination to transform into a particular form
  - https://mathworld.wolfram.com/GaussianElimination.html
- Ax = b can be represented in augmented notation as [A|b], omitting x
- **elementary transformations:**
  - exchanging two equations
  - multiplication of a row with a constant
  - addition of two rows
- we can put the matrix into **row-echelon form (REF)**
  - all rows with only zeros are at the bottom
  - in non-zero rows, the first non-zero number from the left is always strictly to the right of the pivot of the row above it (of the first non-zero number)
- this form gives us a convenient way of getting the solution
- **reduced row echelon form (RREF):**
  - row-echelon form
  - every pivot is 1
  - the pivot is the only non-zero entry in the column
- **minus 1 trick:**
  - we can extend matrices to an nxn matrix by adding n-k rows of the form [0 0 -1 0 0] so that we have either 1 or -1 on the diagonal of A
  - then the columns with -1 as pivots will be solutions of Ax=0
- **inverse:**
  - to compute the inverse, we need to find a matrix X that satisfies AX = I
  - we can write this down as a set of equations where we solve for x
  - $[A|I] => [I|A^{-1}]$
    - if we bring the augmented equation system into RREF, we can read out the inverse
    - determining the inverse is equivalent to solving systems of linear equations
- **algorithms for solving a system of linear equations:**
  - assume that a solution exists (if it doesn't, we need to get approximate solutions)
  - we may be able to determine the inverse which will be a solution $x = A^{-1}b$
    - but A needs to be square and invertible
  - if A has linearly independent columns, we can use $Ax=b$ => $A^TAx = A^Tb$ => $x = (A^TA)^{-1}A^Tb$
    - where $(A^TA)^{-1}A^T$ is a pseudo-inverse (minimum norm least squares solution)
    - however, this isn't really computationally feasible
  - Gaussian elimination is useful for determinants, checking linear independence, computing the inverse and rank of a matrix and determining a basis of vector space
    - but for large systems it can be impractical
  - there are iterative methods for solving large systems of equations
    - the idea is to set up an iteration of the form $x^{k+1}=Cx^{(k)}+d$ that reduces the residual error term $||x^{k+1}-x||$
- **groups:**
  - formalizing the concept of vectors and their spaces
  - a **group** is a set of elements and an operation defined on these elements that keeps some structure of the set intact
  - a set $\mathcal{G}$ and an operation $\otimes$: $\mathcal{G} \times \mathcal{G} \rightarrow \mathcal{G}$
  - $G :=(\mathcal{G},\otimes)$ is a group if these hold:
    - closure under the operation (e.g. applying it results in members of the same set)
    - associativity $(x \otimes y) \otimes z = x \otimes (y \otimes z)$
    - neutral element (like the identity matrix or 1)
    - inverse element ($x^{-1}$)
    - if $x\otimes y = y\otimes x$, then the group is also Abelian
  - examples:
    - integers (positive and negative) and + is an Abelian group
    - natural numbers and + is not a group (no inverse)
    - integers and multiplication is not a group (no inverse)
    - real numbers and multiplication is not a group (no inverse)
    - set of $m\times n$ matries is Abelian (with component-wise addition)
      - component-wise addition: $(x_1,...,x_n)+(y_1,..,y_n)=(x_1+y_1,...,x_n+y_n)$
  - the set of $n \times n$ matrices has closure, associativity, a neutral element and inverses => it is a general linear group together with multiplication
- **vector spaces:**
  - consider sets that have addition and multiplication by a scalar 
  - a real-valued vector-space is a set V with two operations 
    - $\mathcal{V} + \mathcal{V} \rightarrow \mathcal{V}$ 
    - $\R \times \mathcal{V} \rightarrow \mathcal{V}$ 
  - neutral element is the zero vector
  - vector multiplication $ab$ is not defined (but $a^Tb$ (inner/dot product) and $ab^T$ are defined)
- **vector subspaces:**
  - these are sets contained in the original vector space with the property that performing vector space operations on elements within this subspace keeps everything in the subspace
  - properties from the vector space are inherited by the subspace 
- **linear independence:**
  - we can add vectors together and multiply them with scalars to stay in the vector space
  - we can find a set of vectors that can represent every vector in the space using these two operations (this is known as the basis)
  - **linear combination**: $v = \lambda_1x_1+...\lambda_nx_n$ is a linear combination of vectors $x_1...x_n$
  - the 0 vector can always be written as the linear combination of vectors
  - **linear independence:** vectors $x_1..x_n$ are linearly dependent if there's a non-trivial linear combination such that $0 = \sum \lambda_i x_i$ with at least one non-zero lambda
  - linearly independent vectors have no redundancy
  - properties:
    - if at least one vector is 0 or identical to another, then they are linearly dependent
    - same for if one of the vectors is a multiple of another
    - dependency can be checked via Gaussian elimination (REF)
      - if there's at least one non-pivot column, then they are dependent
  - if we have a vector space V with k linearly independent vectors $b_1..b_n$ and m linear combinations $x_1 = \sum\lambda_{i1}b_i$, we define B as the matrix with b as columns and we can write $x_j = B\lambda_j$
    - to test whether vectors x are linearly independent, we can check whether the column vectors lambda are linearly independent
- **basis:**
  - in a vector space V, we are interested in sets of vectors A that can form any vector in V by linear combination (basis vectors)
  - if every vector v in V can be expressed by a linear combination of vectors in A, then it is called **a generating set** of V and the set of all linear combinations of vectors in A is called the **span** of A
  - if A spans V: $V = span[A]$
  - a generating set A of V is called minimal if there is no smaller set 
    - every linearly independent generating set of V is called a **basis** of V
  - in $\R^3$, the canonical basis is [1 0 0], [0 1 0] and [0 0 1]
  - there is no unique basis of a space - there can be many of them
- the dimension of V is the number of basis vectors of V 
- finding the basis of a subspace:
  - write the spanning vectors as columns of a matrix A
  - determine the REF 
  - the spanning vectors associated with the pivot columns are a basis of U
- **rank:**
  - the number of linearly independent columns of a matrix A equals the number of linearly dependent rows and is called the rank 
  - properties:
    - column rank equals row rank
    - the columns of A span a subspace U, where the dimension of U is the rank of A (this subspace is also called the **image** or **range**)
    - a square matrix of size n is only invertible if its rank is also n
    - for all A in $\R^{m \times n}$ and b in $\R^{m}$ , Ax = b is only solvable if rank of A is equal to rank of A|b (the augmented system)
    - the subspace of solutions for Ax = 0 has the dimension of n - rank(A) - this is also known as the **kernel** or **null space**
    - a matrix has full rank if its rank equals the largest possible rank for a matrix of the same dimension (lesser of the number of rows and columns)
- **linear mappings:**
  - we want to preserve vector properties when applying a mapping
  - e.g. if we have a mapping $\Phi$ from vector space V to W, we preserve the structure if $\Phi(x+y)=\Phi(x)+\Phi(y)$ and $\Phi(\lambda x)=\lambda\Phi(x)$
  - a linear mapping is also called a linear transformation
  - we can represent linear mappings as matrices!
- cases of mappings (e.g. for A and B):
  - injective if $\forall x,y \in V : \Phi(x)=\Phi(y) \Rightarrow x = y$ (a.k.a one-to-one of A to B)
  - surjective if $\Phi(V)=W$ (e.g. at least one B for every A)
  - bijective if both of the above (e.g. A to B maps perfectly)
- isomorphism - linear and bijective
- x -> x is the identity mapping
- theorem: there is a linear bijective mapping between two vector spaces of the same dimension (e.g. they can be transformed into each other without loss)
  - therefore, any n-dimensional vector space is isomorphic to $\R^n$
- basis notation: $B = (b_1,...,b_n)$ (ordered), $B = \{b_1,...,b_n\}$ (unordered)
- **coordinates:** consider a space V and a basis B. for any x in V we can get a unique representation $x = \alpha_1b_1+...+\alpha_nb_n$ where the $\alpha$'s are the coordinates!
  - a basis defines a coordinate system
  - e.g. Cartesian coordinates have canonical basis vectors $e_1,e_2$, but any basis of $\R^2$ will define a valid coordinate system
- **transformation matrix:** consider vector spaces V, W with corresponding ordered bases B and C
  - consider a linear mapping $\Phi$ from V to W
  - for j in (1..n), $\Phi(b_j)=\sum_{i=1}^m\alpha_{ij}c_i$
  - the matrix A whose elements are given by alpha will be the transformation matrix of $\Phi$
  - the coordinates of $\Phi(b_j)$ with respect to the basis C of W are the j-th column of A
  - the transformation matrix can be used to map coordinates with respect to an ordered basis in V to coordinates wrt to a basis in W
- **basis change:**
  - basis change example: if we have a matrix A = [2 1; 1 2] with respect to the canonical basis, we can define a new basis B = ([1 1], [1 -1]), in which the matrix A will become [3 0; 0 1], which is easier to work with
  - consider two ordered bases of V (B and B\*) and two ordered bases of W (C and C\*)
  - A (size m x n) is the transformation matrix of the linear mapping from V to W with respect to B and C
  - and A\* is the transformation mapping with respect to B\* and C\*, where $A^* = T^{-1}AS$, where S is the matrix mapping B* coordinates onto B and T is the matrix mapping C* coordinates onto C
- **image and kernel:**

