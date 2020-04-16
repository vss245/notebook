# Intro to neuroinformatics
## Introduction
- Avg weight of the human brain is ~1.5 kg and 1-1.2 L in volume
	- Why do we have a brain?
		- Process information from the outside world
		- Acc. to Daniel Wolpert - need to perform conscious movements
		- Intermediate organism - sea squirt (born with a brain, moves around, settles & digests its brain)
	- Brains are information processing systems
		- There is a constant loop:
			- Stimuli received
			- Encoded into neuronal activity
			- Perceived, integrated, memorized etc
			- Neural signals are decoded
			- Converted into movement, actions, decisions and behavior
	- Many different types of neurons
	http://www.mind.ilstu.edu/curriculum/neurons_intro/imgs/neuron_types.gif
	- Factors in brain efficiency:
		- Brain size:
			- Humans don't have the largest brains of all species
		- Relative brain size:
			- Human brain size relevant to the body is pretty big, but some species have an even higher ratio (e.g. small monkeys, ants)
		- Amount of neurons:
			- Rodents  e.g. capybara (76 g brain) - 1600 M neurons, capuchin monkey (52 g brain) - 3690 M neurons
		- Human brains have 86000 M neurons (86 B)
		- Neanderthal's brains were larger than homo sapiens' brains, though this is an exception because usually with evolution brain size tends to increase
	- Computer
		- Computers are approaching brains in terms of complexity (# of units -> # of neurons, specialization of sections, scaling up the size)
		- First computers - Turing machine
		- Formal definition of computing - input , process, output
		- Neumann - augmented Turing's model, introduced the concept of CPU
			- Von Neumann bottleneck - computers spend a lot of time on memory, e.g. retrieval, saving etc
		- Differences between brains and computers
		
	
	Similarities 					Differences
	- Process information		- Parallel computation
	- Represent information		- Separation of memory and processing
	- Have memory					- Constantly adapting
	- Use signalling				- Chemical signaling
	- Consume energy				- Robust to damage
	- Learn from inputs			- Energy efficient
	- Logical operations		- Analog computation
	
	- Computer capabilities:
		- Computers are very capable, but there are also challenges, especially in terms of perception and mobility
	- Deep neural networks:
		- Use artificial neurons
		- Deep = many layers of information processing
		- Trained using images
		- Examples:
			- AlexNet = 60 M connections
			- Current record is ~5% of errors
		- Deep learning can describe images, though it doesn't work properly sometimes
	- Computational power
		- Computational power of computers has increased exponentially
		- Current fastest supercomputer - 1.31 PB memory
		- The fastest supercomputer in 2013 could only simulate 1% of the brain (1 second of activity took 40 minutes)
	- The only kinds of neurons we can reliably simulate are point neurons
	- Neurons have morphological complexity that is related to its functions
		- To understand/model this complexity, need a lot of data from EM 
	- We have exceeded the computational power needed to model brains, but we are still far from achieving it 
	- Two ways of constructing:
		- Explicit - get the building blocks, assemble according to plan
		- Implicit - start with one cell and specialize, everything ends up in the right place
		- Why does that matter?
			- How things are build right now (explicit)
				- Humans build machines to build chips on the nanometer scale
				- The smaller the level of construction (i.e. the higher the complexity level), the more space is needed for the factory
			- How humans are 'constructed' stays on pretty much the same level
				- No explicit building plan
				- DNA:
					- 25000 genes, 3*10^9 base pairs
					- Number of neurons = 10^11, number of synapses = 10^15 
					- DNA doesn't have enough information to encode everything explicitly, but more than enough space to encode everything implicitly
	- DNA vs computer code:
		- Genetic code is relatively short (~750 MB)
		- No 1-to-1 correspondence between genome length and capability (e.g. the genetic code of an amoeba is larger than human's)
	- How to use implicit encoding?
		-  Encode small 'machines' that implicitly encode the principles
		-  E.g. 'detect' a chemical gradient, grow out in that direction
		-  http://www.ncbi.nlm.nih.gov/pubmed/23966845
	
## Organization of vertebrate nervous system
- Which parts of the nervous system are relevant to computation?
		- Patterns are crucial in the organization of NS
	- Example: tennis player
		- Motor program being deployed
		- Actions in relation to a particular goal (strategy)
		- Perception/cognition
	- How to model this? (e.g. build a robot)
		- Axial posture (needs to have an axis)
		- Long range sensors (e.g. arms, legs, eyes, ears, nose)
		- Local sensors (e.g. hands perceiving touch, proprioception)
			- Sensors assembled in a head
		- System monitors and power management (NS)
		- Everything has to be placed in a strategic context (motivation, reward)
		- The last two things are separate from the mechanics
	- How does biology approach this?
		- Process begins with a single cell
		- Systematic organization due to differentiation and cell division
	- Development of the nervous system: 
		- Approximation  of cellular development:
			- Animal stuff & vegetal stuff (living vs energy)
			- Initial division - very little explicit structure
			- At some point - three prominent types of cells that would form layers of tissue for specific purposes
				- Ectoderm (external layer of the final organism)
				- Mesoderm (muscle and bone)
				- Endoderm (digestion, absorption)
			- Some ectodermal cells can become sensory
			- Also inside ectoderm: drop out into the space between E and M, specialize into neural nets - cells with long connectors that can connect and distribute sensory input to muscle and digestion to affect some  change for the needs of the organism
		- There can be all kinds of configurations of neurons
			- e.g. radial symmetry, bilateral etc
		- In vertebrates:
			- Organization of the neuron - long axons that send information, short dendrites that receive information 
- How does this develop?
	- Starts from an egg (animal and vegetal side)
	-  Entering sperm establishes an axis across the cell 
	-  Cells will begin to divide, animal cells on top, energy-driven cells on bottom, space (blastocoel) in the middle
	-  Effect of blastocoel - pumps pressure into the cell, makes more space to form layers around it
	-  Divides into ectoderm, mesoderm and endoderm
	-  Primitive gut begins to form
	-  Notochord (axis), neural tube form
	-  Structure elongates - one end becomes the head, the rest is a segmental structure
	-  Endodermic cells arranging to be energy extractors
- Neural system development:
	-  Some region of ectoderm invaginates and folds into the neural tube
	-  Neural crest on top of the neural tube - melanocytes, Schwann cells, adrenal medullary cells, dorsal root ganglion cells, cranial nerve sensory cells, autonomic ganglion cells (distribute themselves into the gut, circulation etc)
		-  Alar plate (dorsal side) gives rise to all sensory structures along the tube and in the head
		-  Basal plate (ventral side) gives rise to motor structures 
	- Alar & basal plate development:		-  The tube elongates further and divides into segments
		-  Brachial  has a shoulder group (red - proximal, green - distant)
		-  Lumbar has a hip group
	- Development of the brain:
		-  More irregular manner than spinal cord
		-  Twists in the tube
	- Regionalization of the embryonic brain:
		-  Alar and basal lamina are still a thing
		-  Alar - cortex, basal - motor activities
- Remote sensors:
	- Vision from the eyes => thalamus => distributed to V1
	- Sound from the ears => up to thalamus => auditory cortex
	- Smells do not pass through the thalamus => directly to the olfactory cortex
		-  Probably evolutionary 
- Somatic sensory circuits:
	- Touch, pressure, pain receptors on the surface of the skin
		-  Cell bodies of these neurons are outside of the tube (came from neural crest cells)
		-  Go through the hindbrain and into the somatic sensory cortex through the thalamus
	- Touch, vibration, joint proprioception, also muscle proprioception 
		-  Doesn’t just go into the cortex through thalamus, also goes into the cerebellum through the pons
		-  Cerebellum helps with coordination of the execution
		-  Muscle proprioception (length and tension - spindles and Golgi tendon organ) go into the cerebellum only, not propagated into cortex

- Somatic motor circuits:
	- Many interlocking circuits deciding what muscles should do
	- Simplest case: neuron in MC directly connected to the motor neuron (cortico-spinal fibers) - not a very favorable design scheme, focused on shoulder muscles & manipulator muscles, very few
	- Infrastructure dominated by the midbrain
	- Midbrain motor structure also controls the output to muscles
	- Cerebellum has a direct output into the midbrain
		-  Also receives balance information
	- Loops:
		-  One loop begins in the cortex, comes down to the pons, out to the cerebellum, then back to the thalamus, then upwards back to the cortex (cerebello-cortical loop)
		-  The cortex also projects to the basal ganglia, some part of it is being reported to the thalamus, then back to the cortex
		-  Basal ganglia - funneling the movements with cortical and midbrain feedback
-  Motor control of the muscles is largely in context of midbrain locomotor infrastructure system, the details - cerebellum, the program - basal ganglia + cortex, specific activities on top of the structure - cortex
- Functional organization of the cortex:
	-  Sulci and gyri to have more surface area
	-  Central sulcus - divides sensory and motor
	-  Lateral sulcus - divides perception and generation

-  Distribution of function according to space - begins with distal vision, then body space - more proximal, sensory - immediately on your surface (downwards - specialization towards recognition, order of complexity)
-  From the other side - distribution according to time - motor cortex is moving the muscles now, further down - motor action in extended space, further down - abstract and distant planning and goals; front - very goal-oriented and exploratory; interactions with the limbic cortex

## Membrane potential 
- Level of neurons and synapses
	-  Neurons have a potential difference between the inside and the outside (as well as other cells in the body)
- How much energy is spent on neural activity?
	-  Almost half of all energy used by neurons is used to generate resting potentials & spikes
	-  The brain takes up 2% of the mass, but 20% of the energy consumption
	-  Energy consumption limits computation
- Mechanism of membrane potentials
	- $$V=(k_s T)/q ∗ln⁡([K^+]_{out}/[K^+]_{in})$$
	-  ^ Nernst equation for a channel permeable to a particular ion
	-  Inside: K
	-  Outside: Na, Cl, Ca
	-  Plugging an ion concentration into the Nernst equation gives us the reversal potential
		- $$E_K$$=−90 mV
		- $$E_{Na}$$= +50 mV
		- $$E_{Cl}$$=−65 mV
		- $$E_{Ca}$$= +150 mV
	-  Goldman-Hodgkin-Katz equation
		$$V=(k_o T)/q∗ln⁡((P_K [K^+ ]_{out}+ P_Na [Na^+]_{out}+ P_Cl [Cl^− ]_{in})/(P_K [K^+ ]_{in}+ P_Na [Na^+ ]_{in}+ P_Cl [Cl^− ]_{out} ))$$
		- $$P_{ion}$$= permeability
		- The resting potential of the neuron is ~-70 mV
		- If the flow of ions out->in isn't equal to the opposite flow = net current
		- Currents are proportional to$$g_ion (V−E_ion)$$ - channels behave like Ohmic conductors and resistors
	-  Total current is the sum over all ion types
	-  Voltage is given by $${g_K∗E_K+g_{Na}∗E_{Na}}/{g_K+g_{Na}}$$
	-  The depolarization at soma is smaller than the depolarization at the dendrites
	-  Time constant - how long the depolarization could persist

## Time and space constants
- Time and space dependence
	- Deriving an equation for potential as a function of both space and time 
	
	$$V = V(x,t)$$
	
	$$I_m$$ is the membrane current (leak)
	
	$$ I_m=g_m∗(V−E_m) $$
	
	$$C_m=q/V$$
	
	$$C_m∗dV/dt=dQ/dt=I_m$$
	
	$$I_e=I_m+I_c$$
	
	$$I_e=g_m∗(V−E_m )+C_m∗dV/dt$$
	
	$$dV/dt=−g_m/C_m ∗V(t)+ g_m/C_m ∗E_m+1/C_m ∗I_e$$
	
	At equilibrium, dV/dt = 0
	
	$$I_e=g_m∗(V−E_m)$$
	
	$$V(t)=V_{inf}∗(V(0)−V_m )∗e^{(−t/(\tau_m ))}$$
	
