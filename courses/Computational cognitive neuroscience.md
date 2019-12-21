---
attachments: [brain.png, parts.png, synapse.png]
title: Computational cognitive neuroscience
created: '2019-12-20T23:34:28.802Z'
modified: '2019-12-21T01:00:26.067Z'
---

# Computational cognitive neuroscience

(skipped Networks, Perception, Motor Control)

## Intro
- Computer models for cognitive neuroscience
	- Models must be constrained by data and must generate empirically testable predictions
- Ockham's razor:
		- Develop the simplest possible model that captures the most possible data (ant not just transport the mysteries from one system to another)
		- Example: many biological properties of neurons are irrelevant for the information processing function
- Needed: middle ground between biological detail and cognitive functionality
- Reductionism - complex $\rightarrow$ simple
- Reconstructionism - reconstruct complex from simple
- Emergent phenomena are about interactions between parts - e.g. two connected gears produce torque
	- Doesn't really depend on material - transcendence
	- Does the same apply to neuroscience? Are physical interactions with the environment importnt?
- Why do we care?
	- We need to know about hardware (e.g. ion channels, pathways, behavioral paradigms) so thawt we can appropriately constrain our models
- Marr - three levels:
	- Computational
	- Algorithmic
	- Implementational
	  - We might still need to focus on the implementation
- 1960s = assume the brain is like a computer, use logic and symbolic propositions
	- Since then, Bayesian frameworks
		- Graded nature of processing, optimal processing of uncertainty +
		- Not a good fit on the neural level - 
- Examples:
	- Biology of hippocampus (inhibition, broad diffuse connectivity + rapidly learning information and memory = biological details produce pattern separation to keep memories distinct)
	- Biology of dopamine, BG and PFC + making decisions based on prior reward memory = translating later utility into earlier decisions of what to retain, decision-making based on positive and negative outcomes

## Brain areas
![](@attachment/brain.png)
- Outer portion - neocortex
- Under - subcortical structures
  - Hippocampus - memory
  - Amygdala - emotionally salient stimuli
  - Cerebellum - motor coordination, cognition
  - Thalamus - pathway for sensory information
  - Basal ganglia - collection of areas related to motor control and executive function, also initiating movements
- Parts:
![](@attachment/parts.png)
- Brodmann areas - broad areas based on anatomical differences
### Lobes
  - Occipital lobe (visual processing)
    - V1 (primary visual cortex)
    - higher level visual areas
  - Temporal lobe (categorization)
    - inferotemporal cortex - 'what' pathway, visual recognition
    - primary auditory cortex (A1)
    - language/auditory processing
    - anterior regions - semantic knowledge
    - medial temporal lobe
    - hippocampus (HC)
  - Parietal lobe (metrical information)
    - 'where' pathway
    - 'how' pathway - guiding motor actions
    - primary somatosensory cortex (S1)
  - Frontal lobe
    - primary motor cortex (M1)
    - supplementary motor areas
    - higher level motor areas
    - prefrontal cortex (executive function)
      - anterior - abstract reasoning
      - medial and ventral - emotion and motivation
        - orbitofrontal (OFC) - reward information
        - anterior cingulate (ACC) - consequences of actions
        - vmPFC - basic body functions, neuromodulatory influence
- Evolutionarily older areas (BG, cerebellum, HC) - separating form of activation dynamics (even similar inputs map onto separated neural activity)
  - The HC also has attractor dynamics (recurrent connections in CA3)
### Visual pathway (what)
  - V1 (edge detectors)
  - V2 (intersections, depth, textures)
  - V3 (shapes, angles)
  - V4 (more complex features)
  - PIT (entire object shapes)
  - AIT (abstract/semantic)
### Visual pathway (where) 
  - parietal cortex -> motor output
### Motor pathway
  - neocortex (high level metrical processing, responses)
  - BG - inhibition/disinhibition
  - cerebellum - error-driven learning
### Learning and memory
  - HC (rapidly learning new information while not changing old)
    - sparse representations -> pattern separation
  - MTL - recognition memory
### Executive function
- PFC - top-down cognitive control
- BG interacts with PFC for a gated working memory system

## Biology of neurons
### Parts and mechanism
- Axons (output), dendrites (input), dendritical spines to form neural connections (synapses)
- Primary behavior of a synapse: 
1. triggering release of neurotransmitter (NT) from the presynaptic terminal button
2. NT binds to post-synaptic receptors
3. Ion channels open - signal is communicated (if excitatory NT - increases potential, if inhibitory - decreases)
- Main neurotransmitters:
  - Glu (+) - AMPA, NMDA and mGluR receptors
  - GABA (-) - GABA receptors
