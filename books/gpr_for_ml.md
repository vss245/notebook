# Gaussian processes for machine learning

Rasmussen & Williams 2006

### Introduction

- Kernel machines - Support Vector Machines, Gaussian processes
- Stochastic process = generalization of a probability distribution from a n-dimensional random variable to functions
- Bayesian methods help avoid overfitting and do inference
- Adaptive basis functions are useful, but can be hard to use and interpret - fixed basis functions can also be good if there is enough of them
- Gaussian processes are equivalent to many other models

### Mathematical background

- Let n random variables $y_1...y_n$ have a joint probability $p(y)$ (probability / probability density)
- If we separate the y's into sets A and B (disjoint - no common elements), $p(y)=p(y_A,y_B)$
- The marginal probability of $y_A$ is $\int p(y_A,y_B)dy_B$ (or a sum if variables are discrete)
  - Marginal probability = the probability of one subset across the values of the other subset (so sum of probabilities of $y_A,y_B$ across all values of $y_B$)
- The conditional probability is $p(y_A|y_B)=\frac{p(y_A,y_B)}{p(y_B)}$
  - Conditional probability = the probability of one subset given the values of the other
  - If the two variables are independent, conditional probability = marginal probability
- Bayes' rule
  - $p(y_A|y_B)=\frac{p(y_B|y_A)p(y_A)}{p(y_B)}$
- Gaussian distribution of more than one variable has a density given by $p(x|m,\Sigma)=(2\pi)^{-D/2}|\Sigma|^{-1/2}\exp(-\frac{1}{2}(x-m)^T\Sigma^{-1}(x-m))$
  - Extension of the 1D case, with $\sigma=\Sigma$ and $\mu = m$ (matrices instead of values)
- Product of two Gaussians - another Gaussian
- Generating multivariate Gaussian samples:
  - Compute the Cholesky decomposition (aka the matrix sqrt) of K ($K = LL^T$)
  - Generate u ~ N(0,I)
  - Compute x = m+Lu (will have the distribution with mean m and covariance $L*E[uu^T]*L^T$ - second term is an identity matrix => $x = LL^T$)
- Entropy of a distribution is a measure of the uncertainty in the distribution
  - $H(p(x))=-\int p(x)\log p(x)dx$ (or sum for discrete variables)
- KL divergence - relative distance between two distributions
  - $KL(p||q)=\int p(x)\log \frac{p(x)}{q(x)}dx$

### Chapter 1

- Supervised learning - inputs x, output y
- We need to find a function f that will make predictions for input values
  - This requires assumptions about the underlying function
  - Approaches: restricting the class to one (e.g. linear) or giving a prior probability to every possible function (higher probability for more likely ones)
- The second approach is less problematic in terms of making assumptions, but how do we deal with an infinite set of possible functions?
- A Gaussian process is a generalization of the Gaussian distribution
  - Function ~ very long vector, each entry specifying f(x) at x
  - Only need to define properties at a finite set of points
- Bayesian methods for regression and classification:
  - 1D regression
  - We can have a number of sample functions drawn from the prior distribution over functions and then reduce the uncertainty with observations
- Specification of the prior is important - fixes the properties of functions considered for inference
  - Properties <= covariance function of the GP

### Chapter 2 

- GP in regression
- Simple linear regression view - output is a linear combination of the inputs
- Training set D of n observations (x and y)
- $f(x)=x^Tw$, $y = f(x)+\epsilon$
- We assume that y differs from f(x) due to noise (Gaussian)
- Noise + model = likelihood (p(observations|parameters)​ or $p(y|X,w)$)
- In the Bayesian framework, we specify a prior - zero mean Gaussian prior with covariance $\Sigma$ on the weights 
- Posterior = likelihood*prior/(marginal likelihood)
  - Probability of output given data and parameters * probability of parameters / probability of output given data
  -  

### Chapter 4

-  Covariance functions

### Chapter 5

- Learning parameters from data

### Chapter 6

- Relationships to other methods



