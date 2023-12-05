---
layout: post
title: Global navigation
---
To start de development of this practice, I made a simple code to draw a path directly from the car to the selected target using the function showpath.

![path](https://github.com/psanchezf2021/robotica_movil_blog/assets/92941198/8eb2accc-e1f1-46cf-9e8a-8cf0674e011e)

With this done I used the code given to us to draw a simple gradient in order to get to know the necessary functions to use. Then, I started working on the real gradient. By taking into acount the instructions given to us, I used a priority queue to take new points and draw its surroundings. The gradient is only done until the car is found and with a series of ifs, the possible points to expand are discarded deppending on its conditions. When one of the points is an obstacle, it is added to an obstacle list, this will be important for the next step. At this point the making of the gradient is really slow, so I will need to work on that.

With the obstacle list, the obstacle pixels' cost are increased by 1000, and its surrounding pixels by 10, to avoid the car to go too close to the walls. Then the gradient is drawn.

After the gradient is done, I started working on the navigation, for the car to follow the nearest path, it searches the lowest cost pixel in an square of 10x10 pixels. This pixel is set as the atraction point for the car in each loop. Lastly, the linear sleep is set to get slower as it comes closer to the point and the angular speed is set for the car to orientate towards the said point. After hours of the car not going were it should, I added the absolute2relative function from the previous practice to make target_x and target_y and then set the linear speed to target_x and the angular speed to target_y. As the car collisioned with the corners, I increased the pixels who's cost would be incremented by 10.

This is the result:

[video_p4.webm](https://github.com/psanchezf2021/robotica_movil_blog/assets/92941198/48e8eb6f-d42c-421b-ba6e-a27a28c1d52d)

Notice that I wasn't able to make the gradient be drawn faster, not mattering what I tried, and that the path is not drawn in the map, this is because I lacked the time but also because it seemed unnecesary for the program to work.
