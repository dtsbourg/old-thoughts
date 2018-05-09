---
layout: post
title: "Starry Night"
description: "A primer on style transfer"
tags: [ml, intro]
---

What makes *Starry Night* look like a van Gogh painting ? Is it the colours ?
Is the brush stroke ? Is it the subject ? Somehow when we see this painting we associate its style
to its author. If the style of the painting can be thought of as an independent component from the subject
it represents, would it be possible to apply the style of *Starry Night* to another painting of picture ?

![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Van_Gogh_-_Starry_Night_-_Google_Art_Project.jpg/1280px-Van_Gogh_-_Starry_Night_-_Google_Art_Project.jpg)

In A Neural Algorithm of Artistic Style __[1]__, published in 2015 by Gatys, Ecker & Bethge, the authors try
to address this question using recent advancements in Artificial Neural Networks. They were indeed able to
separate content and style, allowing them to apply style to arbitrary content. Their work gave rise to
beautiful pieces of work, some apps like [deepart.io](https://deepart.io/), [Prisma](https://prisma-ai.com/) or [Pikazo](http://www.pikazoapp.com/).

![](https://jvns.ca/images/neural-style.png)

So how does this work ? The premise is the following : given an image, we want an algorithm that can transfer
the style of a second image onto the first (an example is shown with *Starry Night* in the picture above, whose
style is transferred to a picture of the university of Tubingen in Germany).

When Machine Learning is applied to images, we don't reason in terms of pure images : for a computer,
as for our network, they are just a set of numbers (the pixel values). Of course this means losing a
lot of information about the structure of the image : when you see a photo of a cat, you don't count the
individual pixels to recognise a cat. What you do is look for features. These are characteristics of what
you are looking at that help you identify it : is it cute ? is it furry ? does it have a nose ? does it
have whiskers ? ...

![](https://www.petdrugsonline.co.uk/images/page-headers/cats-master-header)

Thankfully, researchers have already worked on this problem. A Convolutional Neural Network extracts
__features__ from an image. It does so in an abstract manner, looking for lines or shapes. These are
the elementary building blocks that you analyse to determine if the thing you're looking at has a nose or whiskers.

![](https://i.stack.imgur.com/Hl2H6.png)

CNNs are a form of Deep Learning network, meaning they have many different layers. At each layer, the representation is a bit different, each level being more or less abstract as shown in the figure above. In this paper they used a pre-existing CNN called VGG-19 developed at Oxford's Visual Geometry Group __[2]__.

Okay so we've got intermediate representations of images, encoding more or less abstract features from it. How does that help us "transfer style". Well our goal here is to find a way to separate these features into two groups : __content__ and __style__.

Let's start with the simpler one : content. As we mentioned earlier, some of the features naturally encode the structure of the image : lines, shapes, ... This is our content !

How about style ? Well this is the paper's main contribution. They defined style as correlations, relatedness, between features. In other words, if you have some feature "blue" and some feature "swirly", they are highly correlated in Starry Night __[3]__. Formally this is computed as the Gramian Matrix in the feature space, a common measure of correlation __[4]__.

We have now got all the pieces to the puzzle ! We extract structure from the image, and style from the painting. When similar features are matched between the image and the painting (for example a "blue" part), the style from the painting is applied to the image, so that the correlations match (making the "blue" part "swirly"). The result is a transformed version of the original image which looks a lot like the painting, but retaining its structure.

I'll leave you with some examples taken from the paper and some cool flower dinosaurs by Chris Rodley __[5]__ :

![](https://3.bp.blogspot.com/-jYGbp0Ow1Cc/WA6oWw63F7I/AAAAAAAABWc/8_E5A1dbPP4xeo1GuIGTsYvG6TuXIfmoQCLcB/s1600/image06.png)

![](http://kottke.org/plus/misc/images/chris-rodley-01.jpg)

Have you generated some cool style transferred art ? Share it with me on [twitter](https://twitter.com/dtsbourg) !

---

### Sources

* [1] [https://arxiv.org/abs/1508.06576](https://arxiv.org/abs/1508.06576)
* [2] [http://www.robots.ox.ac.uk/~vgg/research/very_deep/](http://www.robots.ox.ac.uk/~vgg/research/very_deep/)
* [3] [https://twitter.com/mewo2/status/830875447504277506](https://twitter.com/mewo2/status/830875447504277506)
* [4] [https://en.wikipedia.org/wiki/Gramian_matrix](https://twitter.com/mewo2/status/830875447504277506)
* [5] [https://chrisrodley.com/](https://chrisrodley.com/)
