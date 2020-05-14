Bastos2016

# A tutorial review of functional connectivity analysis methods and their interpretational pitfalls

## Abstract: 
	- Oscillatory activity may coordinate networks of neurons
	- Rhythmic oscillations can be quantified with many metrics
	- Review metrics and their pitfalls
- Cognitive tasks require a coordinated flow of information
	- Oscillations underlie dynamic coordination
	- Oscillations - synchronized rhythmic excitability
	- Facilitate flow of information
	- Neural information is reflected in action potentials that can be organized in bursts

## Evaluating synchrony
- Invasive vs non-invasive methods
- Experimental vs task-free
- Challenges:
  - At least 42 distincs methods
  - Some methods are based on rigorous theory (GC), others are *ad hoc* (when needed) modifications (PLV)
  - Algorithmic interpretation can be complex
    - Research groups may have their own implementations
    - Interpretation is hard
    
## Taxonomy
- Directed vs non-directed (does it quantify in which direction information flows)
		- Directed measures establish statistical causation (causes=>effects)
		  - GC - causes predict effects
		  - Treat time series as realization of random variables
- Shifting the time series gets us the cross-correlation function which accounts for temporal structure
	- Cross-correlation - effective for dominant unidirectional interaction with a specific time delay
		- Time lag and magnitude are informative
		- Interpretation is harder for bidirectional interaction
- To overcome the non-directedness limitation, other measures are used
	- GC assesses the extent to which past values of one time series are able to predict future values of another series
	- Linear auto-regressive model fit to the data or non-parametric matrix factorization
		- Estimates directed interaction
- Model-free / model-based
	- Model-based - assumption of linearity (e.g. two signals have a linear relationship)
		- Peason's correlation coefficient (MB, ND)
		  - Fraction of the variance of V1 explained by V2
		- Mutual information - no linearity assumption
	- Model-free: developed to detect directed interactions
		- Transfer entropy (causes precede and predict effects; detects non-linear interactions)
- Linear methods are sufficient for most interactions
	- E.g. we want to know if oscillations at similar frequencies in A and B couple with a phase difference => PLV or coherence
	- Non-linear coupling (e.g. cross-frequency, $f2 \ne f2$) => other metrics like PLI
	- *Choice of method should be guided by the underlying hypothesis*

## Measures:
### Phase synchrony 
- computed from frequency domain representation of two signals across time windows for a set of frequency bins <= phase and amplitude estimate
- $Ae^{i\phi}$ or $x + iy$ (complex valued numbers)
  - $i$ is the imaginary number
  - $\phi$ - angle (argument)
  - A - magnitude of vector 
  - Cross spectrum between signal 1 and 2 (S1 and S2)
    - $ S1*conj(S2) = A_1e^{i\phi}*A_2e^{i-\phi}=A_1A_2e^{\phi_1-\phi_2} $
    - get complex number (vector in 2D space), magnitude is $A_1*A_2$​, angle = phase difference

### Cross spectrum - correlation between two signals in the frequency domain
  - If there's consistent differences in phase, weighted sum of the CSD will be non-zero, whereas if the phase differences are inconsistent, it will be 0
  - Real data will probably be between 0 and 1
- Coherence coefficient:
  - $coh_{xy}(\omega)=\frac{|\frac{1}{n}\sum_{k=1}^{n}A_x(\omega,k)A_y(\omega,k)e^{i(\phi_x(\omega,k)-\phi_y(\omega,k))}|}{\sqrt{(\frac{1}{n}\sum_{k=1}^{n}A^2_x(\omega,k))(\frac{1}{n}\sum_{k=1}^{n}A^2_y(\omega,k))}}$
  - $\omega$ = frequency    
  - x and y - signals 
  - numerator = length of the vector average of the cross-spectrum for $A_x$ and $A_y$ for frequency $\omega$ and trial k
  - denominator = square root of average squared $A_x$ and $A_y$
  - matrix representation:
  - $S(\omega)=\begin{bmatrix}S_{xx}(\omega) & S_{xy}(\omega)\\S_{yx}(\omega) & S_{yy}(\omega)\end{bmatrix}$
  - where $S_{xx}(\omega)$ is the power estimate of signal x and $S_{xy}(\omega)$ is the averaged cross-spectral density
  - then, coherence becomes:
  - $coh_{xy}(\omega)=\frac{|S_{xy}(\omega)|}{\sqrt{S_{xx}(\omega)S_{yy}(\omega)}}$
    - length of the vector average of the cross spectrum / square root of power estimates of signals X and Y

### Coherency
- Remove ||, get complex value
  - Phase difference angle is now interpretable as a time delay
  - Under real circumstances - can't really assign directionality
  - Fixed time delay - phase difference will be a function of frequency
  - For example, if there's a time lag of 10 ms and a rhythmic process that exists between 8 and 12 Hz:
    - at 8 Hz, 10 ms is 10/125 of the cycle
    - at 12 Hz, 10 ms is 10/83.3

