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

[...]

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

[...]

#### Non-adaptive distributed-source imaging 

- LORETA
- Minimum-norm estimators

#### Adaptive distributed-source imaging 

- Beamforming

## Connectivity 

- 















