# Graph theory approaches to functional network organization in brain disorders: A critique for a brave new small-world

- Problems in using graph theory approaches:
  - region parcellation and edge definition methods vary widely
  - numbers of connections across graphs can be problematic in clinical populations and induce spurious differences
  - few metrics are common across studies
  - hypotheses are tested without a clear neurobiological rationale and without taking other levels into account (e.g. global topology and modular structure)
- The brain as a functional network whose coordination gives rise to complex behaviors (particularly in the resting state)
- Methodological challenges: 
  - quality of resting state data
  - motion-related artifacts
  - length of resting-state scans
  - brain parcellation
  - effect of data processing on conclusions
- Clinical considerations:
  - differences in the overall level of functional connectivity between patients and controls => differences in the number of spurious connections 
  - many findings are non-replicable

### Review of current studies

- Graph: collection of nodes with links
- resting state data - estimates intrinsic connectivity patterns
- Metrics:
  - clustering coefficient - local density of connections
  - degree - pairwise connections to the node
  - density - number of observed connections to the number of possible connections
  - modules - densely linked clusters
  - path length - shortest distance separating two nodes
  - weight - quantified relationship between nodes 
- defining nodes:
  - most studies define graphs based on comprehensive parcellations of most/all of the brain, some focus on targeted subnetworks
  - **Recommendation: using different parcellations in the same dataset to determine if findings are parcellation-dependent**
- defining edges:
  - MRI - correlation
- quantifying FC:
  - bivariate correlation does not separate the direct connectivity between A and B from indirect effects attributable to C, D etc
  - conditional methods like partial correlation rely on inverting the covariance matrix and removing common variance 
  - **Recommendation: partial correlations should be interpreted based on the relative edge density and mean FC**
  - negative edges in graphs
- **Global network metrics should be reported as a sanity check (degree distribution, clustering coefficient, characteristic path length)**

#### Levels of analysis

- information available ranges from global information (average path length etc) to connectivity differences in a specific edge
- **many studies provide limited theoretical justification for why the pathophysiology of a disorder should alter the global topology**
- Small-worldness:
  - Watts and Strogatz 1998 - organization of C. elegans CNS reflects a small-world topology
  - Many current studies focus on disconnection and loss of network efficiecy
  - however, the relevance of this organization for human information processing is unclear
  - Modularity can have more important implications
  - Unclear whether brain pathology affects small-worldness
    - preserved even in anesthesia and loss of consciousness
    - conventional measures also depend on density and do not handle variations in connection strength
  - modular effects may be very strong but not affect overall global metrics
- Most pathologies such as brain injury or AD primarily affect regional hubs and may not be visible in global metrics
  - hypotheses must be matched with graph analyses

**Recommendations: standardization of metrics to facilitate reproducibility and meta-analyses, handling negative FC values, reporting graph statistics and other broad metrics, providing theoretical justification**