### Phase Slope Index
  - Generic quantity to infer unidirectional interactions
  - Computed from coherency, quantifies the consistency of the direction of the change in the phase difference

### Imaginary part of Coherency
- Contributions along the real axis - instantaneous interactions due to field spread (volume conduction)

### Phase Locking Value
- Apply formula for coherence to FT signals
- Vector average of the relative phase across obsevations
- $plv_{xy}(\omega) =|\frac{1}{n}\sum_{k=1}^{n}e^{i(\phi_x(\omega,k)-\phi_y(\omega,k))}|$
- length of the vector average of a set of phase difference estimates

### Other measures:
- PLI - distribution of phase differences across observations
  - Averaging the sign of the phase difference per observation
  - Non-zero phase differences cannot be caused by volume conduction
    - Also: wPLI, dbwPLI
- PPC - pairwise phase consistency:
  - Distribution of phase differences across observations will be clustered around an avg value if there's true synchronization
  - Not biased by sample size
- More than pairwise:
  - Graph theoretic approaches

### Problem: common input

- How to correctly infer a direct interaction when there's possible unobserved sources
- Information from observed sources can be used to remove indirect sources

## Granger causality

- previously discussed metrics only useful if there's a time-lagged and unidirectional interaction
- GC and others can quantify bidirectional interactions
  - directed influence of x on y and y on x
- $GC_{x\rightarrow y}(\omega)=ln(\frac{S_{yy}(\omega)}{{S_{yy}(\omega)-(\sum_{xx}-\frac{\sum_{yx}^2}{\sum_yy})|H_{yx}(\omega)|^2}})$
- here, $H(\omega)$ is the spectral transfer matrix 
- $\sum$ is the residuals of the autoregressive model
- $H(\omega)\sum H(\omega)^*=S(\omega)$
- S - cross-spectral density matrix
- covariance matrix of the residuals between the spectral transfer matrix = getcross-spectral density
- $GC_{x, y}(\omega)=GC_{x\rightarrow y}(\omega)+GC_{y\rightarrow x}(\omega)+GC_{x \cdot y}(\omega)$
  - last term - instantaneous causality (total interdependence that cannot be accounted for by phase-shifted interactions)
- GC can be calculated non-parametrically (e.g. with Fourier/wavelet methods)

### Bivariate vs multivariate

- Multivariate - all channels
  - all information is taken into account
- Bivariate - pairs of channels
  - more stable results
- Multivariate approach => spectral transfer matrix
  - can be used to compute the directed transfer function (DTF) and partial directed coherence (PDC) - connectivity metrics

## Common problems

- MEG/EEG/LFP recordings reflect a mixture of a signal of interest and noise
- observed vs unobserved input contributions

### Common reference problem

- spurios functional connectivity can result from a common reference channel
  - fluctuations in potential at the reference locaiton will be reflected in both (zero time lag)

### Volume conduction/field spread

- Currents flowing in tissues around active neuronal sources
  - More colloquially, spread of electromagnetic fields
- can create artifactual coherence
- however, the effects are instantaneous - e.g. phase at two sensors will be the same or have a 180 degree difference in the case of opposite poles
- more problematic in non-invasive measurements
  - large distance between sensors and sources
  - spatial blurring because of the skull
  - => single underlying source will be seen at several sensors
- Strategies:
  - unmixing (source reconstruction)
  - experimental contrasts (volume conduction active in both conditions)
  - use connectivity measures that discard interactions at 0 and 180
- MATLAB simulations
- linear mixing of source signals due to spread => SNR differences between channels, inaccurate spectral transfer matrices, noise covariance

### SNR Problem

- Disentangling true signal and noise
- Affects Granger causality - can lead to an asymmetric relationship because noise weakens predictive power
  - weak asymmetry
- Strong asymmetry - true time lagged relationships
  - solution - time-reversal of the signals
  - flips the dominant direction only in the case of true synchronization (e.g. will be unchanged for SNR-affected synchronization)
- Can also be addressed at the experimental level
  - control for impedances of electrodes
  - Analytic approaches: DCM

### Unobserved common input

- Direct vs. indirect interactions
- Imaginary part of coherence - if close to 0, then synchronization is entirely due to zero-lag input (common input)
- Granger causality
  - But: real-data doesn't always have equal coupling strength, same time delay and equal SNR, so can reflect spurious connectivity as well

### Unbalanced data 

- Small sample size - large bias

  - different number of observations - overestimated connectivity in the condition with a smaller sample size

- In non-parametric spectral estimation techniques: vector summation operation, normalized by total # of trials

  - to estimate bias: rearragne data segments (temporal alignment between channels)

- other approaches:

  - randomly delete trials in a higher n condition to equate the number
    - best - bootstrap
  - non-parametric statistical test
  - use unbiased metric like PPC

  