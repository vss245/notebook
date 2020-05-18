# Linear algebra

LA is about translating things from m-dimensional to n-dimensional spaces

## Numbers
- Complex = $a + b*i$, $i = \sqrt{-1}$
- Integers - +/- natural numbers, 0
- Rational - Terminating decimals, non-terminating decimals
- Irrational - $\pi$ or $\sqrt{2}$ etc
- Imaginary - $z = 0 + b*i$ - for solving things like $x^2 + 5 = 0$

## Logic 
- Proposition - a sentence that's either true or false
- If P then Q: $P \rightarrow Q$
  - Does not imply $Q \rightarrow P$
  - If both $P\rightarrow Q$ and $Q \rightarrow P$ are true, then $P \Leftrightarrow Q$

## Sets
- X belongs to set Y = $X \in Y$ 
- Set X is in set Y = $X \subset Y$

## Functions
- Function from X to Y is the rule that binds elements in X to elements in Y 
  - $F:X->Y$
- X is the domain, Y is the co-domain
### Images
- Assume $x_i \in X$
- Elements in Y that correspond to $x_i$ are called $x_i$'s image under f in Y 
- Element x of the set x goes together with the element 2x-1 in the set Y
- $f(2)$ implies that the image of 2 under f is $2*2-1$
- X is the domain
- Y overall is the co-domain, image of x under f in Y is the range (values in Y that actually mapped to)
### Onto and one-to-one
- A function is onto if its image is equal to the codomain (all the elements of Y are
being mapped onto)

- If $x_i \ne x_j \rightarrow f(x_i) \ne f(x_j)$,function is one-to-one (no element in the co-domain can
mapped onto more than one)
- can be both

### Inverse functions
- Mapping from Y onto X instead of from X onto Y
- $g(f(x_i))=x_i$
- $f(g(y_i))=y_i$

## Linear transformations
### Conditions
- $f(x_i) + f(x_j) = f(x_i + x_j)$
- $c*f(x)=f(c*x)$
- For example, 2x is linear, 2x-1 is not
## Matrices
- Values organized in m columns and n rows

- Addition, subtraction, scalar multiplication are performed elementwise

  $\begin{pmatrix}1&2\\3&4\end{pmatrix} + \begin{pmatrix}1&2\\3&4\end{pmatrix} = \begin{pmatrix}2&4\\6&8\end{pmatrix}$

  $\begin{pmatrix}1&2\\3&4\end{pmatrix} - \begin{pmatrix}1&2\\3&4\end{pmatrix} = \begin{pmatrix}0&0\\0&0\end{pmatrix}$

  $\begin{pmatrix}1&2\\3&4\end{pmatrix} * 2 = \begin{pmatrix}2&4\\6&8\end{pmatrix}$

  - Matrix multiplication: RxC

  $\begin{pmatrix}1&2\\3&4\end{pmatrix} * \begin{pmatrix}1&2\\3&4\end{pmatrix} = \begin{pmatrix}1*1+2*3&1*2+2*4\\3*1+4*3&4*2+4*4\end{pmatrix}=\begin{pmatrix}7&10\\15&22\end{pmatrix}$

- Types
  - Zero
  - Transpose (switch R and C)
  - Symmetric (around the diagonal)
  - Upper/lower triangular
  - Diagonal
  - Identity
  - Inverse
  
- Inverse matrices
  - Found by Gaussian elimination
  - To see if matrix is invertible, use the determinant (if it's not 0, the inverse exists)
## Vectors
- Special interpretation of matrices (1xn and nx1)
- Can represent:
  - Points in space
  - Arrow from origin to point
  - Sum of several arrows to point
  - Arrows from anywhere, not just the origin
## Bases
- If there's a unique solution to $c_1*(M)+c_2*(M)$ = zero matrix
  - Vectors are linearly independent
  - Can form the basis for $R^n$
- If >1 solution
  - Linearly dependent
- Basis - minimal set of vectors needed to express a vector in $R^n$
## Subspaces
- Closed under multiplication (element in W multiplied by c is still an element in W)
- Closed under addition (sum of two arbitrary elements in W is an element in W)
## Span
- A subspace can be spanned by scalar multiplication and addition of vectors
## Coordinates
- Can be expressed using trivial bases (0,1) and (1,0)
- But can also be expressed using any bases
## Linear transformations
- Same definition as above, but for vectors
## Rank
- Defines the transformation (if output is 1D - rank 1, 2D - rank 2 and so on)
## Eigenvalues and eigenvectors
- If the image of X through the transformation defined by M is $\lambda X$, then $\lambda$ is the eigenvalue and X is the corresponding eigenvector







