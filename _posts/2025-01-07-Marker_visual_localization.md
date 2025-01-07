---
layout: post
title: Marker visual localization
---

For this practice, firstly, I started learning how apriltags worked, when I was able to take the id of each tag, I started working on the main algorithm.

At first, I thought of doing pnp of the coordinates of the tags already transformed to their real coordinates, by first setting the corners and rotating and translating them so their coordinates match with the 3d world. This was not quite right because I had to then rotate both X and Z axis -90º for them to match to the 3d world. With this I should had a matrix that gave me the rotation and tranlation of the robot, but something was not working as intended. After checking and checking, I decided to change the algorithm and do it as I heard it should be done, step by step using transformed matrices.
