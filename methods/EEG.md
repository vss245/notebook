# EEG
### What is the signal?

- EEG - synchronized activity in populations of cortical neurons

- - Pyramidal cells in cortical columns
  - Excitation of postsyn neurons => extracellular voltage near dendrites
  - => a dipole (negative charge - sink, positive charge - source)

- Electrodes only detect dipoles when they're close to the positive or the negative end

- - Tangential dipoles (perpendicular to the surface)
  - Radial dipoles (parallel to the scalp)

- Dipoles from multiple neurons sum together

- - Measurable dipole: arranged parallel and synchronously active

- Polarity of the signal depends on the orientation

- Measured signal reflects extracellular changes (and do not reflect currents within the neuron)

- EPSPs and IPSPs can produce a positive or a negative deflection in the signal depending on how close the positive or the negative region is to the scalp

- EEG = thalamocortical and corticocortical connections

### Conduction and propagation

- Wave of charges due to ions repelling each other
- In the brain, different tissues impede ion flow
- Size of the dipole also matters
- The signal travels through the brain, dura layes, skull layers, scalp and then gets to the electrode
- The layers can be approximated as a stack of capacitors
- Neural activity cycles between positive and negative voltages => rate = frequency
- Typical EEG spans 0.5-30 Hz, higher frequencies are heavily attenuated by tissues and can be contaminated by artefacts

### Where are the dipoles?

- MEG can measure the magnetic fields that leave the scalp, so it doesn't detect radial dipoles

- EEG can be sensitive to both tangential and radial dipoles

- Large dipoles deep in the brain can still be detected, but could be more prone to noise contamination (could be due to distance or due to passage through potential sources of noise)

- Identifying the source of signals is a challenge due to the fact that surface electrodes detect a mixture of signals

- Simulated models - scalp, skull and brain

- Electrode gel is necessary to pick up signals through the skull

- Noise considerations

- - External - line noise
  - Internal - breathing, muscle artefacts

### Source localization

- Electric potential differences are due to the propagation of current flow induced by postsynaptic potentials of pyramidal neurons in the head 

- Current is modeled by (forward problem):

- - Poisson's equation, which relates electric potential and charge density

  - - Potentials in a volume conductor and the applied current sources

  - Boundary conditions

  - Methods: BEM (boundary element method), FEM (finite element method) and the FDM (finite difference method)

  - Forward problem formulation: finding the scalp potential at an electrode at r due to a single dipole positioned at rdip

- Inverse problem: finding a solution out of the infinite set by introducting a priori assumptions and constraints

### Preprocessing steps

- Temporal filtering to remove irrelevant frequencies

- Downsampling to reduce memory requirements using the Nyquist theorem (in practice, about 4 times the highest frequency)

- ICA and/or manual artefact rejection

- - Interpolation of the bad electrodes

- Spatial filtering

- - Done to determine local outliers in sensor space
  - For each electrode, determine the value of 6 closest neighbors and the electrode value
  - Sort, drop min and max
  - Average the remaining values with weights proportional to 1/distance to central electride

- Detecting bad epochs with transient artefacts

- - Statistics based on outliers

- Functional connectivity (see Connectivity)

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

