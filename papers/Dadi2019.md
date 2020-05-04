# Benchmarking functional connectome-based predictive models for resting-state fMRI

https://sci-hub.tw/10.1016/j.neuroimage.2019.02.062

- There is a lot of variability in pipelines used to derive biomarkers from resting state MRI data: need for systematic benchmarking and best practice guidelines
- Functional connectome: network structure of the brain, weights are used to characterize paramteres such as behavior, cognition and mental health
- Steps in deriving the connectome:
  - obtain rs data
  - define ROIs
  - parametrize connectivity
  - run ML models
- Method variations create researcher degrees of freedom that compromise measuring accuracy

### Questions asked:

- how to choose nodes: pre-defined atlases, data-driven approaches? how many nodes are necessary? should nodes be ROIs or brain networks?
- how should weights be represented - correlations, pcorr, covariances?
- what classifiers to use - linear, non-linear, sparse, non-sparse? feature selection?

### Current practices:

- ROI definition:
  - spheres of 5-10 mm centered on previously established coordinates
  - regions from anatomical atlases like AAL/DK or connectivity based cortical landmarks
  - Data-driven approaches such as k-means or Ward clustering, ICA approaches or dictionary learning
  - Typical number of nodes: ~100 (12-200)
  - Hypothesis
-  Connectome representation:
  - functional interactions based on second order statistics: signal covariance
  - pearson's correlation or pcorr using the max likelihood formula for the covariance
- Classifiers
  - many different methods
  - also, network metrics such as modularity or centrality
    - network metrics are good at capturing global aspects of connectivity but aren't great at connections in specific subnetworks

### ROI definition

- definition should capture the relevant functional units 
- standard atlases: 
  - Automated anatomical labeling atlas - structural atlas, 116 ROIs from anatomy
  - Harvard Oxford atlas - probabilistic atlas of anatomical structures, 48 cortical and 11 subcortical ROIs in each hemisphere (118 total)
  - Bootstrap analysis of stable clusters (functional atlas built with clustering), varying number of ROIs
  - Power - coordinate based atlas, 264 ROIs
- data-driven methods:
  - k-means (Hastie, 2009)
  - Wards - hierarchical clustering (Michel 2012)
  - Canonical independent component analysis (Varoquaux 2010)
  - Dictionary learning (Mensch 2016)
- selection in data-driven atlases:
  - num ROIs from 40 to 300
  - learn ROIs on the training set, cross-validation loop
- nodes
  - either local regions of the brain or distributed functional networks
  - test both:
    - Random-Walker extraction of regions obtained by CanICA and dictionary learning (Abraham 2014)
    - for k-means and BASC, break up clusters into components

### Connectivity parametrization

- full correlation, partial correlation and the tangent space of covariance matrices
- functional connectome is vectorized using the lower triangular part
- predicting a binary phenotypic status from connectivity features 
  - Non-linear: K-NN, Gaussian Naive Bayes, Random Forests
  - Linear: sparse l_1 regularized SVM, LogReg
  - Non-sparse linear: l_2 regularization with ridge classification, SVM and logreg

### Benchmarking

- using the functional connectome classification pipeline on five open datasets
  - COBRE - schizo vs NC
  - ADNI - MCI vs AD
  - ADNIDOD - PTSD vs NC
  - ACPI - Drug use
  - ABIDE - ASD vs NC
  - HCP - IQ
- standard preprocessing, exclude based on visual inspection and classification group overlap
- Cross-validation, 100-folds, 75% for training and 25% for testing
  - stratified folds, preserving the ratio of samples (so that each class is equally represented in every iteration)
  - measure AUROC for each split

### Results 

- Assessment: either consider the impact of one step when the others are close to optimal, or consider depending on all other steps

- Classifier: non-sparse l2 regularized linear classifiers perform better (conditional on a good choice for the other steps of the pipeline)

- Connectivity parametrization: tangent-space parametrization outperforms the others

- ROI: dictionary learning and ICA perform best, also the BASC atlas

  - deriving regions from functional data performs best, with linear decomposition methods
  - dimensionality choice and node definition is less clear but also less important

  

