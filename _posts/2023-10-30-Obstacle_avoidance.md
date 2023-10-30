---
layout: post
title: Obstacle avoidance
---
When I started this practice, I firstly got to know the forces and coordinated systems by adjusting the objectives of the car. First, using the function showLocalTarget(), I drew a test target on the coordinates [1,1].

![target](../images/target.png)

Then by using the function absolute2relative and GUI.map.getNextTarget(), I was able to represent the real targets and take its coordinates. With a simple function comparing the position of the car with that of the target, the actual target would pass to the next one after the car reaches it, this i was able to test by setting the linear speed to a small value for the car to reach the first target (which is in the centre of the road).

With this done i started working on the forces, more specifically, on the attraction force. Firstly, I asjusted it to point directly to the target, but it was, understandably, too big, so I set a maximum and a minimum for the two components of the force.

![carForce](../images/carForce.png)