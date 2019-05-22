---
layout: post
title: Meeting with Wayne
---

### Papers

We went over some of the key concepts and ideas of the 2 papers I've read more closely (Knabe et al., 2006 and Cussat-Blanc et al., 2015). Some important points:

- "Evolvability" => suitability of a representation to incremental changes (ability of genetic operators to make small changes to the model, i.e., take small steps in the search space)
- The alignment idea presented in Cussat-Blanc et al., 2015 of interest. We could do something similar with this model.
- The duplicate and mutate idea from Nicolau et al., 2010 was also interesting, good for population diversity, but it isn't a crossover operator.


### Code Base

We also went over the current Python version of the GRN code (https://github.com/umfranzw/grn-crossover). Notes:

- `simulate.py` does the initial random setup then runs the simulation (bind, produce, diffuse, then decay, repeat for set number of simulation steps)
- see `grn.py` for the implementation of the different steps
- see `Config.py` for meta parameters like population size, simulation steps, etc.
- proteins are encoded as bitarrays (current length is 4), where the most significant bit determines if the protein is internal (binds to genes) or an output protein (determines resulting program)
- protein dictionaries are hashed by protein encoding but bitarrays are variable and can't be hashed so we have to convert them to string representations first to use them as dict keys
- concentrations are by gene location
- genes keep track of their index (will need to be checked in offspring when crossoveris done)
- binding doesn't have to be a perfect match (see play param in Config) but the protein concentration does have to be above the gene's bind threshold
- the bound protein is chosen from elegible proteins (concentration above threshold) probabilisticly respectively to their relative concentrations
- bound protein is created (concentration 0) in bind function, but the concentration is set in produce according to production rate params
- diffusion is currently balanced in both directions (left/right) but can be biased and speed can be altered
- copies of the initial proteins are passed in (courtesy of copy.deepcopy) because otherwise the decay step might delete them from out internal protein list and we want to keep them somewhere
- produced proteins are generated the first time a gene is activated
- the decay step avoids network saturation
- production rate and bind threshold kind of mimic methylation/epigenetic regulation in a sense: it's regulation other than the actual sequence


### Next Steps & Misc Notes

Once Wayne finishes porting the relevant parts of his C++ code base to Python I'll fork the GitHub repo and start working on implementing a standard single point crossover operator.
This will probably involved splitting and crossing the parents gene lists and their initial proteins.
Gene paramters like bind threshold and production rate can simply be averaged for now.
I will need a way to select the parents too. 

Having a way to pull out the chain of interactions would be useful. 
So would having a metric to evaluate the crossover operator being tested.

I will write up summaries of the papers I've read and post those (retroactively perhaps). Assigned by Dr. Thulasiraman.

Next meeting with Wayne will be 2019-05-30 @2pm.

I will get a key for the lab at some point, next week hopefully?
