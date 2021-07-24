### Chapter 2

1. Flexible vs inflexible statistical methods (e.g. non-linear vs linear regression):
   - n >> p - flexible methods would perform better
   - p >> n - either method would not be very good, but flexible method would overfit
   - highly non-linear relationship - flexible methods would be better due to having a better fit to the data
   - variance of the error terms is very high - non-flexible method would be better, as a flexible method is likely to overfit
2. Classification or regression problem?
   - Data: 500 firms, profit, # employees, industry and salary - which factors affect salary? Regression problem, trying to model the relationship between all the factors and the salary
   - Data: 20 products, success/failure, prices, budget - will our product be a success or a failure? Classification problem, we are trying to predict what class our product will be in
   - Data: weekly % change in USD/EUR exchange rate - regression problem
3. Bias-variance decomposition
   - Bias will decrease as we go from less flexible to more flexible models (better fit to the data)
   - Variance will increase (highly complex models less likely to generalize well)
   - Training error will decrease, but test error will decrease and then increase (overfit models don't generalize well)
   - Irreducible error will stay constant
4. Real-life applications 
   - Classification: predicting a diagnosis from symptoms and demographic data
   - Regression: modeling the relationship between a behavioural outcome and interventions
   - Cluster analysis: clustering consumers into groups based on activity to refine recommendations
5. Advantages and disadvantages of flexible approaches - a flexible approach will make less assumptions about the data, but can also overfit and is computationally more intensive. Inflexible approaches such as linear regression are easy to use and interpret, but do not take many data features into account.
6. - green, distance of 1 neighbor from [0 0 0] closest to observation 5
   - red, closest to observations 2, 5, 6, two out of which are red
   - If the boundary is non-linear, a smaller number of neighbors will allow us to be more flexible

### Chapter 3

1. Describe the null-hypothesis for p-values in Table 3.4: each of the coefficients corresponds to the effect of that regressor on the fit, so the null hypothesis for TV, radio and newspaper is that these advertising methods have no effect on the number of units sold.
2. KNN classifier vs KNN regression - KNN classifier is a classification method that allows us to cluster observations into classes based on the classes of their neighbors. KNN regression is a computationally simple regression method where the value of $\hat{Y}$ at a point is the averaged value of K neighbors.
3. Assume the following model for salary: $Y = 50 + 20*GPA + 0.07*IQ + 35*Gender + 0.01*GPA*IQ + (-10)*GPA*Gender$
   - For fixed IQ and GPA, males earn more for high GPAs, but not for low GPAs
   - For a female with 110 IQ and 4 GPA, the salary will be 137.1
   - Coefficient for the GPA\*IQ term is small, which means a small effect, but not necessarily small evidence, that will depend on the p-value and the alpha level
4. For two models with a single predictors, linear ($Y = \beta_0+\beta_1X$) and cubic ($Y = \beta_0+\beta_1X+\beta_2X^2+\beta_3X^3+\epsilon$)
   - If the relationship is linear, which RSS is lower? Training RSS will probably about the same. Test RSS in the linear model will be lower, a cubic model might overfit the training data.
   - If the relationship is not linear, but it's not clear how far from linear, which RSS is lower? Cubic model training RSS will be lower (better fit to data), but test RSS will depend on how close the model is to cubic.

### Chapter 4

1. We can prove that $p(X)=\frac{e^{\beta_0+\beta_1X}}{1+e^{\beta_0+\beta_1X}}$ and $\frac{p(X)}{1-p(X)}=e^{\beta_0+\beta_1X}$ are equivalent by substituting the $p(X)$ into the second equation and simplifying.
2. Under the assumption that the observations in class k are from a distribution with mean $\mu_k$ and variance $\sigma^2$, the Bayes classifier will assign the class for which the discriminant function is maximized
   - Show that $p_k(x)=\frac{\pi_k\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{1}{2\sigma^2}(x-\mu_k)^2})}{\sum_{l=1}^K\pi_l\frac{1}{\sqrt{2\pi}\sigma}exp({-\frac{1}{2\sigma^2}(x-\mu_l)^2})}$ and $\delta_k(x)=x\cdot\frac{\mu_k}{\sigma^2}-\frac{\mu_k^2}{2\sigma^2}+log(\pi_k)$ are equivalent
     - a part of the first equation does not depend on k: $\frac{\frac{1}{\sqrt{2\pi}\sigma}\exp(-1/2\sigma^2x^2)}{\sum_l\pi_l\frac{1}{\sqrt{2\pi}\sigma}\exp(-1/2\sigma^2(x-\mu_l)^2)}$
     - we can take the log of the first equation, which results in $ \log(p_k(x)) = \log(\pi_k) + \log(C) + \frac{1}{2\sigma^2}(2\mu_kx - \mu_k^2) $ - if we ignore the C part (not relevant to k), it can be rearranged to equal delta
3. -
4. -
5. LDA vs QDA
   - If the decision boundary is linear, LDA or QDA? QDA might still be better on the training set, but not on the testing set (might overfit)
   - If the boundary is non-linear, QDA will perform better
   - As sample size increases, QDA will probably perform better
   - If the Bayes decision is linear, we might not get a better result with QDA, since it can overfit to some observations/
6. Logistic regression model: $p(X)=\frac{e^{-6+0.05*hours+1*GPA}}{1+e^{-6+0.05*hours+1*GPA}}$
   - Probability for 40 hours and 3.5 - $\frac{0.0606}{1.0606}\approx37\%$
   - For a 50% chance, 50 hours (plug in the values and solve for x)
7. -
8. If K = 1, the boundary will be fit exactly to the training data, so the test error will be 36% ($\frac{x+0\%}{2}=18\%$), so logistic regression will be better
9. Odds
   - $\frac{p(x)}{1-p(x)}=0.37$, so $p(x)=27\%$
   - same formula, 19%

### Chapter 5

1. Derive (5.6): 
   - we want to minimize $Var(\alpha X+(1-\alpha)Y)$
   - $\sigma^2_X=Var(X)$, $\sigma^2_Y=Var(Y)$, $\sigma_{XY}=Cov(XY)$
   - Formula for variance of a sum: $Var(aX+bY)=a^2Var(X)+b^2Var(Y)+2abCov(XY)$, or, in our case $Var= \alpha^2\sigma^2_X+(1-\alpha)^2\sigma_Y^2+2\alpha(1-\alpha)\sigma_{XY}$
   - Derivative of above with respect to $\alpha$: $\alpha^2\sigma^2_X+\sigma_Y^2-2\alpha\sigma^2_Y + \alpha^2\sigma^2_Y+2\alpha\sigma_{XY}-2\alpha^2\sigma_{XY}$
   - Set to zero, rearrange: $\alpha = \frac{\sigma^2_Y - \sigma_{XY}}{\sigma^2_X+\sigma^2_Y-2\sigma_{XY}}$
2. Probability that a given observation is part of a bootstrap sample from a set of n observations
   - Probability that the first bootstrap observation is not the jth: $1-\frac{1}{n}$ (because the probability of getting the jth observation out of n will be 1/n)
   - Same question, but for the second observation: $1-\frac{1}{n}$ (same, because we sample with replacement)
   - Probability of not selecting the jth observation for a sample will be n-1, for n selections, the probability is $(\frac{n-1}{n})^n$ or $(1-\frac{1}{n})^n$
   - When n = 5, the probability that jth observation is in the sample is 1 - the above probability, so $p = 1 - (1-1/5)^5 = 0.672$
   - $p = 1 - (1-1/100)^{100} = 0.634$
   - $p = 1 - (1-1/10000)^{10000} = 0.632$
   - Probability of jth observation being in the sample asymptotes at 0.63
3. k-fold cross-validation
   - We split the data into k groups, the first group is the test set and the remaining groups are the training set. We calculate the error on the test set. Repeat k times and use the average MSE as the answer.
   - Relative to the validation set approach, we have a more flexible method as we have separate validation sets - with just one test set, we may get one that under- or over-estimates the MSE. Relative to LOOCV, k-fold CV is easier to run (complexity depends on k, not on n).
4. We use a mthod to make a prediction for Y based on X. How do we estimate the standard deviation of our prediction? We can use bootstrapping, make multiple predictions of Y and get their error and use it to estimate the standard deviation.

### Chapter 6

