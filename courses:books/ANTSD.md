# Analyzing neural time series data

## Electrophysiological methods

- Temporal resolution depends on the rate of acquisition and temporal precision depends on the applied analyses
- Temporal accuracy of EEG is high since electric charges travel instantaneously 
- EEG is sensitive to both radial and tangential sources (maximally sensitive to radial sources)
- MEG is maximally sensitive to tangential sources and has low sensitivity to radial sources

### Time-frequency

- EEG contains rhythmic activity that reflects neural oscillations (fluctuations in excitability of populations of neurons)
- Oscillations are described by frequency, power and phase
  - Frequency - cycles/s
  - Power - amplitude^2 (energy in a frequency band)
  - Phase - position along the sine wave at any diven point (rad or deg)
- Frequency bands (roughly):
  - delta (2-4 Hz)
  - theta (4-8 Hz)
  - alpha (8-12 Hz)
  - beta (15-30 Hz)
  - low gamma (30-80 Hz)
  - high gamma (80-150 Hz)
- Individual differences in peak frequencies have been linked to individual characteristics
- Neural dynamics outside of tasks may reflect general properties of neural architecture or support neural computation
- Spatial autocorrelation - activity at neighboring electrodes is strongly correlated, which limits spatial precision and affects connectivity analyses
  - Spatial filters can be applied to attenuate it

### Physiological basis

#### Signal

- Summation of EPSPs and IPSPs at dendrites of ensembles of neurons that are oriented in parallel
  - EEG - mainly 10-50000 neurons in superficial cortical layers
- Magnetic fields are perpendicular to electric fields
- Dipoles pointing in opposite directions will cancel each other in the EEG signal

#### Oscillations

- Origin:
  - interaction between GABA-ergic interneurons and excitatory pyramidal cells (shifting E-I balance)

### Role in cognition

- Long term potentiation in HC occurs preferentially at specific theta phases
- Timing of action potentials can also depend on the phase of the LFP oscillation
- Phase synchronization allows networks to cooperate and transfer information

### Preprocessing

- Keep track of details of preprocessing for each subject
- There is a tradeoff between signal and noise
- ICA should be run on non-overlapping trials
- Buffer zones on the edge of epochs to avoid artefacts (less stringent for STFFT or multi-taper TF)
- Time-frequency analyses involve temporal smoothing
- Number of trials should be roughly equal

#### Artefacts

- Types: blinks, muscle movements, amplifier artifacts and line noise
- Additionally: cognitive artifacts
- ICA can be used to isolate artifacts or to reduce the dimensions in the data
- Blink and other ocular artefacts can be regressed out
- EMG - bursts of 20-40 Hz activity

## Time-domain analyses

#### ERPs

- Averaging many trials with a time-locked response
- Non-phase-locked activity will be cancelled out
- Topographical variance plots - standard deviation over all electrodes at each point in time

#### Microstates

- EEG 'landscapes' can remain stable for subsecond time period
- Microstates have been linked to cognitive processing
- Can be studied using cartool

## Frequency and time-frequency domain analyses

### The dot product and convolution

- Dot product:
  - Can be interpreted as
    - sum of elements in one vector weighted by elements of another vector
    - or covariance between two vectors
    - or mapping between vectors (product of the magnitudes scaled by the cosine of the angle between them)
- Computed by multiplying each element in one vector by the element in the other vector and sum all the points
  - dot product is zero when the vectors are orthogonal

- Convolution:
  - Computing the dot product repeatedly over time
  - Can be seen as
    - A time series of signal A weighted by signal B that slides along signal A
    - Cross-covariance (the similarity between two vectors over time)
    - A time series of mappings between two vectors
    - A frequency filter
  - Performed by computing the dot product between two vectors, shifting one vector in time, computing the dot product again etc
  - One vector is considered the signal and the other is the kernel
  - $(a*b)_k = \sum_{i=1}^{n}a_ib_{k-i}$
  - k - time point, i - element, k-i flips the kernel backwards
- Cross-covariance (if scaled by the variances - cross-correlation) and convolution are similar (compute the time-varying mapping between vectors), but the kernel is reversed in convolution and in cross-covariance it's unchanged
- In EEG, convolution is used to isolate frequency specific activity and to localize it in time
  - Wavelets (small sine waves) are convolved with EEG data
  - As the wavelet slides through the data, it reveals where and how much the data looks like the wavelet
  - Therefore, by using different frequency wavelets on data, we can obtain TF representations

### The Fourier transform