![](@attachment/synapse.png)
### Electrophysiology
- Atoms:
  - Electrons and protons (have electrical charge, neutralize each other)
- Ions: more of $e^-$ or $p^+$ (have net charge)
  - $Na^+$
  - $Cl^-$
  - $K^+$
  - $Ca^{2+}$ - two net positive charges
- Ions flow because of volage (difference in electric potentials)
  - opposite charges attract
  - $I = GV$ (current = conductance (how wide is the path between imbalanced charges) x potential)
  - diffusion - ions move around until uniformly distributed
    - increases entropy
- Resting (equilbrium) potential of a neuron is around -70 mV
  - Na pump gets Na ions out
  - Cl ions are pushed out because of the potential
  - K ions are drawn into the cell
  - $I = G(E-V)$, where E us the driving potential

## Learning mechanisms
- In a neural network, modification of synaptic weights - synaptic plasticity
  - achieved via spike timing dependent plasticity (LTP, LTD)
### Types of learning
  - self-organizing (developing an internal model with statistical regularities)
    - longer time scale
  - error-driven (contrasts between expected and actual, driven by NT)
    - short time scale
### Biology of plasticity
  1. the overall level of neural activity on both ends of the synapse (sending and receiving neural firing) drives the influx of calcium ions ($Ca^{2+}$) via NMDA channels
  2. synaptic weight changes are driven by the level of postsynaptic $Ca^{2+}$ in the dendritic spine associated with a given synapse
  3. low levels of $Ca^{2+}$ cause synapses to get weaker, and higher levels cause them to get stronger
### Hebbian learning
- fire together - wire together
- based on NDMA channels
- written as $\Delta w = xy$
  - change in synaptic weight w as a function of sending activity x and receiving y
### Self-organizing learning
- BCM model
-   $\Delta w = xy(y-\theta)$
  - $\theta$ is a threshold that represents the average in the activity of the receiving neuron ($\theta = \langle y^2 \rangle$, $\langle \rangle$ is the expected value (average)
- Provides a better accound of some behavioral phenomena
### Learning rate
- $\epsilon$ - multiplies the rate with which the weights change 
  - faster isn't necessarily better
  - slower learning - more experience/statistics incorporated

## Memory
- Weight-based (synaptic plasticity) vs activation-based (ongoing neural activity)
### Episodic memory
- Memory for events
- Exceptional memory can be driven by excessive rehearsal and retrieval (BG)
- Hippocampus
  - optimized to record memories using sparse representations that minimize overlap
  - trade-off between
    - pattern separation - neurons in CA1 and CA3 fire much less often, high levels of GABA
    - pattern completion - cued recall (human memory is content addressable), faciliated by recurrent connections in CA3
- Memory consolidation - migrating of memories from HC to the neocortex
  - replay during sleep
  - episodic memories become more semanticized and generalized, integrate with existing memories
### Spatial memory
- Specific cells that encode positions on a grid, borders, head direction (place, grid, head direction, border cells)
- Dead reckoning - determine current position based on previous movements
#### Theta oscillations
- Neurons fire at 8-12 Hz, different areas are out of phase with each other
- Oscillations could enable the switch between encoding and recall
- Also thought to be involved in grid cell activations and encoding sequences
### Familiarity and recognition
- Neocortex supports episodic memory traces
- Dual process model of recognition memory
  - Perirhinal cortex produces a *familiarity* signal (indicates whether stimilus was experienced recently) - can be accessed consciously somehow
  - Hippocampus provides a *recollective* memory signal (full explicit recall of the last time it was experienced)
### Priming
- Like a familiarity signal, but fully unconscious
  - slow incremental learning effects and/or residual activaation
  - paradigm: stem completion (e.g. win___)
## Executive function
- Occurs primarily within the PFC
- Receives information from posterior cortical association aeras
- Interconnected with motivational and emotional areas
- PFC
  - encodes environmental dependency (e.g. would not wear pyjamas outside)
  - inactive in dreaming
  - sits on top of the information processing hierarchy of the brain, exerts control over actions
  - robust active maintenance (or working memory) - keep a population of neurons active 
  - able to rapidly shift behavior (cognitive flexibility) by dynamically updating actvation states
- other areas
  - BG and VTA - dynamic gating of the maintenance of information
- Top down cognitive control example - Stroop Model






