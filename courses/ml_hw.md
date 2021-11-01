### Useful stuff from the homeworks

- The **generalized mean** takes the form $M_p = (\frac{1}{N}\sum_{i=1}^N x_i^p)^{\frac{1}{p}}$
  - minimum: $p = -\infty$
  - harmonic mean: $p=-1$
  - geometric mean: $p = 0$ 
  - arithmetic mean: $p=1$
  - quadratic mean: $p = 2$
  - if $j < k$, then $M_j < M_k$, which can be useful for establishing upper bounds
  - e.g. the Bayes error is $\int \min[P(w_1|x),P(w_2)|x]$ and can be upper bounded with the harmonic mean since $M_{-\infty}<M_{-1}$
- In high-dimensional cases, we can estimate the error by replacing it with the expectation, sampling from the space and taking the mean (since directly computing the error may be too costly).
- 