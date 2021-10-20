### Gaussian processes

- regression tasks find a function that is close to the training data
- mapping view: functions can have a body, like x+1, but they can also be defined as mappings (sin(30)->1/2)
- we can generate training data using an actual sine function and add noise
- Our function f is in the domain R, which can be split into:
  - X is the set of locations from training data (length n), X* is the set of test locations where we want to evaluate the function f (finite, length n*), Xo is the set of locations other than X and X* - infinite length
- for each input location we introduce a random variable f(x) - it has a Gaussian distribution and function values depend on each other 
  - a MV Gaussian is defined by a mean vector [m(X),m(X*),m(Xo)] and a covariance between all of these
    - sq exp kernel:
      - exp and sigma2 are both positive, so the cov is always positive
      - the kernel is at the maximum when x=x' and decreases to 0 when x and x' are inf apart
  - we can write out the cov matrix and omit the Xo entries, the resulting [f(x)f(x*)] = N(mean and cov matrices) will also be Gaussian (due to marginalization)
    - this distribution is the GP prior - assumption on how the values are distributed and this distribution is over functions - the random variable vector [f(x),f(x\*)] represents a function and the distribution over these random variables gives a different probability for each function, the GP prior probability density function takes function value vectors (e.g. x = 1, x* = 2; f(x)=3,f(x*)=4) and returns a probability for them
    - we can draw from the GP prior and plot the resulting functions (e.g. if our distribution is 600 dimensional, the curve will have 600 points)
  - we design the GP prior based on convenience, so it may not represent our training data well 
    - given the training data and the likelihood, we can use Bayes' rule to re-weight the functions, the Bayes' rule outputs the posterior distribution (different probabilities for functions)
    - the likelihood is the probability of observing Y given the random variables f(X) and f(X*) from the prior - there are n observations in Y (random variable y(X) of length n)
      - we define y(X) do be a multivariate Gaussian with mean f(X) and covariance $\eta^2I$ (Noise variance)
        - linear transformation from the random variable f(X) with added Gaussian noise e
      - f(X) already has variance, but this lets us separate some things: f(X) and its variance is about modeling the underlying dynamics and the inherent uncertainty; y(X) is its variance is the uncertainty that occurs during observation

### Notes on MATLAB

- Cross-validation (two ways)
  - cvgprMdl = fitrgp(x,y,'KernelFunction','squaredexponential','Holdout',0.25);
    - trains a single model on 75% of the dataset and outputs a "RegressionPartitionedModel". This contains the trained model in cvgprMdl.Trained{1}
    - holdout loss = kfoldLoss(cvgprMdl)
  -  gprMdl = fitrgp(x,y,'KernelFunction','squaredexponential',... 'OptimizeHyperparameters','auto','HyperparameterOptimizationOptions',struct('Holdout',0.25));
    - runs a BayesianOptimization in which 30 models are fit, each to the same 75% of the dataset, using different hyperparameters
    - the optimization searches for the hyperparameters that minimize the holdout Loss on the remaining 25%. f
    - fter the optimization completes, a final model is fit to 100% of the dataset using the optimal hyperparameters, the returned object is a "RegressionGP"
  - when you don't pass 'OptimizeHyperparameters', fitrgp optimizes the kernel parameters of the chosen kernel function, and Sigma, the noise variance. It does this by maximizing the marginal likelihood (https://www.mathworks.com/help/stats/exact-gpr-method.html). 
  - when you do pass 'OptimizeHyperparameters', it will optimize the parameters you specify, which is some subset of {'BasisFunction','KernelFunction','KernelScale','Sigma','Standardize'}, using Bayesian Optimization, minimizing the out-of-sample MSE as measured using cross-validation.

- Parameters are commonly tuned to maximise the log marginal likelihood
  -  [Chapter 5 of GPML](http://www.gaussianprocess.org/gpml/chapters/RW5.pdf).

https://stats.stackexchange.com/questions/83303/trying-to-understand-gaussian-process

https://stats.stackexchange.com/questions/266552/gaussian-process-regression-with-wide-confidence-interval

https://stats.stackexchange.com/questions/246425/how-to-select-proper-functions-and-hyperparameters-for-gpml-in-matlab