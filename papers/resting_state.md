### Brain activity is not only for thinking (Laumann & Snyder 2019)

- BOLD fMRI is the dominant tool for brain activity
- brains exhibit constant fluctuations in activity not related to the task at hand
- RSFC is based on this spontaneous brain activity
- Views:
  - RSFC is associated with unconstrained cognitive processes (retrospection, prospection, environmental monitoring, planning)
    - changes in FC between rest and tasks have been interpreted as indicators of cognition
    - Problems:
      - SWS and anesthesia don't significantly change RSFC structure
      - RSFC structure is largely consistent across subjects at the population level and even across mammalian species
      - the metabolic activity of the brain is minimally affected by task performance
  - RSFC is associated with learning and memory
    - homeostatic and consolidative signalling
- learning machine theory:
  - David Marr - learning organisms alternate between a learning phase and a restorative phase (e.g. wake and sleep)
  - activity dependent synaptic plasticity plays a role in learning
  - this plasticity is substantiated by LTP or LTD
  - but unconstrained Hebbian plasticity will lead to either constant activation or constant inactivation
  - Brains need homeostatic plasticity which adjusts synaptic strength in the opposite direction (restoring to prior set points)
  - these homeostatic mechanisms can operate at multiple levels and time scales
- electrophysiology
  - consolidation takes place after events and responses
  - off-line processing: consolidation of episodic memory through place cell replay and SWR in the HC + procedural memory
  - perception, action etc are carried out online
  - thesis: off-line and on-line processing is parallel to the learning and restoration phases proposed by Marr
  - similar distinction: internally vs externally oriented states
  - some of the ongoing brain activity can be understood via this fluctuation
  - on-line activity suppresses off-line activity locally
- Functional connectivity changes are observed in the contexst of multiple training paradigms (across days or weeks)

### Resting state connectivity biomarkers of depression subtypes (Drysdale 2017)

- Intro:
  - Depression is a heterogeneous syndrome, which has several hundred variations of changes in mood, sleep, energy etc
  - Therefore, there might be multiple forms of depression, but their neurobiological basis is unknown
  - Most previous studies identify clusters of symptoms and test for correlates of those, but the relationship between subtypes and substrates is variable across individuals
  - Another alternative is to cluster patients by shared brain activity features 
    - rsMRI is a useful modality for this
    - depression is associated with abnormal functional connectivity in frontostriatal and limbic networks
  - Developed a method for defining depression subtypes by clustering subjects according to whole brain patterns of abnormal FC
- Methods:
  - Data
    - Dataset 1: n = 711 (333 patients and 378 controls), cluster discovery performed on n = 220 (out of 333)
      - Patients had to match DSM depression criteria for a currently active episode (failure to respond to treatment with 2 medications)
      - Classifier training, CV and optimisation were performed on the full dataset 1
    - Dataset 2: n = 477 (125 patients and 352 controls), used for validation of classifier
    - Classifiers were also tested on patients meeting the diagnostic criteria for generalized anxiety disorder and schizophrenia
    - MRI data obtained from several different sites and from several online open repositories of data
  - Preprocessing
    - Template alignment, motion correction etc
    - Additional checks for whether clustering and classification results were biased by motion
    - Parcellation:
      - Functional parcellation: 258 nodes (264 original nodes + 13 depression related nodes -19 nodes with incomplete coverage)
      - Other parcellations: Desikan Killiany (68 cortical + 22 subcortical ROIs), another functional parcellation (Shirer, Greicus et al).
    - BOLD extracted from each ROI by averaging across all voxels in an ROI
    - Multiple linear regression to control for site- and age-related effects (regress the Fisher z-transformed correlation coefficients for each element on ages and dummy variables for sites)
      - Result 258 x 258 connectivity matrices
  - Analysis
    - Cluster discovery analysis was restricted to a subset
    - To get a low-dimensional representation:
      - Use Spearman's rank correlation to find statistically significant features that correlate with severity scores
      - Use canonical correlation analysis to find linear combinations of these features that were correlated with linear combinations of symptoms
      - Identified two linear combinations of features that were correlated with distinct symptoms combinations (anhedonia related and anxiety related)
    - Clustering:
      - Tried k-means or hierarchical clustering
      - Clusters defined by maximizing the ratio of between cluster variance to within cluster variance
      - Wilcoxon rank-sum test to identify features that are significantly different in patients
      - ANOVA - connectivity features that differ most between clusters
  - Classification:
    - Classifiers:
      - logistic regression, LDA, SVM

