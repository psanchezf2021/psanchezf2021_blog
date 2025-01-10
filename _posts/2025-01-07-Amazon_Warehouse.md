---
layout: post
title: Amazon warehouse
---
This was the most difficult practice for me and is the one I decided to submit later so I don't quite remember some of my thought process from when I started it a month ago.

In summary, I made the tranformation of points from 3D to 2D in order to work only in 2D and then some basic planning, this worked half of the times I ran it, wich at the moment I thought may be due to the transformation. For the state validation I only took into account points, but still drawed squares to see the paths easier. I also pasted the movement function I did for my first practice, as it has the same concept: move to a point.

When I resumed this practice, I started checking where were my mistakes and by drawing everything the robot was doing I figured out it was the planner's fault, wich thanks to adjusting it, made more precise paths. The movement also did not work at first becouse of the angles transformation, so after a lot of tries, it was solved, letting the robot move to each point effectively.

With all this done, all that was left was to take into account the geometry of the robot and of the selves. This was done by checking if the points inside of the rectangles that formed eather of theese were only white. The orientation was also taken into account by using opencv's geometry.

Lastly, I changed the main loop so the robot plans two times and lifts and drops the selves, wich needed an aextra function in order for the robot to look forward when lifting the selves.

[p5.mp4](https://youtu.be/Ewdp_EEa_Lo)
