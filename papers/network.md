### Complex network measures of brain connectivity and their uses and interpretations (Rubinov and Sporns 2010)

- Brain regions can be connected via anatomical tracts or functional associations
  - This can be conceptualized as a network
  - Advantages: easy to quantify & compare
- Network – a representation of complex system, has nodes and edges
  - Can be represented in a connectivity matrix
  - Influenced by choice of imaging method, parcellation, method of connectivity
  - Issues with nodes and links:
    - Nodes typically represent brain regions and edges represent connections (directed or undirected). Ideally, nodes represent distinct brain regions, but in some methods, for example, sensor-level analysis with EEG or MEG, regions can be less distinct. 
    - Edges can be binarized (absence or presence of a connection) or weighted (strength of connection). Binary edges are easier to work with, but weighted metrics can be more meaningful
    - We may or may not want to include directionality in the model
- Network measures characterize aspects of connectivity (for the whole network or individual components)
  - Basic metrics:
    - Number of nodes and links
    - Degree – number of neighbors
      - Degree distribution, density (mean degree)
    - These metrics are useful for statistical comparisons
- In networks, we are interested in how segregated their components are (modularity), but also how integrated they are (interconnectedness)
- Measures of segregation quantifies the presence of densely interconnected separate groups
  - Clustering coefficient – the fraction of triangles around a node
  - Transitivity - same thing, but normalized for the whole network
  - Modularity – the degree to which a network can be subdivided into groups
- Measures of integration quantify interconnectedness within a network
  - Characteristic path length – average shortest path length between all nodes
  - Global efficiency – inverse of the above
  - Structural and effective networks have high efficiency, functional networks have lower efficiency
- Small world networks are supposed to reconcile segregation and integraion
  - More clustered than random networks but with the same characteristic path length
  - Prominent in anatomical networks, less so in functional (and harder to interpret)
- Other metrics
  - Motif – pattern of local connectivity
  - Centrality – importance of individual nodes
  - Degree
  - Resilience 
  - Degree distribution
  - Assortativity (how much similar nodes connect to each other)
- Examples of uses (from Journal Club):
  - Schizophrenia (van den Heuvel et al, 2010)
    - Structural networks (DTI): longer characteristic path lengths, reduction of centrality of frontal regions (i.e. less global integration)
  - Alzheimer’s disease (Supekar et al, 2008)
    - Resting state MRI: network analysis helps distinguish healthy and pathological subjects (loss of small world properties, clustering coefficient)
  - Brain development (Boersma et al, 2011)
    - Resting state EEG: development shows shift from more random to organized small-world networks (clustering, path length)
- Critique:
  - Composition of networks varies depending on method and analysis choices
  - Many studies assume the same number of nodes and edges across graphs (while pathology may reduce it for some groups)
  - Not a lot of graph metrics in common across studies
  - Hypotheses tested on a certain graph level without justification

### Graph theory approaches to functional network organization in brain disorders: A critique for a brave new small-world (Hallquist and Hilary, 2018)

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

Review of current studies

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

Levels of analysis

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





