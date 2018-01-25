---
layout: post
title: "Pose Sketching for the Control of a Humanoid Robot - Part 1"
description: "Motivation: Controlling robots is hard."
tags: [robot, project, epfl]
---

## Introduction

In this series of posts, I will be writing up about some work done in the
context of a semester project counting for my degree from [EPFL](https://epfl.ch).
This is meant more as a record than an in-depth tutorial, but don't hesitate to
drop me a line if you would like to see more details.
This work was done under supervision by [Sylvain Calinon](https://calinon.ch),
senior researcher in the Robot Learning & Interaction Group at [Idiap Research Institute](https://idiap.ch)
in Martigny, Switzerland.

The main focus of the project was to investigate new ways of controlling
high degree of freedom robots, with an application to the Humanoid robot Baxter.

![baxter](https://www.edinburgh-robotics.org/sites/default/files/baxter-robot.jpg)
*Figure 1: The Baxter robot (source: edinburgh-robotics.org)*


## Controlling robots is hard

As robots further enter our everyday lives, increasing our interactions
with them, we need better ways to cooperate with or command them. In
industrial settings, where the large majority of robots live at the
moment, the design of operational tasks and their control is yielded to a
dedicated technician or engineer, who often needs extensive experience
in the use of a proprietary interface corresponding to the robot in use.

Personal or service robots, which have started to enter our homes, still
only enjoy rudimentary control : they usually sacrifice completeness for
simplicity as users are usually not well versed in robot control.

![control panel](https://www.techtransfer.com/wp-content/uploads/image007.jpg)
*Figure 2: An industrial robot control panel from techtransfer*

In recent years we have seen the arrival of a variety of new Augmented
Reality platforms, such as Google's Tango [^1] (now ARCore [^2]) or Apple's ARKit [^3].
Thanks to more powerful embedded hardware, companies
have started to provide libraries which easily allow visual tracking,
rendering in 3D space, and even interaction with physical planes. This
presents an elegant framework for interacting with complex systems such
as robots, as they take advantage of context to display information.
They also could provide an intuitive way of manipulating robots which
have a high number of degrees of freedom, such as the Baxter robot, in
the space in which they operate normally, provide direct visual feedback
rather than a collection of joysticks or buttons for every DOF.

![ARKIT](https://photos5.appleinsider.com/gallery/22874-28279-170919-Strava-l.jpg)
*Figure 3: ARKit in action*


## Towards an intuitive control model

One of the simplest ways of expressing complex shapes has long been to
draw. Particularly in the case of human poses, which can be difficult to
describe, are intuitively represented with stick figures.
The original aim of this project was to allow a user to draw a stick
pose on an Augmented Reality interface which would map to a robot pose.
This would allow for intuitive control of the robot’s many DOFs by
providing direct, contextual and visible feedback to the user
controlling it.

To achieve this we started by investigating partial control of the
robot’s joints in a Matlab simulation, developing an interactive
simulation which allows for this type of control. This aspect will be
detailed in Part 2 (*coming soon*).

An alternative approach to this control is to give and track commands directly
in the image space (on the screen). This idea led to the investigation
of the visual servoing problem, as detailed in Part 3 (*coming soon*).
This led us to keep this method of control for a final application in
which the user could click on the screen of an Android phone, and have
the robot move to this selected point.

![Interaction Model]({% asset_path setting.png %})
*Figure 4: Proposed interaction model*

This should converge towards a unified control model described in Fig. 4.
The user, helped by feedback from an Augmented Reality overlay, can click
on the screen to make the robot's arm move from position 1 to 2, while having
the freedom to move around, edit his selection, and virtually interact with the
separate degrees of freedom of the robot.



---
[^1]: https://developers.google.com/tango
[^2]: https://github.com/google-ar/arcore-android-sdk
[^3]: https://developer.apple.com/arkit/
