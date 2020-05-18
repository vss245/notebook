# Cluster‐based permutation tests of MEG/EEG data do not establish significance of effect latency or location

Sassenhagen and Draschkow 2019

### Intro

- MEG and EEG experiments result in high-dimensional outcomes with a spatio-temporal structure
- ERP analysis - average over multiple time points and sensors, use parametric tests of significance (ANOVA or t-tests)
  - however, electrodes and time points cannot be selected contingent on observed data w/o cross-validation (Kilner, 2013) - statistically invalid
  - analysis parameters can be set a priori, but sometimes an exploratory analysis is required
  - sol-n = massively univariate tests => MCP
    - many corrections for multiple comparisons reduce power and reduce the chance of observing a true effect (Button 2013)
- Cluster-based permutation tests allow us to address this problem with good power/FP ratio
  - built on the assumption that effects are clustered along dimensions of interest - time and space
  - true signal will be reflected at multiple adjacent time points and adjacent sensors will show similar patterns
  - no inference is made over individual voxels
    - clusters are identified in the data
    - cluster structure in the observed data is compared to the pattern of null-hypothesis based data
    - therefore, **no statement about onsets and offsets with millisecond precision will be accurate, since the invidivual voxels are not visible to the statistical test**
    - additionally, **the spatial location of the cluster is also invisible at this stage, since the p-values refer only to the size of the clusters**
- **Cluster-based permutation tests do not provide statistical inference for the location of effects**

### How it works

- two components: cluster forming algorithm and the algorithm to create a surrogate null distribution
- example:
  - data in space x time
  - binary condition contrast
  - a test statistic is calculated at each coordinate
  - H0 = in an unobserved population of subjects exposed to the same manipulation the difference would be 0
  - Result: sensor x time t-value map
    - comparing these to the t-distribution yields p-values but the MCP precludes interpretation
  - Voxels are thresholded according to an a priori defined criterion e.g. a certain t-value
  - adjacent voxels with t-scores exceeding this value are grouped together
    - temporal adjacency and sensor neighbourhoods 
    - groups are summarized by a sum of t-values or other methods 
- the extent of clusters (start time, topography, frequency boundaties) is fixed at this stage and depends strongly on the cluster-forming algorithm (e.g. t-value or other score? raised to a power? 0.05 or 0.01? cluster sum or count? etc)

### Inference stage

- thresholding voxels can be interpreted as an inferential stage but this stage is affected by repeated tests
- Second order inference: the cluster structure of the data identified in the first stage is exchangeable between conditions under the null hypothesis
- permutation tests establish the probability of the data under the null hypothesis
  - e.g. condition 1 and 2 would give the same results
  - done by generating all possible assignments of data points to the condition (satisfactory number of permutations >800)
- thus the original high dimensional data is reduced to a single number

### How to use results

- the inferential stage does not "see" the coordinates from the first stage, only the cluster sizes
  - no guarantee of the FP rate on any of the points in the cluster
  - statistical claims regarding condition differences are not justified for any included points
- Reasons:
  - the test did not evaluate if the inclusion or omission of an earlier time point in the cluster would have given a significant result
    - **you can report the extent of the cluster, but no statistical inferences with guaranteed error rates have been made about the specific shape and location**
  - Noise/sample size can affect the cluster location and spatial extent
  - cluster-based methods can also underestimate the latency, spatial or frequency extent

- **MEG effect latencies: Kiesel, Miller, Jolicœur, and Brisson (2008), Luck (2005), Miller, Ulrich, and Schwarz (2009), Piai, Dahlslätt, and Maris (2015), and Rousselet (2012)**

- Clusters can be used as masks but only if they are either established on an independent dataset or using cross-valudation

### How to report results

- Significance of the cluster refers only to the location of its cluster-level statistic in the distribution but not to its location in space, time or frequency

- **It could, however, be justified to say: “A nonparametric cluster‐based permutation analysis indicated an effect of condition (*p* < 0.05). This corresponded to a cluster in the observed data beginning at 180 ms.”**

- **This statement is justified; however, it might not be con- sidered best practice. The categorical distinction between the first and second sentence—one is inferential, the other descriptive—is very easily glossed over.**

  

  