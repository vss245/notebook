## EEG/MEG articles

### Multi-Dimensional Dynamics of Human Electromagnetic Brain Activity (Kida et al, 2016)

- MEG and EEG provide information in space, time, and frequency
  - also activity magnitude, connectivity
- brain regions have billions of connections that affect overal population level dynamics

EEG/MEG basics

- cerebral cortex - 2-4mm, 5-6 layers
- pyramidal neurons aligned in the same direction => common activation leads to detectable magnetic fields
  - primary current due to movement of ions
  - volume current - passive ohmic current
- radial current sources and volume currents do not produce magnetic fields
- MEG - cortical sulci, less from cortical gyri (because no cortices are oriented exactly perpendicularly)
- EEG - volume currents from radial and tangential sources
- temporal resolution - millisecond scale
  - both on the scale of underlying activity and measuring devices
- Wide range of frequencies - near DC to 100 Hz and above
  - by transforming time-dimensional data to frequency dimensional data with Fourier or wavelet analyses (TF representations)
  - possible to extend TFR to space as well
- Signals are recorded from sensors or electrodes and are estimated using different techniques with constraints
  - ECD - activity is assumed to be focal and explained by a small number of current dipoles
  - minimum L2 norm - distributed method, divides the source space into a grid with a large number of dipoles, estimate the current in all locations at each time point with minimum power (L2 norm)
  - beamforming - distributed method, spatial filter to pass brain activity from a specified location and attenuate activity from other locations
  - LORETA and variants - distributed method, estimate with zero errors using sparce source configurations (low resolution)
- Time- and frequency-domain beamforming implementations exist:
  - LCMV, DICS
- Parcellations
  - can be performed based on anatomical atlases like Talaraich, AAL, Harvard-Oxford atlases
  - or based on functional parcellations (Power et al 2011, Craddock et al 2012)
  - another method is to set dipoles with arbitrary spacing after cortical segmentation or on cortical meshes
- Using sensor-level connectivity can lead to spurious connectivity caused by a common signal source

Connectivity

- metrics differ in linearity, information included (amplitude and phase), accounting for volume conduction and directionality

Functional metrics

- Correlation
  - prone to volume conduction
  - EEG signals also use a common reference
  - MEG signals are less affected by these problems but field spread may also exist
  - Strategy: source localization, but signal leakage may occur between voxels
- Coherence
  - extension of correlation to the frequency domain
  - similar issues as with correlation
  - however, has been used more widely with DICS
- Partial coherence
  - computed by removing the linear effect of a common signal
  - no ideal signals for common signal Z
- Phase coherence
  - coherence (or MSC) only measures linear relationships and may fail to detect non-linear interdependencies
  - instantaneous phase of time series is computed, interactions are estimated by n:m time-dependent phase synchronization
- Above approaches are valid if time-series are approximately oscillatory
- Synchronization likelihood
  - linear and non-linear synchronization, suitable for non-stationary data
  - distance between two vectors in state space is the similarity metric
- Phase locking value
  - detects frequency-specific transient phase locking
  - phase difference between two TFRs at each time
  - sensitive to VC and reference electrodes
- Imaginary component of coherency
  - complex coherency - cross-spectrum divided by the product of the two power spectra
  - reflects true interactions, depends on the amplitudes of the signals and the magnitude of the phase delay
- Phase lag index
  - removes zero-lag synchronization and the amplitude information included in iCoh
  - based on consistent non-zero phase lag between two time series
- wPLI and dwPLI
  - the sensitivity of PLI to VC and noise can be affected by discontinuity (e.g. phase lags turning into phase leads)
  - wPLI was developed to increase the capacity to detect true changes - contribution of the observed leads and lags is weighted by the magnitude of the imaginary component and the cross-spectrum
  - dwPLI has been suggested to reduce sample size bias
- Band-limited power correlation/amplitude envelope correlation 
  - functional coupling without coherence or phase coherence
  - signal is expressed using the hilbert transform of the time series
  - envelope is obtained by measuring the magnitude
  - pearson's correlations between hilbert envelopes is obtained as a metric
- Power envelope correlation of orthogonalized signals
  - signals that reflect the same source at two different sensors have identical phase
  - signals from different neuronal populations may have a variable phase relationship
  - this difference is used to remove zero-lag correlation
  - orthogonalization - removing the linear regression (removing the components sharing the same phase)

