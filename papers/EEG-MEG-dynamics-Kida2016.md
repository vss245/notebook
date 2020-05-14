# Multi-Dimensional Dynamics of Human Electromagnetic Brain Activity

- MEG and EEG provide information in space, time, and frequency
  - also activity magnitude, connectivity
- brain regions have billions of connections that affect overal population level dynamics

### EEG/MEG basics

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

### Connectivity

- metrics differ in linearity, information included (amplitude and phase), accounting for volume conduction and directionality

#### Functional metrics

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

#### Effective metrics

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

#### Choice of metric

- which types of errors are acceptable
- Specific research question
- clear hypothesis

### Source estimation

- requirements for algorithms:

  - reconstruction of time series data in the source space is possible
  - number of estimated sources as well as location and orientation are accurate
  - computation demand is low

- Strategies for identifying significant connectivity pairs:

  - selection of individual regions based on findings from other studies => tests for connectivity of time-series adta based on these regions
  - selection of regions based on their activity and subsequent tests for connectivity
  - selection of regions directly based on their connectivity (e.g. DICS)

  