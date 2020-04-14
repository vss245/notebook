# EEG
## Spectral analysis
- Deconstructing waves into sine and cosine waves (FT)
- Can be thought of as linear regression:
  - Fit a set of weights to a design matrix to explain
variance
  - $Y=\beta*X$
  - Design matrix = sine and cosine functions at diff freq (basis functions)
  - Beta = how much it contributes
  - Basis functions should be orthogona (perpendicular, dot product is 0) 
  - Frequencies can't be arbitrary (integers)
- Frequency resolution defined by length of data segments
  - 1/T is the resolution
  - N samples in signal - n basis functions
  - Highest frequency that you can determine = N/2
    - E.g. sf = 1 KHz, 1 second = 1s => multiples of 1 Hz, 1 KHz sf => 500 Hz is the highest
- Spectral leakage = true oscillations are at frequencies we can't sample, energy is spread to other frequencies
  - Controlled via tapering
## Phase and amplitude
- Complex numbers: Z = a + bi
- Polar coordinates:
  - R (length of vector) - magnitude
  - $\phi$ - angle 
  - R = |Z| = $sqrt(b^2+a^2)$
  - Phi = $arctan(b/a)$
  - a = $r*cos(\phi)$
  - b = $r*sin(\phi)$
  - Z = $r*cos(\phi)+r*sin(\phi)*i$
- Cross-spectrum between two signals:
  - signal 1*conj(signal 2)
  - $(A_1e^{\phi_1}*A_2e^{\phi_2})=A_1*A_2*e^(\phi_1-\phi_2)$
- Calculating phase, PLV and other indices

