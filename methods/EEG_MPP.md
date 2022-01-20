### Makoto's preprocessing pipeline notes

### Basic conventions

- don't put spacebars into file names
- don't shadow MATLAB's functions

#### Importing and checks

- pop_loadset to import
- check for zero/garbage channels

#### Preprocessing steps

##### Filtering

- downsample to around 250 Hz if necessary (usually you'd need a low-pass filter before downsampling, but EEGLAB does this automaticallly)
- high-pass filter at 1 Hz - removes baseline drift, lower frequencies could be contaminated by artefacts
- low-pass filter - optional, but if cleanline doesn't work, use a filter to cut off below 50/60 Hz
  - note: 50 Hz - European line noise, 60 Hz - USA
- GC notes for filtering
  - should be invariant under zero-phase filtering, but can cause problems
  - solving: end transition band at 0 Hz (?), use cleanline instead of a notch, don't put filter stop bands under Nyquist

##### Artefact rejection

- eyeblinks are generally well removed by ICA
- bad channels - clean_rawdata() (artifact subspace reconstruction) or trimOutlier() (simple outlier rejection)
- removed channels should be interpolated to avoid bias in ICA or referencing
  - default: spline, can introduce rank issues
  - spherical - better

##### Referencing

- average referencing is fairly simple
- other methods: bipolar

##### Line noise

- CleanLine uses a sliding window to estimate sin wave amplitude to subtract
- if line noise is not stationary, it may not help

##### Epoching

- epoch to -1 to 2 sec 
- recommended before ICA, but not necessary
- 