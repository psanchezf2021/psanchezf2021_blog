---
layout: post
title: Marker visual localization
---

For this practice, firstly, I started learning how apriltags worked, when I was able to take the id of each tag, I started working on the main algorithm.

At first, I thought of doing pnp of the coordinates of the tags already transformed to their real coordinates, by first setting the corners and rotating and translating them so their coordinates match with the 3d world. This was not quite right because I had to then rotate both X and Z axis -90º for them to match to the 3d world. Then, using the pnp method IPPE_SQUARE I should had a matrix that gave me the rotation and tranlation of the robot, but something was not working as intended. After checking and checking, I decided to change the algorithm and do it as I heard it should be done, step by step using transformed matrices (you can still see snippets of commented code of this first iteration I used to help me on the making of the second one).

Thankfully, I could use most of the code I had already done. First I set the coordinates but changing it to be as the documentation of the method solvePnP said (witch could be one of the things that made my previous iteration not work), with its results I made a 4x4 matrix witch included the rotation and translation. Then I rotated that matrix -90º on the axis X and Z, and then, by checking the paper, I notice I had to also invert the matrix. Wil¡th all of this I had the matrix tagToCamera finished. For worldToTag I made a 4x4 matrix with the translation and rotation I used before for the corners of the tags. By multiplying this two matrices I had worldToCamera, witch I could use to infer the yaw and X and Y coordinates of the robot.

Finally, for the estimation when tags are not seen, I save the last estimated position of the robot and add the change in position meassured by the odometry. And, for the movement, the robots moves in circles, but if its changed to any other kind of movement it should estimate its position as normal.
