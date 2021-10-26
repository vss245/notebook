## Pattern classification 

### Chapter 1

- pattern recognition is crucial
- we seek to build systems that can recognize patterns
- example: fish packing plant
  - a camera records an array of **features** (e.g. length, width etc)
  - we also notice noise in the images due to the position of the fish, electronics etc
  - we view the two populations (e.g. seabass or salmon) as having different models
  - we can try different features for the models, e.g. try a histogram for length - too much overlap, so there is no clear separation
    - try lightness, better results
  - we assume cost symmetry - e.g. each wrong class is equally costly
  - the task of **decision theory** is to find a decision boundary that minimizes the overall cost 
  - we can also use several features and now we will have a feature space $x = [x_1,x_2]$
  - overly complex models will have overly complicated decision boundaries (overfitting)
    - we need good generalization
- **analysis by synthesis** - we would like to have a model of how each pattern is generated, e.g. how we know how sounds are produced in speech recognition