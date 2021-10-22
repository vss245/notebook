## Data analysis: A Bayesian tutorial

### The basics

- Deductive logic: from cause to possible effects (if we are told a fair coin is going to be flipped, we can calculate the chances for different outcomes)

- Inductive logic: given that an outcome has been observed, what are the underlying causes?

  - We can try to make the best inference based on the data and any prior knowledge that we have available, revising our decision if there is new information

- Richard Cox: rules for logical reasoning

  - We should rank our beliefs in a transitive manner: e.g. if we have a), b) and c) and we believe a) more than b), we should also believe a) more than c) - therefore, we rank them according to how much we believe in them
  - If we assign numbers to this belief, if we specify how much we believe something is true, we also *implicitly* state how much we believe it's false, e.g.:
    - $p(x) + p(1-x) = 1$ or $p(X|I) + p(\bar{X}|I)=1$, where I denotes background information and bar denotes X is false - **sum rule**
  - If we specify how much we believe that Y is true and state how much we believe that X is true given that Y is true, we also implicitly state how much they are both true:
    - $p(X,Y|I)=p(X|Y,I)*p(Y|I)$ - **product rule**

- The two useful theorems that can be derived from these rules are Bayes' theorem and marginalization:

  - **Bayes theorem**: $p(X|Y,I)=\frac{p(Y|X,I)p(X|I)}{p(Y|I)}$

    - Follows from the product rule with X and Y exchanged

    - To relate this to data analysis, we can write it as 

      $p(hypothesis|data,I) \propto p(data|hypothesis,I)*p(hypothesis,I)$

      ​	**posterior**								**likelihood**							**prior**	

    - Our quantity of interest is the probability that the hypothesis is true given the data

    - The denominator aka the overall probability of data does not depend on the parameters and can be removed for parameter estimation problems, but will be important for model selection (also called evidence)

  - **Marginalization**:

    - $p(X|I) = \int p(X,Y|I)dY$
    - Y stands for a proposition, so why is there an integral? 
    - Marginalization equation for propositions:
      - $p(X|I)=p(X,Y|I)+p(X,\bar{Y}|I)$ (e.g. probability of X is the sum of probabilities of X and Y and X and not Y)
    - But, instead of a single proposition Y (true or false), we can have a set of alternative possibilities ($Y_1, Y_2...Y_m=\{Y_k\}$ - mutually exclusive and exhaustive)
    - Then, $p(X|I)=\sum_{k=1}^Mp(X,Y_k|I)$
    - Then, if we go to the limit of the number of propositions and M => inf, we get an integral
      - In this case, $p(X,Y|I)$ will be a *probability density function*
    - Marginalization allows us to deal with parameters that have no direct relationship to our experiment (e.g. background noise, instrumental parameters)

  - Historical aside: the notion of probability as a degree of belief or plausibility was rejected by most statisticians and probability was redefined as the long-run relative frequency with which an event occured over infinite trials - it seems like a more objective definition, but it has limited validity

    - The concept of randomness in frequentist statistics is no better defined than the concept of uncertainty in Bayesian statistics
    - Conditional probabilities represent logical connections rather than causal ones (represents a state of knowledge rather tha a physical entity)
      - If we have a bag with 5 red balls and 7 green ones, the probabilities are 5/12 and 7/12, respectively
      - If we draw a red ball on the first draw, the probability of the second draw will change
      - If we are not given the result of the first draw, does the probability of the first draw change with knowledge of the second? It might seem to be unrelated, but if we have an extreme case, such as only two balls, then it does
    - Prior belief may be a contentuous concept, but objectivity only needs that two people with the same background information assign the same probability (and this conditioning on previous information must be explicit)

### Parameter estimation I

-  Most simple case - estimating a single parameter
- Is a coin from Vegas fair if you have 4 heads in 11 flips?
  - Fair: 50-50 outcome
  - If fair, how sure are we? If unfair, how unfair?
  - We can consider a range of hypotheses about the bias-weighting
  - H - bias weighting, H = 0 or H = 1 is all tails or all heads
  - There's a continuum of hypotheses between these
  - We can assign a probability to these propositions, and if only some closely grouped ones have a high probability, then the degree of uncertainty would be low
  - Conditional probability density function: $p(H|\{data\},I)$ (or, more accurately, $p(H|\{data\},I)dH$, because H is a continuum and dH gives us an infinitesimally narrow slice)
  - We need to use Bayes' theorem to relate this to other quantities that will be easier to calculate:
    - $p(H|\{data\},I) \propto p(\{data\}|H,I)*p(H|I)$
    - Since we assume that this might be a weird casino coin, we would be better off with a uniform rather than normal distribution for the probabilities, so p(H|I) = 1 on the interval 0 < H < 1
    - Since we have two independent outcomes (heads and tails), we can represent the likelihood of the data with a binomial distribution $p(\{data\}|H,I) \propto H^R(1-H)^{N-R}$, where R represents the heads and N represents all of the tosses
    - The product of the two distributions will yield the posterior probability density function
  - Does the prior change the result? We can try a fair prior (around 0.5) or a heavily biased for both (peaks at 0 and 1)
    - The pdfs converge to the result (the normal prior is a bit slower because it encodes some information already)
    - With sufficient data, the prior does not have a very large influence
