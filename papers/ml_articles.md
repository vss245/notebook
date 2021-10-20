# ML articles

### How to avoid machine learning pitfalls (Lones 2021)

- take the time to understand the data
  - read explainatory papers, understand the features, do exploratory data analysis (Cox 2017)
- but don't look at data from the point of view of making assumptions - e.g. don't look at test data or examine patterns
- survey the literature
- think about how the model will be deployed
- have test data to measure the model's performance
- try out a range of models, but only the ones appropriate for your type of data
- optimize hyperparameters - but not manually, with a strategy
- evaluate models multiple times to remove instability - e.g. cross-validation
- don't assume higher accuracy means a better model - could be due to data, different hyperparameter optimisation 
- statistical tests when comparing models - student's t-test or mann-whitney's u-test (doesn't assume a normal distribution)
- correct for multiple comparisons
- be careful when reporting statistical significance 

### Model evaluation, model selection and algorithm selection (Raschka 2020)

- Terms
  - statistical bias - difference between the expected value and the true value of a parameter
  - variance - statistical variance of an estimator (measure of the variability of a model's predictions)
  - holdout method - split into training and testing set
  - Stratification - making sure classes are represented equally in subsets of data
- ![image-20210809132329461](/Users/work/Library/Application Support/typora-user-images/image-20210809132329461.png)
  - holdout validation - randomly divide the data into two subsets, pick an appropriate learning algorithm, fix hyperparameters (not learned from the model fitting, unlike the actual model parameters), use the model on the test set, compare the predicted to "ground truth"
  - capacity of a model - whether additional data is useful or not
  - pessimistic bias - if the model is not at capacity (e.g. could improve), the performance metrics will be pessimistically biased
  - confidence interval - can be computed via normal approximation (since point estimates of performance can be volatile). assume the predictions follow a normal distribution
  - ![image-20210809133549901](/Users/work/Library/Application Support/typora-user-images/image-20210809133549901.png)



- resampling

  - repeated hold-out validation can provide us with a better estimate of a model's performance
  - bootstrapping is a way of fortifying the model with data when you do not have actual independent real life data

- hyperparameters and model selection
  - hyperparameters - parameters of the learning algorithm itself (specified a priori) - e.g. k and distance metric in k-nearest neighbors
  - parameters of the model - some models are non-parametric, so they do not assume that the data follows a certain probability distribution (with the exception of Bayesian non-parametric methods)
  - hyperparameter oprimization is a meta task
  - if we reuse the testing set for tuning the hyperparameters, we will leak test set info into the model learning
  - we need to have an independent validation set for hyperparameter tuning

- k-fold cross-validation

  - iterate over the data set k-times, splitting one chunk for testing and the rest for training

  

