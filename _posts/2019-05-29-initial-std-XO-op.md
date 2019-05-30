---
layout: post
title: Initial Standard Crossover Operator
---

Wayne let me know he finished the code on 2019-05-24! I forked the repository: my code can be found [here](https://github.com/nagreme/grn-crossover-COMP4520).

The first step is to implement a standard single-point crossover operator to have a baseline/point of reference for the new crossover operator.

#### Basic Outline of Standard Crossover Operator

##### Selection (see `sim.select_parents` function):

Params: population list (of Grn objects)  
Returns: the 2 selected parent (Grn objects), not necessarily different

- Pairs of parents are selected from the current population using roulette-wheel selection.

- This means that fitter individuals are more likely to be chosen as parents but not guaranteed.

##### Crossover (see `sim.std_crossover` function)

Params: population list (of Grn objects)  
Returns: the 2 children (Grn objects)

- For each pair of parents, random crossing points are chosen for the `genes` array and the `initial_proteins` ordered dictionary.

- Two new Grn objects are created (children) and each gets one half (split at the index) from each parent

- Note: no need to adjust gene indices since the number of genes is constant in the model currently and the crossover is not unequal

#### Current Issues/Conundrums

- I'm not deep copying the gene objects given to the children (simpler implementations this way for now), so the children also get the bound proteins from their parents. Should we create new gene objects and overwrite their default attributes, simply set the bound proteins to None (affecting children and parents), or something else?

- Since the initial proteins are stored in a dictionary, children that would have had duplicate initial proteins end up with less initial proteins than they should. How do we want to fix this?

- Is there a crossover probability? I think it should be handled at a higher/meta level but it could also be handled here.

- (Related to above point) I might need to change some split index selections (some edge cases may result in no crossing over currently)

#### Misc. Changes and Additions

- I added both `__repr__()` and `__str__()` methods to the Grn, Gene, and Protein classes in their respective files.

- Note the way I have to handle the fitnesses during selections to allocate wheel chunks since small numbers == better fitness

- There are a bunch of my comments, thoughts, and debugging/testing prints commented throughout the code
