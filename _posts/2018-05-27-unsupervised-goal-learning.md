---
layout: post
title: "[NOTES] Unsupervised Learning of Goal Spaces for Intrinsically Motivated Goal Exploration"
description: "by A. Péré, S. Forestier, O. Sigaud and P.-Y. Oudeyer"
tags: [ml, deep_learning, notes, reinforcementlearning]
---

[Open Review](https://openreview.net/forum?id=S1DWPP1A-)

## What?

Instead of engineering a goal space, proposes to learn an unsupervised latent representation
of the goal space using deep representation learning.

## Why?

This work is an extension of the Intrinsically Motivated Exploration by Pierre-Yves Oudeyer and ...
Usually the goal space in engineered manually, which is not always possible, for example in high
dimensional spaces where the achievable space is ...

## How?

Using deep representation learning to embed the environment in a latent space.
KL-Coverage to evaluate the quality of the sample latent space.


## Evaluation

ArmBall

## Comments

* Interesting approach to learning a latent goal space
* Could open the door to the use of GANs to generate goals from the latent space
* A bit unclear what the other baselines of goal space learning are and how well they perform
* Needs some more complex examples as noted in the conclusion

## Questions

*

## Resources
#### Code

* [Implementation](https://github.com/flowersteam/Unsupervised_Goal_Space_Learning)

## References

[^1]: Intrinsically motivated exploration as efficient active learning in unknown and unprepared spaces, by Pierre-Yves Oudeyer and Adrien Baranès [link](http://www.pyoudeyer.com/OudeyerBaranesEpirob08.pdf) (Exploration as active learning, exploration vs exploitation trade-off)
[^2]:
[^3]:
