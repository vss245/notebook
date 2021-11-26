### Formulas and definitions

- The **generalized mean** takes the form $M_p = (\frac{1}{N}\sum_{i=1}^N x_i^p)^{\frac{1}{p}}$
  - min: $p = -\infty$, harmonic: $p=-1$, geometric: $p = 0$, arithmetic: $p=1$, quadratic: $p = 2$, max: $p = \infty$
  - $a < b \rightarrow M_a < M_b$ (e.g. $P\text{(error|x)}=\int \min[P(w_1|x),P(w_2|x)]$ and can be upper bounded with the harmonic mean since $M_{-\infty}<M_{-1}$)
- In **high-dimensional cases**, we can estimate the error by replacing it with the expectation, sampling from the space and taking the mean (since directly computing the error may be too costly).
- **Gaussian distribution:**
  - $p(x|w_j) = \frac{1}{\sigma\sqrt{2\pi}} 
      \exp\left( -\frac{1}{2}\left(\frac{x-\mu_j}{\sigma}\right)^{\!2}\,\right)$
  - $p(x|w_j)=\frac{1}{\sqrt{(2\pi)^d\det\Sigma_j}}\exp(-\frac{1}{2}(x-\mu_j)^T\Sigma^{-1}_j(x-\mu_j))$
- **Bayes' Theorem**: $$P(w_j|x)=\frac{p(x|w_j)\times P(w_j)}{p(x)}$$, or $$\text{posterior}=\frac{\text{likelihood x prior}}{\text{marginal likelihood}}$$
  - to make a decision using BDT, $\arg \max_j \log p(x|w_j)  + \log p(w_j)$ (since $p(x)$ doesn't depend on j)
  - if Gaussian: $$\arg \max_j x^T\Sigma^{-1}\mu_j-\frac{1}{2}\mu_j^T\Sigma^{-1}\mu_j + \log P(w_j)$$
- **Likelihood**: given a dataset $D=(x_1...x_N)$, assume i.i.d. examples, $$p(D|\theta)=L(\theta|D)=\prod_{k=1}^N p(x_k|\theta)$$ (probability of data given parameters is the likelihood of parameters - product of all probabilities for independent events)
  - best parameters are given by $\hat\theta=\arg\max_\theta p(D|\theta)$
- **MLE**: $p(w_j|x)=\frac{p(x|w_j,\hat\theta_j)p(w_j)}{\sum_jp(x|w_j,\hat\theta_j)p(w_j)}$
  - apply log to likelihood (for concavity)
  - take the gradient
  - set it to 0 and compute $\hat\theta$
  - $$\hat\theta=\frac{1}{N}\sum_{k=1}^Nx_k$$ (*MLE estimator is the empirical mean of the data*)
  - calculate $p(w_j|x)$
- **Bayesian classifiers**: $p(w_j|x,D)=\frac{p(x|w_j,D)p(w_j)}{\sum_jp(x|w_j,D)p(w_j)}$
  - get likelihood $p(D|\theta)$ 
  - compute $p(\theta|D)$
  - *the result is a posterior distribution* (these classifiers prefer classes with more data and rely on priors)
- **PCA** is done to reduce dimensions (minimizes noise, maximizes signal)
  - we want to find a unit projection vector w such that $\arg\min_w[\frac{1}{N}\sum_{k=1}^N\norm{x_k-ww^Tx}^2]$ (minimize difference between data and projected data)
  - similarly, we can maximize the variance $\arg\max_w[\frac{1}{N}\sum_{k=1}^N(w^Tx_k-E[w^Tx])^2]$ (in centered data $E[w^Tx]=0$)
- **Lagrange multipliers**: 
  - to find $\arg\max f(\theta)$ subject to $g(\theta)=0$, we construct a Lagrangian $\mathcal{L}(\theta,\lambda)=f(\theta)+\lambda g(\theta)$
  - compute the gradient with respect to $\theta$ and set it to 0
- **PCA solution**: $\hat\Sigma w=\lambda w$ - the eigenvector of the covariance matrix is the principal component
  - this can be done without computing the covariance matrix via **SVD**:
    - SVD factorizes $M = U\Lambda V$, where U = eigenvectors of $MM^T$, V = eigenvectors of $M^TM$, the square roots of the eigenvalues of $MM^T$ are on the diagonal of $\Lambda$
  - iterative power algorithm
    - start with a random unit vector $w^0$ and apply $w^{t+1}=\frac{Sw^t}{\norm{Sw^t}}$
    - always converges
- **Fisher's discriminant analysis**:
  - find a line to project the data onto that maximizes the ratio between between-classes variance and within-classes variance
  - $\arg\max_w \frac{w^TS_Bw}{w^TS_Ww}$
  - $w \propto S_w^{-1}(w_1-w_2)$
- **Model selection**
  - structural risk minimization: structure the space of solutions into nested regions (like polynomials), prefer solution that belongs to a smaller region
  - BIC - penalises the number of parameters
  - $\text{Bias}(\hat\theta)=E[\hat\theta-\theta]$ (expected deviation of the mean)
  - $\text{Var}(\hat\theta)=E[(\hat\theta-E(\hat\theta)^2]$ (scatter around the estimator of the mean)
  - $\text{MSE}(\hat\theta)=E[(\hat\theta-\theta)^2]=\text{Bias}(\hat\theta)^2+\text{Var}(\hat\theta)$ (prediction error)
- MLE has an unbiased estimator, but that's not always good
  - James-Stein estimator: $\hat\mu_{JS}=\hat\mu-\frac{(n-2)\sigma^2}{\hat\mu^2}\hat\mu$ (increases the bias, decreasing the variance)
- High bias, low variance: small range + inaccurate
- High bias, high variance: large range + inaccurate
- Low bias, low variance: small range + accurate
- Low bias, high variance: large range + accurate