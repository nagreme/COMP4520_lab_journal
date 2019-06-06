---
layout: post
title: Meeting with Wayne (June 6th)
---

### Meeting notes:

- I will use a digraph to map the interaction in the network as they're happening, likely using the [NetworkX package](https://networkx.github.io/).

- The relationships we care about not breaking are the input to output protein relationships. Evaluation of the crossover operators will be based around that.

- There may be multiple paths between one input protein and one output protein: in that case we can probably just select a random one of the two paths? Or maybe we should prioritize the shorter path instead since it should occur more reliably?

- Once we have interaction graphs we could look for isomorphic parts of the graph, match those up, and rearrange the pieces around it? Remember gene order/index matters here (because of their range of influence)

---

### Other note:  

- I refactored the crossover code into its own file to make it cleaner and more manageable.

---

### Next steps:

- Implement interaction graphs
- Think about how to implement the new crossover operator, maybe using the interaction graphs?


Next meeting with Wayne will be 2019-06-13 @3:30pm.
