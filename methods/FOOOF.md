## Aperiodic and periodic components in oscillations and power spectra

- Most power spectral densities of neural field data reflect an aperiodic component ($1/f^X$), in which power falls off with frequency, and peaks above this component (e.g. alpha, beta peaks)
- We can model these components separately by parametrizing them and then explore them independently
  - Full model of the neural power spectra: $NPS(F)=L(F)+G(F)_n$
- Periodic activity (the peaks) is fit by a Gaussian (total n Gaussians, where n is the number of peaks) - the Gaussian is a function of frequency
  - $G(F)_n = a*\exp(\frac{-(F-c)^2}{2*w^2})$
    - a is the height of the peak
    - c is the center frequency of the peak
    - w is the width of the peak
    - F is the array of frequency values
- Aperiodic activity has no characteristic frequency - in linear space, the power across frequencies decreases with $1/F^X$
  - $L(F)=b-log_{10}(k+F^X)$ - this is fit on semilog y (log power, linear frequencies)
  - $AP(F)=10^b*\frac{1}{(k+F^X)}$ is the linear analog of the above for linear power and frequencies
    - b is the broadband offset (distance to the top of the curve)
    - k is the knee - optional, but sometimes there's a bend in the aperiodic component
    - X is the exponent of the aperiodic fit (controls the slope)
    - F is the array of frequency values 

- Another way to measure 1/f properties in neural power spectra is to measure the slope of the spectrum in log-log spacing (where it will look linear), fitting a line: $L(log(F))=aF+b$
  - a is the power spectrum slope
  - b is the offset
  - F are the frequencies
- Knee in the fit:
  - With no knee, -a = X (the exponent is the negative slope)
  - To interpret the knee frequency, take the X-th root of k: $kf = k^{1/X}$
  - Check the data across the range of interest - if it looks roughly linear in log-log space, fit without a knee
- Algorithm settings:
  - Default settings minimally constrain the power spectrum model, but may
  - Consideratio