---
layout: post
title: "\"Scientists Discover That the Brain Can Process Clickbait in 11 Dimensions !\""
description: "An example of approximative vulgarization."
tags: [brain, neuroscience, epfl]
---

So a few days ago, I was scrolling Facebook and saw an article by a popular scientific vulgarization page, titled Scientists Discover That Our Brains Can Process the World in 11 Dimensions __[3]__. Obviously, this sounded a bit clickbaity, but I was revising for a computational neuroscience class and the paper they mentioned was written at my University, EPFL (in Lausanne, Switzerland). So what better to do than to actually read the paper (which apparently the author did not do) ?

*__tldr;__ The article is really bad and misleading, the brain does not encode 11 dimensions. What the paper is about is the ability to find the depth and distribution of millions of subnetworks of neurons within the brain.*

The article starts off with an impressive claim :

> "What they’ve discovered is that the brain is full of multi-dimensional geometrical structures operating in as many as 11 dimensions.".

This idea of "dimensions" are geometrical dimensions is replayed throughout the article. However, right in the introduction of the paper __[2]__, the authors explain what they really mean by "dimensions" :

> Networks are often analyzed in terms of groups of nodes that are all-to-all connected, known as cliques. The number of neurons in a clique determines its size, or more formally, its dimension.

Evidently, these do not relate or encode some set of hidden geometrical dimensions that the brain is able to process and that we are not able to perceive.

![A clique as defined by the paper](https://www.frontiersin.org/files/Articles/266051/fncom-11-00048-HTML-r3/image_m/fncom-11-00048-g001.jpg)
*__Figure 1 :__ How to find a clique of neurons as shown in the relevant paper [2]*

So now onto what the paper actually talks about ... We know that in the brain, neurons connect together and send each other impulses (spikes) based on stimuli or general network activity (this can be caused by trying to recall a memory, recognizing a visual stimulus, processing logic, etc ...). This connection behavior can be modeled as a graph : each neuron is a node, who can be connected to an arbitrary number of other nodes. Information is transmitted through this graph to accomplish any number of tasks mentioned earlier.

What Henry Markram's team was able to do is use topological arguments to find the depth and distribution of millions of these graphs in the brain. This is quite impressive because it is very difficult to isolate logical groups of neurons within this dense network. Yet using this mathematical framework on the graphs they can achieve this isolation mathematically rather than physiologically. They are also able to model gaps, i.e. groups of neurons that don't communicate together, hence revealing the larger structure as well ! They can even compute their depth, which is thought to be an important characteristic for their ability to encode more abstract information : the deeper the more abstract features they can represent, similarly to Artificial Neural Networks (ANN) __[1, 4, 5]__.

![CNN features](https://i.stack.imgur.com/Hl2H6.png)
*__Figure 2 :__ ANNs abstract away the presented information into common features (you can see this in the bottom layer, which are simply lines)*

Once again we had here an example of shaky scientific vulgarization. Though it is extremely important that scientific research is communicated to the masses, it is important to do so with scientific rigor and method: don't interpret what you don't fully understand, don't exaggerate facts and state the hypotheses within which you make these claims.

It is crucial that people be interested in scientific advances, but it is just as important that they are not mislead. This is especially true nowadays, where myths about many domains (from AI to climate change) are widespread and could do with a little measure and a sprinkle of extra facts ...

---
<br />
**Disclaimer** *I'm not claiming to be an expert on the subject, just a student, and I only want to express my frustration when I see approximate renditions of cool scientific advancements. Nevertheless I'm happy to answer your questions about neuroscience to the best of my abilities or spark a discussion about how science is communicated to the public. Do you have examples of good (or bad) scientific communications ? Feel free to share them with me on [twitter](twitter.com/dtsbourg)*

---

### Sources

* [1] [https://blog.keras.io/how-convolutional-neural-networks-see-the-world.html](https://blog.keras.io/how-convolutional-neural-networks-see-the-world.html)
* [2] [http://journal.frontiersin.org/article/10.3389/fncom.2017.00048/full](http://journal.frontiersin.org/article/10.3389/fncom.2017.00048/full)
* [3] [https://futurism.com/scientists-discover-that-our-brains-can-process-the-world-in-11-dimensions/](https://futurism.com/scientists-discover-that-our-brains-can-process-the-world-in-11-dimensions/)
* [4] [http://kvfrans.com/visualizing-features-from-a-convolutional-neural-network/](http://kvfrans.com/visualizing-features-from-a-convolutional-neural-network/)
* [5] [https://cs231n.github.io/understanding-cnn/](https://cs231n.github.io/understanding-cnn/)

---
<br />
