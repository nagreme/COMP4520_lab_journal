---
layout: post
title: Meeting with Wayne (June 13th)
---

This meeting was mostly spent discussing ideas for the new crossover operator.

### Meeting Notes:

Wayne mentioned a few different ideas:

___Build a Markov model/generator from two parents and use it to generate one or more children___

- Sounds very cool but more complicated than my remaining time allows I think.

___An incremental approach: merge/cross parents (build the children) gene by gene___

- Seems feasible but I'm not sure how to implement it this way while considering all the interactions. Will keep it in mind.

___Merging two parent graphs and cutting off excess___

- Also interesting, I have the same concerns as for the other ideas although to a lesser extent. Will also keep in mind.

We had also considered using graph algorithms to find isomorphic subgraphs and swapping those somehow, but Wayne did some research and found that these algorithms tend to have high complexity and some even recommend using GAs to accomplish their task.

I've spent some time thinking about the problem after building the digraph visualizations and noticed that most of the paths between input (initial) and output proteins were quite short.
Most of them were of the form (initial prot -> gene -> output prot) and some had one additional jump (init prot -> gene 1 -> internal prot -> gene 2 -> output prot).
This still occurred with larger number of genes and initial proteins and more simulation steps.
Because of this, and since shorter paths are likely more reliable, we could find all the input to output protein paths (starting with the ones of shortest length) and look at the gene indices on those paths to decide a split point: if we found clusters of these genes we could split around them.
Progressively longer paths could be used to break ties, but I would probably limit it to the two shortest path lengths mentioned above.

Once the genes are split we could assign initial/input proteins to children to maximize the number of intact input to output protein paths in a Pareto optimality style.

(I have shared this idea with Wayne)

This might even be a crossover method closer to natural biology: apparently plants have genome sections that are always inherited together, i.e., conserved blocks that cannot be crossed during reproduction.
I've been told there are a number of cotton papers on the subject.
(My sources for this are biology PhD students)

### Next Steps:

- Unless I hear anything about the other ideas I might try working out my approach or at least think about how I would implement this.
- Having a meta-level loop to handle generations for us might be useful
- Implementing a metric to evaluate the XO operator will become more important in the (hopefully near) future
