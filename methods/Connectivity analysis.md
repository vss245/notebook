# Connectivity analysis in MEG and EEG data

- https://www.youtube.com/watch?v=ZBwh0Vm4fh4
- Univariate analysis:
  - time course of activation => processing steps (ERP, averaging, TF, source analysis)
  - each channel reflects activity of sources close to sensor
- Beyond univariate: connectivity
  - combine measurements recorded at >1 locaiton
- Measures of connectivity:
  - Effective (causal) vs functional (statistical)
  - Model-based (e.g. DCM) vs data-driven
  - Time vs frequency domain
  - Linear vs non-linear

### Oscillations:

- signal with changing amplitude as a function of time (periodic)
- period - distance between two peaks
- amplitude - distance from 0
- phase defines where you are within 1 cycle
- oscillations can be represented in polar coordinates
- $S = Ae^{i\phi}$
  - A - amplitude
  - $\phi$ - phase angle
  - simplifies mathematical operations
- Observing and comparing several oscillations
  - phase difference moves around - low synchrony
  - phase difference constant or clustered - high synchrony

### Cross-spectrum 

-  $x_1=A_1e^{i\phi_1}$ - signal 1
- $x_2=A_2e^{i\phi_2}$ - signal 2
-  $x_1x_2*=\langle A_1A_2e^{i(\phi_1-\phi_2)}\rangle$
  - multiplying signal 1 by signal 2 with a flipped sign of the phase
- => CSD = fourier transform of S1 * conj(S2) => complex valued number that represents a signal in which the amplitude is the product of A1 and A2 and the phase is the phase difference

## Measures

