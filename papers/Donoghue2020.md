# Parametrizing neural power spectra

Donoghue et al 2020

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

    

  