---
layout: post
title: Meeting with Wayne (May 30th)
---

Mostly discussed the code and the standard crossover operator.

- To deal with the duplicate initial proteins resulting in less items in the dictionary just insert a new random protein to replace it.

- To deal with the bound proteins issue we'll just deepcopy the genes and None the bound protein field

- The crossover operator comes in at a meta level (EA loop) after eval()/sim and mutation()

Wayne will get back to me about a few code things (crossover probability, meta loop, ideas for new crossover operator) soon

---

Next steps:

- Implement small fixes for duplicate initial proteins and bound proteins above
- Think about:
  - ideas for new crossover operator
  - ways to evaluate crossover operators
  - tracing/connecting events (initial_protein -> gene -> protein -> gene -> ...)


Next meeting with Wayne will be 2019-06-06 @3pm.