Effective metrics

- Granger causality
  - bivariate linear autoregressive models of two time series
  - if variance of the error term is reduced by incorporating information about the other signal, they are assumed to be be granger-dependent
  - AIC or BIC are used to determine the model order
- Dynamic causal modeling
  - metric of causality with a Bayesian framework
  - models the system at the neuronal level (neuronal mass model)
  - neuronal dynamics => BOLD signals via a hemodynamic model
  - Goal - estiamte parameters at the neuronal level such that the modeled and measured BOLD signals are optimally similar
- Phase Slope index 
  - direction of information flow during multivariate time series from complex systems
  - slope of the phase spectrum

Choice of metric

- which types of errors are acceptable
- Specific research question
- clear hypothesis

Source estimation

- requirements for algorithms:

  - reconstruction of time series data in the source space is possible
  - number of estimated sources as well as location and orientation are accurate
  - computation demand is low

- Strategies for identifying significant connectivity pairs:

  - selection of individual regions based on findings from other studies => tests for connectivity of time-series adta based on these regions
  - selection of regions based on their activity and subsequent tests for connectivity
  - selection of regions directly based on their connectivity (e.g. DICS)

### A mechanism for cognitive dynamics: Neuronal communication through neuronal coherence (Fries, 2005)

- A mechanism for cognitive dynamics - communication through coherence

Abstract

  - Groups of neurons active at any time
  - How do they interact?
    - Via coherence
    - Rhythmic excitability fluctuations

Intro

- We have selective attn and cognitive control
- Anatomical connections stay unchanged on the timescale of ms, but communication is altered
- Model: neuron sends message (AP rate or degree of sync)
  - Receiving neurons combine input
  - Distribution and reception is governed by anatomy
  - However, cognition requires effective communication on top of anatomy
  - Implemented by patterns of coherence

CTC hypothesis

  - Neuronal groups oscillate
  - Oscillations modulate excitability
  - Peaks are windows
  - Also relevant for binding perception (BBS)

Feedforward models:

- FR:
  - Neurons communicate by changing the firing rate, receiving neurons integrate the input and modulate their FR
- Degree of spike sync:
  - Neurons are sensitive to densities of spike input (bursts)
  - Neurons of groups synchronize bursts

Coherence

- Oscillations affect output and sensitivity
- To have effective communication:
  - Timing must be predictable (oscillations)
  - Spike travel time must be reliable (conduction velocity)
  - Sending group times the output with the open window (based on the other two)

Frequency bands:

  - Accounting for delays is important
  - If conduction delays are on the same order as cycle length, two groups are coherent at 0 phase (send at one peak, arrive at next)
  - However, more likely that this happens within one peak
  - Gamma band = cycle length 10-30 ms, conduction delays = 1-3 ms

Selective coherence:

  - Preclusion of communication is important
  - Global phase locking in epilepsy
  - Non-communication through non-coherence
    - Irregular oscillations (broadband) restrict spurious coherence
    - Physiological oscillations are only predictable for a few cycles

Corticospinal coherence:

  - Hazard rate correlates with RT correlates with synchronization between muscle EMG and MEG in contralateral motor cortex

Binding:

  - Possible scenario to test synchronization as a measure of selectivity
    - Attended visual stim induces stronger gamma band
    - If there's two inputs, the receiving neurons will get two inputs of bursts of spikes (non-synchronized)
    - Attended stimulus will be more gamma-synchronized

- Flexible pattern of coherence can modulate effective gain despite constant anatomical connections
- Neurons can entrain to the rhythm and made sensitive for selected input

### A tutorial review of FC methods (Bastos et al, 2016)

Abstract: 

	- Oscillatory activity may coordinate networks of neurons
	- Rhythmic oscillations can be quantified with many metrics
	- Review metrics and their pitfalls

- Cognitive tasks require a coordinated flow of information
  - Oscillations underlie dynamic coordination
  - Oscillations - synchronized rhythmic excitability
  - Facilitate flow of information
  - Neural information is reflected in action potentials that can be organized in bursts

Evaluating synchrony

- Invasive vs non-invasive methods
- Experimental vs task-free
- Challenges:
  - At least 42 distincs methods
  - Some methods are based on rigorous theory (GC), others are *ad hoc* (when needed) modifications (PLV)
  - Algorithmic interpretation can be complex
    - Research groups may have their own implementations
    - Interpretation is hard