1. Comparing best subset, forward stepwise and backward stepwise selection
   - Which of the models will have the smallest training RSS? Best subset will try every combination so will probably fit the data closest
   - Test RSS? Best subset generally, but it might be the case that forward/backward stepwise selection will find a good model too
   - True or false:
     - The predictors in the k predictors model from forward stepwise are a subset of the result of the (k+1) forward stepwise - true
     - The predictors in the k predictors model from backward stepwise are a subset of the result of the (k+1) backward stepwise - true
     -  The predictors in the k predictors model from backward stepwise are a subset of the result of the (k+1) forward stepwise - false, the predictors may not be the same between the two
     - The predictors in the k predictors model from forward stepwise are a subset of the result of the (k+1) backward stepwise - false, same reason
     - The predictors in the k predictors model from best subset are a subset of the result of the (k+1) best subset - false, predictors may become less useful in some combinations
2. Find correct options
   - The lasso, relative to least squares, is less flexible (will select variables) and will give improved predictions when its increase in bias is less than its decrease in variance (due to selecting coefficients, will decrease variance a lot)
   - Ridge regression, relative to least squares, is less flexible (will constrain coefficients) and will give improved predictions when its increase in bias is less than its decrease in variance
   - Non-linear methods, relative to least squares, are more flexible (will select variables) and will give improved predictions when its increase in variance is less than its decrease in bias (predictions will have a higher variance due to flexibility)
