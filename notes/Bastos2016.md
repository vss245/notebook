---
title: Bastos2016
created: '2019-12-21T01:01:11.817Z'
modified: '2019-12-21T01:11:45.429Z'
---

### Bastos2016
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
    - $S1*conj(S2) = A_1e^{i\phi}*A_2e^{i-\phi}=A_1A_2e^{\phi_1-\phi_2}$
    - get complex number (vector in 2d space), magnitude is A1*A2, angle = phase difference

### Cross spectrum - correlation between two signals in the frequency domain
  - If there's consistent differences in phase, weighted sum of the CSD will be non-zero, whereas if the phase differences are inconsistent, it will be 0
  - Real data will probably be between 0 and 1
- Coherence coefficient:
  - W = frequency    
  - X and y - signals 

### Coherency
- Remove ||, get complex value
  - Phase difference angle is now interpretable as a time delay
  - Under real circumstances - can't really assign directionality

### Phase Slope Index
  - Generic quantity to infer unidirectional interactions
  - Computed from coherency, quantifies the consistency of the direction of the change in the phase difference
### Imaginary part of Coherency
- Contributions along the real axis - instantaneous interactions due to field spread (volume conduction)

### Phase Locking Value
- Apply formula for coherence to FT signals
- Vector average of the relative phase across obsevations

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

## Problem: Common input
- How to correctly infer a direct interaction when there's possible unobserved sources
- Information from observed sources can be used to remove indirect sources