Taxonomy

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

Measures:

Phase synchrony 

- computed from frequency domain representation of two signals across time windows for a set of frequency bins <= phase and amplitude estimate
- $Ae^{i\phi}$ or $x + iy$ (complex valued numbers)
  - $i$ is the imaginary number
  - $\phi$ - angle (argument)
  - A - magnitude of vector 
  - Cross spectrum between signal 1 and 2 (S1 and S2)
    - $ S1*conj(S2) = A_1e^{i\phi}*A_2e^{i-\phi}=A_1A_2e^{\phi_1-\phi_2} $
    - get complex number (vector in 2D space), magnitude is $A_1*A_2$​, angle = phase difference

Cross spectrum - correlation between two signals in the frequency domain

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

Coherency

- Remove ||, get complex value
  - Phase difference angle is now interpretable as a time delay
  - Under real circumstances - can't really assign directionality
  - Fixed time delay - phase difference will be a function of frequency
  - For example, if there's a time lag of 10 ms and a rhythmic process that exists between 8 and 12 Hz:
    - at 8 Hz, 10 ms is 10/125 of the cycle
    - at 12 Hz, 10 ms is 10/83.3

Phase Slope Index

  - Generic quantity to infer unidirectional interactions
  - Computed from coherency, quantifies the consistency of the direction of the change in the phase difference

Imaginary part of Coherency

- Contributions along the real axis - instantaneous interactions due to field spread (volume conduction)

Phase Locking Value

- Apply formula for coherence to FT signals
- Vector average of the relative phase across obsevations
- $plv_{xy}(\omega) =|\frac{1}{n}\sum_{k=1}^{n}e^{i(\phi_x(\omega,k)-\phi_y(\omega,k))}|$
- length of the vector average of a set of phase difference estimates

Other measures:

- PLI - distribution of phase differences across observations
  - Averaging the sign of the phase difference per observation
  - Non-zero phase differences cannot be caused by volume conduction
    - Also: wPLI, dbwPLI
- PPC - pairwise phase consistency:
  - Distribution of phase differences across observations will be clustered around an avg value if there's true synchronization
  - Not biased by sample size
- More than pairwise:
  - Graph theoretic approaches

Problem: common input

- How to correctly infer a direct interaction when there's possible unobserved sources
- Information from observed sources can be used to remove indirect sources

Granger causality

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

Bivariate vs multivariate

- Multivariate - all channels
  - all information is taken into account
- Bivariate - pairs of channels
  - more stable results
- Multivariate approach => spectral transfer matrix
  - can be used to compute the directed transfer function (DTF) and partial directed coherence (PDC) - connectivity metrics

Common problems

- MEG/EEG/LFP recordings reflect a mixture of a signal of interest and noise
- observed vs unobserved input contributions

### Common reference problem

- spurios functional connectivity can result from a common reference channel
  - fluctuations in potential at the reference locaiton will be reflected in both (zero time lag)

Volume conduction/field spread

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

SNR Problem

- Disentangling true signal and noise
- Affects Granger causality - can lead to an asymmetric relationship because noise weakens predictive power
  - weak asymmetry
- Strong asymmetry - true time lagged relationships
  - solution - time-reversal of the signals
  - flips the dominant direction only in the case of true synchronization (e.g. will be unchanged for SNR-affected synchronization)
- Can also be addressed at the experimental level
  - control for impedances of electrodes
  - Analytic approaches: DCM

Unobserved common input

- Direct vs. indirect interactions
- Imaginary part of coherence - if close to 0, then synchronization is entirely due to zero-lag input (common input)
- Granger causality
  - But: real-data doesn't always have equal coupling strength, same time delay and equal SNR, so can reflect spurious connectivity as well

Unbalanced data 

- Small sample size - large bias

  - different number of observations - overestimated connectivity in the condition with a smaller sample size

- In non-parametric spectral estimation techniques: vector summation operation, normalized by total # of trials

  - to estimate bias: rearragne data segments (temporal alignment between channels)

- other approaches:

  - randomly delete trials in a higher n condition to equate the number
    - best - bootstrap
  - non-parametric statistical test
  - use unbiased metric like PPC