- We could analyze the data collectively as a whole or we can do it sequentially, replacing the prior for the subsequent analyses with the posterior from the last
  - They will give the same answer
  - However, it would not be correct to use the posterior as the prior for a re-analysis of the same data - the resulting accuracy will be extremely overstated
- How do we summarize the posterior pdf?
  - If the quantity of interest is X, the posterior pdf is $P = p(X|\{data\},I)$, then the best value is given by $\frac{dP}{dX} = 0$ (and strictly speaking, $\frac{d^2P}{dX^2} < 0$ to make sure it's a minimum)
  - To get a measure of reliability, we look at the width of the posterior pdf around Xo, the best value
    - Taylor series expansions are helpful - approximating a function by a low order polynomial
    - It's also easier to work with logarithms, since they vary slower
      - $L = ln[p(X|data,I)]$
      - Expanding L near X = Xo, we get
      - $L = L(X_o) + \frac{1}{2} \frac{d^L}{dX^2}|_{X_o} (X-X_o)^2+...$ with the condition that the derivative at Xo is equal to 0
      - The first term is constant, the linear term is missing (because we are looking at the maximum) so the quadratic term $(X-X_o)^2$ determines the width of the posterior, with the width inversely related to the square root of the second derivative (multiplies the quadratic term)
  - If we do this for the coin example, we find that the best estimate is given by the relative frequency of outcomes of heads
    - The error bar is given by $\sqrt{\frac{H_o(1-H_o)}{N}}$
- The concept of the error bar is connected to the idea of symmetry
  - In asymmetric pdfs, we can have a confidence interval (usually 95% - chosen arbitrarily, we can have any other interval)
    - For skewed distributions, the maximum will be the most likely value but the mean (or expectation) could be more representative
  - We can also have multimodal posterior pdfs, sometimes even with several maxima of comparable magnitude
    - Sometimes the posterior pdf won't be easily summarized in a couple numbers
- Gaussian noise and averages
  - Estimating the mean of a Gaussian process
  - The normal distribution is often used as a model of noise associated with experimental data
    - $p(\{x_k\}|\mu,\sigma)=\frac{1}{\sigma\sqrt(2\pi)}\exp[-\frac{(x_k-\mu)^2}{2\sigma^2}]$
    - What is the best estimate of the mean and the confidence of this estimate?
      - It's expressed by the posterior $p(\mu|\{x_k\},\sigma,I)$
      - If we assume independence in the data, the likelihood function is the product of probabilities of obtaining the individual data
      - Since we will know nothing about the mean from the width, we can assign a uniform pdf for the prior
        - so $p(\mu|I)=A$ on the interval between the min and max of mu, where A is $1/\mu_{max}-\mu_{min}$
      - If we multiply the prior by the likelihood, we get $L = ln(p(\mu|x_k,\sigma,I))=constant - \sum_{k=1}^N \frac{(x_k-\mu)^2}{2\sigma^2}$ (logarithm of the Gaussian posterior)
        - We differentiate it and set the derivative to 0: $\sum_{k=1}^N \frac{x_k-\mu}{\sigma^2}=0$
          - Sigma can be taken outside and the equation can be rearranged to $\sum x_k=\sum \mu_o = N\mu_o$
          - Or $\mu_o=1/N\sum x_k$
      - The confidence will be indicated by $\sigma/\sqrt{N}$, which is the inverse square root of the second derivative of L (log of posterior)
  - We can also have different error bars for data - for example, with different laboratories or equipment
    - The computation will be the same, but the formulas will be a bit more complicated since we will have a separate $\sigma_k$
- The lighthouse problem - if there is a lighthouse somewhere on the coast at position $\alpha$ and distance $\beta$ at sea and we record some flashes at a different position (no angle data $\theta$) - where is the lighthouse?
  - Prior - uniform = $p(\theta_k|\alpha,\beta)=1/\pi$
  - How does the angle relate to x?
    - $\beta\tan\theta_k=x_k-\alpha$
  - We can use this to rewrite the prior for the angle in terms of the position of the flash
    - $p(x_k|\alpha,\beta)=\frac{\beta}{\pi[\beta^2+(x_k-\alpha)^2]}$ - Cauchy distribution formula
  - We assume that the distance to sea is known, to reduce the unknown parameter to alpha 
    - Our inference about alpha is the posterior pdf $p(\alpha|x_k,\beta)\propto p(x_k|\alpha,\beta)*p(\alpha|\beta)$
      - Since knowledge of the distance doesn't tell us anything about alpha, the prior is uniform (A = 1/range)
      - Since the flashes are independent, the likelihood is the product of the probabilities, same as in the previous explanation
      - Logarithm of the posterior $L = ln[p(\alpha|x_k,\beta)]=constant - \sum ln[\beta^2+(x_k-\alpha)^2]$ 
      - The best estimate will be at $dL/d\alpha = 0$, but it's hard to express $\alpha_o$ in terms of x and $\beta$
        - We can solve this numerically - evaluate L for different alpha, the largest L will be the best estimate
- The central limit theorem
  - For a Gaussian pdf, the best estimate of $\mu$ is the mean of samples
  - For a Cauchy pdf, the sample mean is not the best estimator
    - For this distribution, the variance is infinite and the mean is undefined

### Parameter estimation II

- Estimating several parameters
- Amplitude of the signal in the presence of background noise
  - We assume that we have a flat background of unknown magnitude B and the signal of interest is a peak with amplitude A of known shape and position
  - We have a set of counts of this measurement at settings x along the x axis, how do we estimate the amplitude of the signal peak and the background?
  - We expect the number of counts in the kth data channel to be proportional to the sum of the signal and the background at $x_k$ - peak of the Gaussian would be expressed by $D_k = n_o[A\exp(-(x_k-x_o)^2/2w^2)+B]$, where n is the constant related to the time of the measuremebts
  - A good distribution for this kind of data is the Poisson distribution $p(N|D)=\frac{D^Ne^{-D}}{N!}$ , which is the likelihood of the data N and the formal expectation value for it is D
  - Likelihood - product of the probabilities of the individual measurements (because the counts are independent)
  - Inference abpout the amplitude of the signal and the background is in the posterior pdf ($p(A,B|N,I)$)
    - $p(A,B|N) \propto p(N|A,B)*p(A,B)$
  - Prior pdf - we encode this in a naïve way - uniform constant for A and B >= 0
  - More measurements - more "peaked" estimate (in this case, a joint distribution for A and B)
  - Often, we would like to get only one of the probabilities, so we follow the marginalization rule:
    - $p(A|N,I)=\int_0^\infty p(A,B|N,I)dB$
    - the marginal distribution is *not* the same as the conditional probability $p(A|B,N,I)$
  - For this analysis, we assume that the shape and position of the signal are known (w and x (width and position of the peak) are in I)
    - If this is not the case, we can integrate out the relevant variables
      - $p(A,B|N,I)=\int \int p(A,B,w,x|N,I)dw dx$
    - Or we can calculate the same metrics for the 4 parameters, but it's more complicated
  - Binning the data is also important - there's a trade-off between accuracy and computability
- Reliabilities
  - We would like to summarize our multi-dimensional posterior pdf using a best estimate and a measure of its reliability
  - Probability density is an estimate of how much we believe these measurements lie in the neighborhood of those values, so the optimal estimate is the maximum of the posterior pdf
    - If we are interested in X with a posterior of $P=p(X|data,I)$, then the best values are given by the set of equations:
      - $\frac{\part P}{\part X_i}|{X_{oj}}=0$
      - We set the partial derivative of the posterior distribution with respect to the variable of interest to 0 (technically, we would also need a test to ensure that it's a minimum and not a maximum)
  - It might still be easier to work with L and not the posterior pdf
    - $L = ln[p(X|data,I)]$
    - If we have two variables X and Y, we would need to solve two equations
      - $\frac{\part L}{\part X}|_{X_oY_o}=0$ and $\frac{\part L}{\part Y}|_{X_oY_o}=0$ 
      - The measure of the reliability can be obtained by looking at the spread of the posterior around the optimal point
        - We can also look at the Taylor series expansion and derive equations for sigma

 