- The Fourier transform works by computing the dot product between the signal and sine waves of different frequencies
  - $X_f = \sum_{k=1}^nx_ke^{-i2\pi f(k-1)n^{-1}}$
  - The dot product is computed between the complex sine wave and the time series x 
-  The inverse Fourier transform allows us to reconstruct the original data using the frequency domain information
  - Build sine waves of specific frequencies, multiply them by the Fourier coefficients, sum all of them together and divide by the number of waves
  - $x_f = \sum_{k=1}^nX_ke^{i2\pi f(k-1)n^{-1}}$
    - The dot product is computed between the complex sine wave and the Fourier coefficients X
- FT assumed that your data are stationary (meaning that the average, variance and frequency structure don't change over time)
  - Violated in the case of EEG data
  - Nonstationarity smears the peaks 
  - Frequency decomposition methods like wavelet convolution, Hilbert or STFT assume that data is stationary over brief periods of time, which is a valid assumption
- Convolution in the time domain is the same as multiplication in the frequency domain

### Wavelets

- A Morlet wavelet can be created by tapering a sine wave with a Gaussian
- This allows us to obtain temporally localized frequency information
- Creating a Gaussian:
  - $Gauss = ae^{-(t-m)^2/(2s^2)}$
  - a = amplitude
  - m = x-axis offset
  - s = standard deviation defined according to $s = \frac{n}{2\pi f}$ (n = number of cycles)
- Bandpass filtering the data and convolving with a wavelet produce similar results
- Complex Morlet wavelets have a real and an imaginary part

#### Refresher on complex numbers

- $a + ib$
- $i = \sqrt{-1}$
- Polar coordinates: magnitude [$M = \sqrt{(real^2+imag^2)}$] and angle to real axis [$\theta = arctan(imag/real)$]
  - $real = Mcos(\theta)$
  - $imag = Msin(\theta)$

##### Euler's formula:

- Allows us to represent complex numbers as points on a circle
- $Me^{i\theta} = M[cos(\theta)+isin(\theta)]$

#### Constructing wavelets

[...]

### Bandpass filtering and the Hilbert Transform 

[...]

### Short-time FFT

[...]

### Multitapers

[...]

### Other methods

[...]

## Time-frequency power and baseline normalization

- Power decreases at increasing frequencies (1/f)
- Individual differences in raw power are also influenced by skull thickness, anatomy of sulti and cortical surface area + experimental conditions
- Raw power values are also not normally distributed because they cannot be negative
- Normalization methods:
  - dB conversion (relative to baseline, logarithmic ratio)
  - Percentage change (relative to baseline)
  - Z-transform (scaled to standard deviation units relative to baseline)

#### Signal-to-Noise Estimates

- Not possible to directly compute for EEG data, but can be estimated as the ratio of the mean signal to the standard deviation
- $SNR = \frac{\mu}{\sigma}$

### Intertrial Phase Clustering

- EEG series convolved with a complex wavelet can be represented as a vector in the complex polar plane (magnitude and phase angle relative to the real axis)
  - The phase angle shows timing of frequency band specific activity
- Phase values cannot be averaged like voltage or power, since they are circular (e.g. 0.05 and 6.23 radians are close to each other)
- Phase angles can be represented on the circle using Euler's formula $e^{ik}$
- Measure of phase clustering - distribution of phase angles
  - ITPC
- This measure can also be referred to as the phase-locking value, phase coherence etc
- Uniformity of the distribution is measured by computing the average vector and taking its length (individual vectors are of unit length, average vector will be less than 1 - smaller if the individual vectors are further apart)
- $ITPC = |n^{-1}\sum_{r=1}^ne^{ik}|$
  - $n^{-1}$ takes the average
  - $e^{ik}$ represents phase angle k 
  - r = trial
  - in Matlab code: abs(mean(exp(i*k)))
    - k = vector of phase angles at one TF point
- Noise and sampling errors can increase ITPC
- Phase angles are independent of power, but they are harder to estimate at low power

## Spatial Filters

- Function similar to temporal filters, isolating features of data

#### Surface Laplacian

- Spatial bandpass filter that filters out spatially broad features (which can represent volume-conducted potentials)
- Highlights local features and improves topographical localization
  - But also conceals true spatially broad activity
- Basic approximation: for each electroed, subtract the averaged activity of immediately surrounding ones
- Related to the spherical spatial derivative

#### PCA

- The goal is to construct a set of weights (PCs) based on the covariance of a set of correlated variables (electrodes) so that the components explain all of the variance in the data (without correlations between components and with the first one explaining most of the variance and the next ones being orthogonal to each other)
- Identifies patters of large-scale covariance
- Computation:
  - Construct covariance matrix: $cov = (n-1)^{-1}(X-\bar X)(X-\bar X)^T$ (subtract the mean and multiply by transpose to obtain a channels x channels matrix, normalize by n-1)
    - Can be either computed from all time points from all trials concatenated into one matrix, or separately for each trial and then averaged together (better SNR)
  - Perform eigendecomposition or SVD
    - Returns eigenvectors and eigenvalues (axes and magnitudes of the PCA "arrows")
    - The eigenvectors are the PCs (weights) for each electrode that produce the PCA time courses
    - eigenvalues can be scaled to percentage variance accounted for by dividing each EV by the sum of all EV and multiplying by 100
  - Result of EVD/SVD = square matrix of electrodes x electrodes
    - Each column in the EV matrix is the PC and each row has the weights of each electrode
    - The electrode weights can be plotted as topomaps
- Rank of a matrix - number of linearly independent dimensions
  - Subtracting independent components can decrease the rank of the data

#### ICA

- PCA is used to de-correlate and reduce the dimensionality of a multivariate signal, ICA is used to de-mix independent sources
- ICA doesn't assume orthogonality

## Source imaging

- Source-space imaging approaches define sets of weights per electrode such that the weighted sum of all electrodes gives us approximate activity at some physical location in the brain
- Forward solution is a topomap that results from activity of a specific dipole, inverse problem is what dipoles produce a specific topomap
- Can be conceptualized as a regression or GLM:
  - Forward solution is the independent variable, sensor-level data is the dependent variable
  - Set of weights = regression coefficients

#### The inverse problem

- There is no unique solution (many different configurations of brain activity can produce the same map)
- Existing methods involve assumptions and parameter selections

### Methods 

#### Dipole fitting

- Estimating a single point or a small number of points that explain the maximal amount of topographical variance
- Estimate dipole parameters => Determine weights for all electrodes so that the sum of their activity ~ dipole activity
- Disadvantage: rests on the assumption that the dipole that's fitted is the only active source in the brain
  - can be valid for motor/sensory experiments, but usually not for cognitive ones

#### Non-adaptive distributed-source imaging 

- Estimate activity at thousands of fixed dipoles with known locations and orientations and estimated magnitude
  - With 64 sensors, 10000 sources and 3 dipole orientations => 64 x 3 x 10000
  - Sources are voxels in the brain
  - The electrode weights are computed based on the electrode location relative to the brain
- Examples: LORETA, minimum-norm estimators
- Advantages: quick, can be applied to a single time-point of data
- Disadvantages: weights for each electrode are not fine-tuned, number of comparisons (e.g. estimate sources over time and frequency for 10000 voxels and two conditions => 100 mil statistical comparisons)

#### Adaptive distributed-source imaging 

- Compared to non-adaptive methods, weights are computed differently (not just according to physical position, but also according to the data - covariance of interelectrode activities)
  - Covariance matrices can also be computed from cross-spectral densities (frequency-domain analogue of time-domain covariance)
  - Must be based on time windows
- Example: beamforming
- Advantage: weights are adapted to the data, increasing sensitivity
- Disadvatange: number of required parameters
- Book: Adaptive Spatial Filters for Electromagnetic Brain Imaging (Sekihara and Nagarajan 2008)

#### Limits

- Uncertainty in source imaging can result from uncertainties in electrode position, brain anatomy, coreg of MRI data, head movement, conductivity of tissues etc
- MEG is practically superior, but EEG can be just as good with precise data

## Connectivity 

- Most brain connectivity measures are bivariate
  - Easier to implement, interpret, visualize and quantify
- Bivariate correlations can misinterpret relationships if the networks is multivariate 
  - in task-related connectivity - mitigated by condition comparisons
- Important points:
  1. The magnitude of phase lag is usually not taken into consideration, just the consistency across time and trials
  2. Nonzero phase lag does not necessarily imply causal or directed connectivity
     - Also hard to interpret who's first
     - Methods such as GC or PSI provide directed connectivity
     - Proving causal connectivity should be supported with known anatomical connectivity, previous research or causal methods such as TMS
  3. Phase-based and power-based measures reveal different patterns of results
  4. Functional connectivity is different from effective connectivity
  5. Connectivity can be confounded by volume conduction
- Which measure to use?
  - No correct method for any dataset

- Phase-based connectivity metrics
  - Based on the distribution of phase angle differences between two electrodes
  - Have a neurophysiological interpretation
  - However: rely on precise temporal relationships in the same frequency band

- Power-based connectivity metrics
  - Correlation of time-frequency power between two electrodes
- Granger causality
  - Tests whether variance of signal A can be predicted from variance in signal B earlier in time
  - Tests for directed connectivity and can ignore simultaneous connectivity
  - Twice the number of statistical comparisons that need to be controlled for (A -> B and B -> A)
- Mutual information
  - Detecting shared information between two variables
  - Computed using the distributions of values within variables and the joint distribution
  - No clear neurophysiological interpretation
- CFC
  - Coupling of activity in two different frequency bands
  - Neurophysiological theories of information processing based on CGC
- Graph theory
  - Large-scale/multivariate network dynamics
  - High-level summary can be compared between EEG and MRI and other modalities
  - However, these metrics are often used in exploratory data-mining analyses that lack a theoretical framework
  - Important to have a specific hypothesis in mind
- Confound: volume conduction
  - Signal from the same source can be captured by separate electrodes
  - Features:
    - Zero phase lag (however, there's some true zero phase lag connectivity (Chawla 2001, Roelfsema 1997, Viriyopase 2012)
    - Strength of connectivity (VC connectivity will be stronger at neighboring electrodes)
    - Spurious connectivity can only show positive correlations
    - VC-driven connectivity means that changes in power correlate with changes in connectivity
  - Solutions:
    - Spatial filter (such as the surface Laplacian or source imaging filter)
    - Examine only negative correlations
    - Test for temporally lagged connectivity
    - Test for condition differences in connectivity
    - Test for cross-frequency correlation
    - Test for a dissociation between connectivity and power
    - Use measures like iCOH, PLI, wPLI or PSI

### Phase-based connectivity

#### ISPC (intersite phase clustering)

- average of phase angle differences between electrodes over time
- $ISPC_f=|n^{-1}\sum_{t=1}^ne^{i(\phi_{xt}-\phi_{yt})}|$
- $\phi_x$ is the phase angle from electrode x at frequency f at time point n

#### Spectral coherence (magnitude-squared coherence)

- Phase values are weighted by power values
- $Coh_{xy} = |\frac{S_{xy}}{S_{xx}S_{xy}}|$
- $S_{xy}$ is the cross-spectral density between electrodes X and Y 
- $S_{xx}$ and $S_{yy}$ is the autospectral densities of electrodes X and Y
- Using Euler's formula:
  - $C_{xy} = |n^{-1}\sum_{t=1}^n|m_{tx}||m_{ty}|e^{i\phi_{txy}}|^2$
  - $m_x$ and $m_y$ are the magnitudes of analytic signals X and Y
  - $\phi_{xy}$ is the phase angle difference between electrodes X and Y
  - t = either trials or time points
- Spectral coherence is normalized by power

#### Phase lag based measures 

- Spurious connectivity occurs at zero or $\pi$ phase
- Measures: 
  - iCOH - same as spectral coherence, but only the imaginary part is taken before the magnitude
  - PSI - measures directed phase-based connectivity - if the slope of the phase lag is consistent (but measures only the overall asymmetry, so will be zero for strong bidirectional connectivity)
  - PLI - measures the extent to which a distribution of phase angle differences is skewed towards the positive or negative sides of the imaginary axis
    - $PLI_{xy} = |n^{-1}\sum_{t=1}^nsgn(imag(S_{xyt}))|$
    - imag(S) is the imaginary part of cross-spectral density at time point t
  - wPLI - weighs angle difference according to their distance from the real axis (scaled by the magnitude of the imaginary component)
- Connectivity over time is sensitive to high frequency connectivity and resting state data, connectivity over trials has higher temporal precision

### Power-based connectivity

- Correlation coefficient
  - Pearson's: covariance of two variables scaled by the variance of each variable
  - Spearman correlation (non-parametric): data are ordered and ranked, then Pearson's correlation formula is applied

### Granger prediction

#### Univariate autoregression

- $X_t = 0.8*X_{t-1}$ - autoregression of order 1
- $X_t = 0.8*X_{t-1} - 1.3*X_{t-2}$ - autoregression of order 2
- General expression: $X_t = \sum_{n-1}^ka_nX_{t-n}+e_{xt}$
  - a - vector of the autoregression coefficients
  - e - error of the residual that can't be predicted from X

#### Bivariate autoregression

- $X_t = 0.8*X_{t-1} - 0.3*X_{t-2}$
- $Y_t = -0.4*Y_{t-1} - 1.3*X_{t-1}$ - bivariate
- General expression: 
  - $X_t = \sum_{n-1}^ka_nX_{t-n}+\sum_{n-1}^kb_nY_{t-n}+e_{xyt}$
  - $Y_t = \sum_{n-1}^kc_nY_{t-n}+\sum_{n-1}^kd_nX_{t-n}+e_{yxt}$
  - a and b can be different, so the influence of X on Y can be different from the influence of Y on X
- For orders >1, coefficients are vectors
- Measure: compare the variance of the errors in the univariate and bivariate model
- $G = \ln(\frac{var(e_x)}{var(e_{xy})})$
- For EEG analyses, GC is computed in sliding time segments
- Model order can be selected using BIC or AIC (how many terms to go back into the past)
  - can be estimated separately for each time segment

#### Frequency domain GC

- Incorrect approach: bandpass filter the data and apply Granger prediction
- Geweke method: compute dot products between the autoregression coefficients and complex sine waves and apply those results to the error variance

#### Statistics

- Permutation testing
  - useful for frequency domain since the underlying distibution is not known
- Permute the order of time segments within trials

### Mutual information

[...]

### Cross-frequency coupling

[...]

### Graph theory

- Networks can be represented as matrices or as graphs
- First step: all-to-all connectivity matrix
  - Slice of a hypercube with dimensions electrode x electrode x time x frequency x condition
- Connectivity matrices can be thresholded to compute metrics
  - Thresholding value can change with the frequency band
  - Or you can keep the k strongest connections
- Connectivity matrices can also be binarized

#### Degree

- measure of how many connections are at each vertex (e.g. if there's a 'hub')

#### Clustering coefficient

- proportion of electrodes with connections w electrode A that also have connections with each other
- $CC_i = \frac{2\sum_{j=1}^nv_ij}{n_i(n_i-1)}$
- v is 1 if there's connectivity between electrodes i and j
- Clustering coefficient and degree are mathematically and conceptually independent

#### Path length

- Average distance from each vertex to any other vertex in terms of waypoints
- Limited physiological interpretation, since many brain nodes are not measurable with EEG (like the thalamus)

#### Small-world networks

- High clustering and lower path length than expected by chance
- $swn = \frac{C/C_r}{L/L_r}$ - compare network with a random network
  - Erdös-Rényi random graphs
  - Statistical significance can be evaluated by permutation testing - making a random network at every iteration

## Statistics

- Within-subject analyses - cross-trial variability
- Group-level analyses - consistency of the direction of the effect
- p-value thresholds are arbitrary, but 0.05 or 0.01 are common

### Correction for multiple comparisons

- In electrophysiology, a large number of tests is performed
- Common: Bonferroni correction, but it's inappropriate for EEG data since it assumed independency and can be too stringent
- P-values are based on the number of datapoints
  - should be supplemented with a measure of effect size, SNR, odds ratio, sensitivity, ROC etc

### Parametric vs nonparametric

- Difference: assumptions regarding the distribution from which the data is drawn
- Parametric statistics assume a Gaussian distribution
- Non-parametric statistics make no assumptions
  - Permutation tests compute an observed distribution of data points

### Combining data across subjects

- Most often, data are averaged across subjects
  - Even if subjects have different alpha peaks, smoothing from wavelet convolution and spatial smoothing from VC can render them comparable
- Time-frequency windows can be defined individually for each subject

### Non-parametric permutation testing

- Doesn't rely on assumptions about the distribution and easily incorporates corrections for multiple comparisons
- Compute values under the null hypothesis by shuffling values and build a random distribution, compute statistical test values
- Compute a p-value from the test value
- Correct for MC by using pixels or clusters of pixels that are above the threshold

#### Cluster-based

- How to define a cluster?
  - Non-data driven: set amount of ms and Hz
  - Data-driven: 
    - Perform permutation testing
    - Apply threshold to the TF map using 0.05 (precluster threshold) at each iteration
    - This will result in clusters under the null hypothesis 
    - Collect the data from the biggest cluster in the map
    - Remove any clusters that are less that the 95% of the distribution of largest clusters expected under the null hypothesis 

### False discovery rate

- Controls for the probability of type I errors within a distribution of p-values

## Within subject analyses

[...]

## Between subject analyses 

- Avoid circular inferences:
  - e.g. selecting data based on a particular characteristic and then testing for significance
  - 

## Conclusions

- 





