### Parametrizing neural power spectra (Donoghue et al 2020)

- Neural oscillations are widely studied and applied in many paradigms and disorders

- Canonical bands are infraslow (< 0.1 Hz), delta (1-4 Hz), theta (4-8 Hz), alpha (8-13 Hz), beta (12-30 Hz), low gamma (30-60 Hz), high frequency activity (60-250 Hz) and fast ripples (200-400 Hz)

- Standard approaches do not assess whether true oscillatory activity is present

- Oscillations manifest as narrowband peaks of poewr above the aperiodic component

- Applying narrowband filtering (like 8-12 Hz for alpha band) can lead to misinterpretation

- Processes that contribute to narrowband power:

  - Reductions in oscillatory power
  - Shifts in center frequency
  - Reductions in broadband power
  - Changes in aperiodic exponent ($1/f^\chi$)

- There is clear variability in central frequency in different bands with age and different behavioral states

- Oscillations are also embedded within aperiodic activity

  - Noise has power at every frequency
  - This activity has a 1/f distribution
  - The power is exponentially decreasing with increasing frequency
  - The exponent $1/f^\chi$ defines the slope of the aperiodic power

- The aperiodic component also has an offset parameter

- This component should not be ignored, as it also contains physiological information

  - The offset is correlated with spiking and BOLD
  - The exponent is related to the integration of synaptic currents

- When there is more excitation, the spectrum is flatter (and vice versa)

- Both periodic and aperiodic parameters change in meaningful ways and discarding aperiodic activity can confound oscillatory measures

- Algorithm:

  - Fit aperiodic signal (estimated)
  - Subtract aperiodic component (result is oscillatory peaks + noise)
  - Fit a Gaussian distribution to the peak and remove them
    - Continue until below the noise threshold
  - Fit multiple Gaussian on signal from step 2 (without the aperiodic component)
  - Subtract the multi-Gaussian peaks from the original data
  - Re-fit the 1/f component
  - Combine 1/f+multi-Gaussian to capture 99% of PSD variance

- The algorithm was tested against simulated power spectra with known ground truth and performs comparably to human raters

- Simulated data:

  - Simulated spectra - combination of Gaussians with a variable center frequency, power and bandwidth + an aperiodic component with a varying offset and exponent + noise
  - Assessing algorithm - overall fit error + number of peaks (the algorithm can trivially fit every peak)
  - Power returned by the algorithm refers to aperiodic-adjusted power

- Age-related differences in parameters:

  - Variability of the alpha in occipital EEG channels as compared to the canonical 10 Hz alpha band
  - Slower alpha center frequencies than younger adults, bandwidth did not significantly differ between groups
  - The adjusted alpha power difference was 0.33, non-adjusted 0.45 (so the periodic and aperiodic changes can be conflated)

- Working memory analyses

  - Predicting performance with ordinary least squares - the most consistent model was using the offset and exponent
  - In the older group, aperiodic-adjusted alpha power was a significant predictor, but in the younger adult group no measure of alpha power predicted behavior
  - More accurate predictions come from aperiodic activity which may be misinterpreted as alpha dynamics in canonical analyses

- Spatial analysis of periodic and aperiodic parameters

  - Large dataset of source reconstructed rsMEG
  - When all participants and locations are combined, the distribution of center frequncies recapitulates canonical frequency bands
  - Aperiodic-adjusted oscillation band power recapitulates spatial patterns - beta at frontal midline, alpha at posterior and sensorimotor, beta centrally over the sensorimotor cortex
  - Oscillations score - how often an oscillation was observed for each band across the cortex weighted by the relative power of the parameters
  - Alpha and beta oscilaltions are more consistent across the cortex, theta is more variable, but the consistency of oscillation presence and power doesn't mean that the center frequency is also consistent 
  - As for the aperiodic component, highest exponent values are found in posterior regions and the exponent gets smaller as it moves anteriorly

- Standard analyses rely on canonical bands and conflate spectral power with oscillatory power

- In the time-domain, aperiodic exponent differences manifest in voltage

- Interpreting the parameters:

  - Presence of power above the aperiodic component suggests an oscillation, but does not always imply a true oscillation - sharp wave whythms or mu rhythm will manifest as narrowband power at harmonics of the base frequency

  - Lack of a peak does not imply lack of an oscillation

    

  