3. Suppose that we minimize $\sum_{i=1}^n(y_i-\beta_0-\sum_{j=1}^p\beta_jx_{ij})^2$ subject to $\sum_{j=1}^p|\beta_j|\leq s$ (the lasso)
   - As we increase s from 0, the coefficients will increase from 0 to their least squares versions (as if there's no penalty), so the training error will decrease (better fit). The test error will decrease initially and then increase (larger values might overfit). Variance in this model will increase, as the coefficients get larger and the model will have a worse fit to test data. Squared bias will decrease, as a more complex model with higher coefficients will have a better fit. Irreducible error stays constant.
4. Suppose that we minimize $\sum_{i=1}^n(y_i-\beta_0-\sum_{j=1}^p\beta_jx_{ij})^2 + \lambda\sum_{j=1}^p\beta^2_j$ (ridge regression)
   - As we increase $\lambda$ from 0, the penalty will have a larger effect so the model will constrain the coefficients and the training error will increase. The test error will decrease, as the model will be a better generalized fit, but then increase as the model becomes too simple when it's too constrained. Variance will decrease as the model is constrained, bias will increase. Irreducible error stays constant.
5. Ridge regression tends to give similar coefficients to correlated variables, the lasso may give different coefficient values to those. Suppose n = 2, p = 2, $x_{11}=x_{12}$, $x_{21}=x_{22}$, also $y_1+y_2=x_{11}+x_{21}=x_{12}+x_{22}=0$, so $\beta_0 = 0$
   - Write out the ridge regression optimization problem:
     - $\sum_{i=1}^n {(y_i - \sum_{j=1}^p {\hat{\beta}_jx_{i}} )^2} + \lambda \sum_{i=1}^p \hat{\beta}_i^2$ - generic version with $\beta_0=0$
     - since  $x_{11}=x_{12}$, $x_{21}=x_{22}$, we get $(y_1-\beta_1x_{1}-\beta_2x_{1})^2+(y_2-\beta_1x_{2}-\beta_2x_2)^2+\lambda(\beta_1^2+\beta_2^2)$
     - Since we are minimizing that, we need to take a derivative and set it to 0 (with respect to $\beta_1$ and $\beta_2$)
   - Write out the lasso optimization problem:
     - $(y_1-\beta_1x_{1}-\beta_2x_{1})^2+(y_2-\beta_1x_{2}-\beta_2x_2)^2+\lambda(|\beta_1|+|\beta_2|)$
6. -
7. -

### Chapter 7

1. Cubic regression spline with a knot at $\xi$ can be obtained using a basis of the form $x, x^2,x^3,(x-\xi)^3$ (the last term = $(x-\xi)^3$ if x > $\xi$ and 0 otherwise). Show that $f(x)=\beta_0+\beta_1x+\beta_2x^2+\beta_3x^3+\beta_4(x-\xi)^3_+$ is a cubic regression spline

   - Find a cubic polynomial $f_1(x)=a_1+b_1x+c_1x^2+d_1x^3$ such that $f_1(x)=f(x)$ for all $x \leq \xi$. Express a-d in terms of the beta coefficients:

     - $a_1 = \beta_0, b_1 = \beta_1, c_1 = \beta_2, d_1 = \beta_3$

   - Find a polynomial  $f_2(x)=a_2+b_2x+c_2x^2+d_2x^3$ such that $f_2(x)=f(x)$ for all $x > \xi$. Express a-d in terms of the beta coefficients:

     - $f(x)=\beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 + \beta_4 (x - \xi)^3$ for x > $\xi$

     - We can expand the cubic expression, resulting in $\beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 + \beta_4 (x - \xi)(x^2-2x\xi+\xi^2)$ = $\beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 + \beta_4(x^3-3x^2\xi+3x\xi^2-\xi^3)$ = $\beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 + \beta_4x^3-\beta_43x^2\xi+\beta_43x\xi^2-\beta_4\xi^3$ 

     -  Then, we can rewrite this equation by common coefficients:

       $(\beta_0-\beta_4\xi^3)+(\beta_1+3\beta_4\xi^2)x+(\beta_2-3\beta_4\xi)x^2+(\beta_3-\beta_4)x^3$

     - Therefore, our coefficients will correspond to:
       - $a_2=\beta_0-\beta_4\xi^3$
       - $b_2=\beta_1+3\beta_4\xi^2$
       - $c_2=\beta_2+3\beta_4\xi$
       - $d_2=\beta_3-\beta_4$

2. Suppose that a curve g is computed to smoothly fit a set of n points while minimizing the loss (y - g(x)) and penalty (integrating all m derivatives of g). What does g look like?

   - $\lambda = \infty, m = 0$ - we are minimizing g itself - g is a line at 0 ($g(x)=0$)
   - $\lambda = \infty, m = 1$ - we are minimizing the first derivative - g will be a constant function ($g(x)=c$)
   - $\lambda = \infty, m = 2$ - minimizing the second derivative, g will be a smooth linear function
   - $\lambda = \infty, m = 3$ - g will be a quadratic function
   - $\lambda = 0, m = 3$ - penalty will not play a role, g will overfit

3. -

4. -

5. Consider two curves $g_1$ and $g_2$, defined by minimizing loss + penalty for either the 3rd derivative of g or 4th derivative of g

   - as $\lambda \to \infty$, the function will become less flexible (penalty is most important), and $g_2$ is the higher order polynomial so it will probably have a better training fit (lower RSS), but it could have a worse test fit (depends on the true shape of the data)
   - for $\lambda = 0$, they will probably both overfit and have a very low training RSS and high test RSS

### Chapter 8

1. Plot
2. -
3. Plot
4. Plot
5. Final classification based on majority: Red, based on average (p=0.45): Green
6. To fit a regression tree, we partition our response space into j regions, where for each observation in region j the prediction is the average (we select the regions based on a recursive binary approach, choosing the best split based on RSS or classification error at a particular point). We do this until a stopping criterion is fulfilled (RSS change < threshold, # of terminal nodes). We use pruning to select the best subset of trees as a function of $\alpha$, which we choose using cross-validation (grow regression tree, prune it based on $\alpha$, evaluate MSE on left-out data). 

### Chapter 9

1. Plot

2. Non-linear decision boundaries

   - Plot

   - Plot

   - Blue: (0,0), (2,2), (3,8). Red: (-1,1)

   - The decision boundary is a circle in terms of $X_1$ and $X_2$, but not in terms of quadratics: $(1+X_1)^2+(2-X_2)^2$=

     $(1+2X_1+X_1^2)+(4-4X_2+X_2^2)$=

     $5+2X_1+X_1^2+4X_2+X_2^2$ (linear sum of terms)	 

3. Plot

### Chapter 10

1. K-means clustering

   - Prove that $\frac{1}{|C_k|}\sum_{i,i'\in C_k}\sum_{j=1}^p(x_{ij}-x_{i'j})^2 = 2\sum_{i\in C_k}\sum_{j=1}^p(x_{ij}-\bar{x}_{kj})^2$ 

2. Observations and dissimilarity matrix

   - Plot for hierarchical clustering
   - Plot for dendrogram clustering

   





