# Maximum likelihood estimation

Myung 2003

- Two methods of parameter estimation: least squares and maximum likelihood
- LSE is not useful for testing hypotheses or constructing confidence intervals
- MLE has consistency, efficiency and invariance

### Probability density function

- Data vector $y = (y_1...y_m)$ is a random sample from an unknown population
- We want to identify the population that has most likely generated this sample
- Each population is identified by a probability distribution
- Each probability distribution is associated with unique model parameters
- A model is the family of probability distributions indexed by model parameters
- $f(y|w)$ is the PDF for p of observing y given parameter w ($w = (w_1...w_k)$)

### Likelihood function

- Inverse problem: given data and a model of interest, find the one PDF that is most likely to have produced the data
- Likelihood function $L(w|y)=f(y|w)$
  - L represents the likelihood of the parameter w given data y
  - f is defined with data on the y-axis, L is defined with parameters on the y-axis

### Maximum likelihood estimation

- Given data and the likelihood function of a model given the data, we can make statistical inferences about the population (PD that underlies the data)
- We are interested in finding the parameter value that corresponts to the desired probability distribution
- MLE estimates do not always exist and are not always unique
- Obtained by maximizing the log-likelihood function
  - e.g. $\frac{\part L(w|y)}{\part w_i}=0$
  - additional condition: $\frac{\part^2 ln L(w|y)}{\part w^2_i}<0$ to ensure it is a maximum
- Most of the time, MLE is found numerically using optimization algorithms
- Sometimes, a local maximum will be found instead of the global one

#### Relationship to LSE

- In LSE, we want to find the parameter values that describe the data most accurately

  - by minimizing sum of squares error

  

