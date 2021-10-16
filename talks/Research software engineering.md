## Research software engineering

- Bio background - coding involves multiple brain areas, including memory areas, WM and the multiple demand system
- Coding can be cognitively hard, so simplifying code is best
- Research code can also be long-term memory intensive, so commenting stuff and simplifying things is, again, helpful

### Practical lessons

- what needs to be tidy?
  - project folder structure
  - code style (PEP8 guide)
  - notebooks
  - scripts
- one repo = one project
- templates: turing way, data science cookie cutter, shablona
- example template:
  - core code in one folder
  - docs
  - compatible with pip install
- use filenames that indicate hierarchy (but if you want to use these in a packege, don't start with a digit)
- use a master script to bind everything together (make/Bash/nipype)
- use documentations for functions
- IPython notebooks are hard to keep tidy because they're non-linear

- keep things decoupled!
  - spaghetti code is convoluted and hard to separate

### Testing and other strategies

- automated code testing makes code testing formal instead of just running bits of code to see if they work
- assert throws an error if the assertion is false
- memoization - global cache to save intermediate output

