---
layout: post
title: Plotting Interactions with a DiGraph
---

As mentioned in the previous meeting post, digraphs seem well suited to mapping out the interactions in the GRN simulation.

I've used the NetworkX DiGraph object to create edges for bind and produce events and I've coloured nodes so it's easier to grasp the meaning of relationships:

- Purple is used for initial proteins
- Blue is used for internal proteins and genes  
- Green is used for output proteins

The gene nodes are displaying their binding sequence since the edges towards protein imply their production sequence.

The layout I'm using for drawing the graph might look oddly triangular and create longer edges but it provides better spacing between nodes improving readability.

For some reasons I can't get the fitness to print in a fixed location on the figure

Here are some examples:

<img src="{{ site.baseurl }}/images/fit_10.png"/>
<img src="{{ site.baseurl }}/images/Figure_5.png"/>
<img src="{{ site.baseurl }}/images/Figure_6.png"/>
<img src="{{ site.baseurl }}/images/fit_5.png"/>
