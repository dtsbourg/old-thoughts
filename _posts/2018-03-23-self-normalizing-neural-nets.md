---
layout: post
title: "[NOTES] Self-Normalizing Neural Networks (SELU)"
description: "by G. Klambauer, T. Unterthiner, A. Mayr, and S. Hochreiter"
tags: [ML, deep_learning, notes]
---

[arXiv](https://arxiv.org/abs/1706.02515)

## What?

Proposes a new activation function allowing the robust training of very
deep vanilla neural networks.

## Why?

Most of the successes of Deep Learning have come either from Recurrent (RNN)
or Convolutional (CNN) forms: they are stable through weight-sharing.
Vanilla Neural Networks suffer from training
instabilities mainly due to SGD being unstable after a few layers (vanishing or
exploding gradients).

Some methods have been proposed, notably **batch normalization** [^3] which
brings activations to zero-mean and unit variance, but they are perturbed by
stochastic regularisation methods (e.g. dropout [^2]).

Normalizing activations avoids a bias in the inputs of the following layer.

## How?

An activation function is designed along the following requirements:

1. Negative and Positive values for controlling the mean
2. Saturation regions (zero-gradient) to control the exploding gradient problem
3. Slope larger than 1 to increase the variance if necessary
4. Continuous curve

Derive a mapping between layers that satisfies these requirements. Interestingly
the properties are verified through a computer-aided proof. The starting point
is mix between Exponential Linear Units (ELUs) and Leaky ReLUs.

$$selu(x) = \lambda  \begin{cases} x & \text{ if } x \gt 0 \\ \alpha e^{x} - \alpha & \text{ if } x \le 0 \end{cases}$$

Parameters are obtained by finding a fixed point of the mapping function that
satisfies the normalization requirements. They propose:

$$\alpha = 1.6732632423543772848170429916717$$
$$\lambda = 1.0507009873554804934193349852946$$

They also derive a parametrised dropout which does not suffer from the same issues
as regular dropout as it is designed to preserve zero-mean and unit-variance in
the layer's activations.

![SELU]({% asset_path selu.png %})
*Figure 1: SELU activation function*


## Evaluation

* 121 Tasks from [UCI dataset](https://archive.ics.uci.edu/ml/datasets.html)
* Drug discovery task
* Astronomy task

![Res]({% asset_path snn_accuracies.png %})
*Figure 2: Image from Klambauer et al, https://arxiv.org/abs/1706.02515 [license http://arxiv.org/licenses/nonexclusive-distrib/1.0/]*

Compare against many baselines: Batch Norm, Layer Norm, Weight Norm, Highway, ResNet.

## Comments

* Interesting use of a computer generated proof to give bounds on the variance
when weights don't satisfy the zero-mean, unit-variance property
* Very smooth accuracy even for very deep networks (see Fig. 2)
* Sepp Hochreiter [^1]
* Makes batchnorm obsolete, which means big training speedup

## Questions

* Evaluated with SGD. How does it behave with e.g. Adam?
* Evaluated with small learning rates, can we be more agressive in learning?
* Comparison between Spectral Normalization [^4] and SNN for mode collapse in GANs.

## Resources
#### Code

* [Tensorflow Implementation](https://github.com/bioinf-jku/SNNs)
* [PyTorch Implementation](https://github.com/dannysdeng/selu)
* [Notebook](https://gist.github.com/Drakensberge/2d8a4e8f9ff48e095e12a892b08598ec#file-distribution-ipynb)

#### Discussion

* [/r/MachineLearning](https://www.reddit.com/r/MachineLearning/comments/6g5tg1/r_selfnormalizing_neural_networks_improved_elu/)
* [hackernews](https://news.ycombinator.com/item?id=14527686)
* [Shortscience](http://www.shortscience.org/paper?bibtexKey=journals/corr/1706.02515)

## References

[^1]: [*Long Short-Term Memory*. Sepp Hochreiter and Jürgen Schmidhuber.  Neural Comput. 9, 8 (November 1997), 1735-1780](https://dl.acm.org/citation.cfm?id=1246450)
[^2]: [*Dropout: A Simple Way to Prevent Neural Networks from Overfitting*, Nitish Srivastava, Geoffrey Hinton, Alex Krizhevsky, Ilya Sutskever, Ruslan Salakhutdinov; 15(Jun):1929−1958, 2014.](http://jmlr.org/papers/v15/srivastava14a.html)
[^3]: [*Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift*, Sergey Ioffe, Christian Szegedy](https://arxiv.org/abs/1502.03167)
[^4]: [*Spectral Normalization for Generative Adversarial Networks*, Takeru Miyato, Toshiki Kataoka, Masanori Koyama, Yuichi Yoshida](https://openreview.net/forum?id=B1QRgziT-)
