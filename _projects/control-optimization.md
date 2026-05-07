---
layout: page
title: Optimal Control of Quadcopters and Robonauts
description: Real-time control systems for a simulated quadcopter and two-wheeled robot using state-space dynamics, LQR, and hill-climbing optimization.
img: assets/img/quadcopter.gif
importance: 4
category: fun
---

These two projects were part of the Control Systems and Optimization course as part of my undergraduate studies in aerospace engineering at the University of Illinois at Urbana-Champaign. Both projects involved creating a real-time control system using a state-space representation of the dynamics of the system. To delve into optimal control we also implemented a linear-quadratic regulator (LQR). The weights and parameters of this system were up to us to optimize. The environment in which we tested our control systems was a simulated, limited-physics, with fixed time-step simulation setup in MATLAB.

The first project was to bring a quadcopter from any (within reason) orientation to a fixed point in space, the reference location. We then had to minimize the error with respect to the reference location, and the time it took the system to arrive at this equilibrium. An example of the quadcopter in action can be seen in the GIF below.

{% include figure.liquid loading="eager" path="assets/img/quadcopter.gif" title="Quadcopter control" class="img-fluid rounded z-depth-1" %}

In the final project of the year we were tasked with guiding a "robo-naut" in a race on a twisting and turning track. The robot had to be able to navigate the track without going out of bounds, all the while keeping itself upright (it was on two wheels) in the least amount of time. The GIF below shows the robot navigating the track.

{% include figure.liquid loading="eager" path="assets/img/robonaut.gif" title="Robonaut race" class="img-fluid rounded z-depth-1" %}

In order to train the weights for this system I used a hill-climbing algorithm, an iterative approach at finding the (local) optimum of a function. To avoid local optima, or at least hope for a result close to the global optimum, I used a random restart approach. This involved running the hill-climbing algorithm multiple times, each time with a different set of initial weights. The best result of all the runs was then chosen as the final result. A simple diagram illustrating the potential advantage of this approach can be seen below.

{% include figure.liquid loading="eager" path="assets/img/hill_climbing.png" title="Hill climbing algorithm" class="img-fluid rounded z-depth-1" %}
