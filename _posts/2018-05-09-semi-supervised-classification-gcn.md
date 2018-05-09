---
layout: post
title: "[NOTES] Semi-Supervised Classification with Graph Convolutional Networks"
description: "by T. Kipf, M. Welling"
tags: [ml, deeplearning, notes, graph]
---

[OpenReview (ICLR '17)](https://openreview.net/forum?id=SJU4ayYgl)

## What?

Classifying nodes in a graph where labels are only available for a small subset of nodes.

## Why?

Usually smoothing label information over graphs is done via graph-based regularization (see [^4] [^5] [^6]). This can
be an issue as it assumes that connected nodes are likely to share the same label, which is
not always the case. This methods encodes actual node similarity w.r.t to the vertex features.

## How?

Proposes learning a feature map $$f(X,A)$$, as a function of both the labels and the adjacency, so
as to encode the node similarity and graph structure at the same time. These features are then
optimised as loss terms, so the whole process is learned end-to-end.

This feature map is learned using Graph Convolutional Networks. The authors
provide a derivation of the propagation model through first-order approximation
of localized spatial filters [^1] [^7]. The main take away is that $$k$$ applications of a linear filter result in
convolving the $$k^{th}$$-order neighbourhood, as if is was a filter of degree $$k$$. This is what makes the method tractable.

The authors also provide the propagation model as a derivation of the Weisfeiler-Lehman algorithm [^8] in Appendix A.

## Evaluation

* Document classification in citation networks with low label rates: [Cora](https://relational.fit.cvut.cz/dataset/CORA), [PubMed](https://catalog.data.gov/dataset/pubmed), [Citeseer](http://csxstatic.ist.psu.edu/about/data)
* Semi-supervised entity classification in bipartite graphs extracted from knowledge graphs: [NELL](http://rtw.ml.cmu.edu/rtw/kbbrowser/)
* Random graphs

The authors achieve high classification accuracies for all the proposed tasks, and compare different propagation models.

## Comments

* Graph-based methods are a very exciting domain, with applications in domains like network analysis,
power-grid balancing, computer graphics, relational networks (social, citation, political, ...), video tracking, ...
Seeing that the semi-supervised setting is natural is very encouraging for applications in these domains (note that some limitations
were presented in F.Huszar's blog post, linked below)
* It is a powerful formulation for graphs where either the structure of the graph or the nodes have partial or missing information: inference can still be run.
* Can be extended to do graph-level (or subgraph) classification with a pooling layer (such as [^2] [^3])
* Seems like there were quite a few memory issues in implementation

## Questions

* How to handle mini-batches? Since the Adjacency matrix is needed, information about k-neighbours is needed for each iteration.
    * [EDIT] The authors have [pointed out](https://twitter.com/thomaskipf/status/994210684761264128) that this issue has been addressed in frameworks like GraphSAGE [^10]
* The authors note that the method does not naturally support directed graphs, but propose to represent the original graph as a bipartite graph to model directed edges and edge features.
* The semi-supervised setting could be better defined, taking cues from the _Realistic Evaluation of Semi-Supervised Learning Algorithms_ by Oliver et al. [^9].
    * What are the class distributions for unlabeled data? (Only label sparsity seems to be reported)
    * How does the proportion of unlabeled data influence the classification quality (and the label propagation model)?
    * How were the different sets sampled (1k labeled examples for test)?


## Resources
#### Code

* [Tensorflow Implementation](https://github.com/tkipf/gcn)

#### Discussion

* [/r/MachineLearning](https://www.reddit.com/r/MachineLearning/comments/52d8ms/160902907_semisupervised_classification_with/)
* [Ferenc Huszar post](http://www.inference.vc/how-powerful-are-graph-convolutions-review-of-kipf-welling-2016-2/)
* [Thomas Kipf (author) post](https://tkipf.github.io/graph-convolutional-networks/)
* [/r/MachineLearning discussion of @fhuszar's post](https://www.reddit.com/r/MachineLearning/comments/52klq2/how_powerful_are_these_graph_convolutional/)
* [HN Discussion](https://news.ycombinator.com/item?id=12619694)
* [Discussion on Twitter with the Thomas Kipf, addressing some of the comments highlighted here](https://twitter.com/thomaskipf/status/994210684761264128)

## References

[^1]: *Convolutional Neural Networks on Graphs with Fast Localized Spectral Filtering*, by Michaël Defferrard, Xavier Bresson, Pierre Vandergheynst [link](https://arxiv.org/abs/1606.09375)
[^2]: *Gated Graph Sequence Neural Networks*, by Yujia Li et al. [link](https://arxiv.org/abs/1511.05493)
[^3]: *Convolutional Networks on Graphs for Learning Molecular Fingerprints*, by David Duvenaud et al. [link](https://arxiv.org/abs/1509.09292)
[^4]: *Learning with local and global consistency*, by Zhou et al. [link](https://dl.acm.org/citation.cfm?id=2981386)
[^5]: *Manifold regularization: A geometric framework for learning from labeled and unlabeled examples*, by Belkin et al. [link](https://dl.acm.org/citation.cfm?id=1248632)
[^6]: *Deep learning via semi-supervised embedding*, by Weston et al. [link](https://dl.acm.org/citation.cfm?id=1390303)
[^7]: *Wavelets on graphs via spectral graph theory*, by Hammond et al. [link](https://arxiv.org/abs/0912.3848)
[^8]: *On the Combinatorial Power of the Weisfeiler-Lehman Algorithm*, by Marten Fürer [link](https://arxiv.org/abs/1704.01023)
[^9]: *Realistic Evaluation of Semi-Supervised Learning Algorithms*, by Oliver et al. [link](https://arxiv.org/abs/1804.09170)
[^10]: *Inductive Representation Learning on Large Graphs*, by Hamilton et al. [link](https://arxiv.org/abs/1706.02216)
