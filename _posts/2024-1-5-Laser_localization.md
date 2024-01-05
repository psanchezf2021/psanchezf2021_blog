---
layout: post
title: Laser localization
---
To start this exercise I first inspected the first set of examples provided to us in order to make the exercise in our computers. After this I started combinning snippets of code from the examples in my own program and implemented the functionality for the particles not to form on the walls or outside of the map.

After we had available the second and last set of examples we had all the tools necessary to finish the project. I added theese new functions to my program, changing what was necessary for the program to execute properly.

With this done, the "only" thing left was the weight assignment, which came with some complications.

Firstly, I created a function which adapts the getLaserData function but instead of getting the virtual laser from the robot, it gets that of the particles.

```
def get_beam_particle(particle):
    # Get the robot pose in map coordinates as the origin of the laser 
    #start_x, start_y, robot_yaw_map = MAP.worldToMap(particle.pose)
    start_x, start_y, robot_yaw_map = MAP.worldToMap(particle[0], particle[1], particle[2])
    # Convert max laser detection distance from meters to map cells
    laser_distance_cells = MAX_LASER_DISTANCE * MAP.MAP_SCALE
    virtual_laser_xy = []
    for beam_angle in range(180):
        # Actual beam's angle in map coordinates
        # Substract 90º to have the center aligned with the robot
        angle = robot_yaw_map + np.radians(beam_angle) - np.pi/2
        # Compute the theoretical (max) endpoint of the laser
        end_x = start_x + laser_distance_cells * np.cos(angle)
        end_y = start_y + laser_distance_cells * np.sin(angle)
        # Get the laser measurement
        laser_x, laser_y = HAL.virtual_laser_beam(HAL(), start_x, start_y, end_x, end_y)
        virtual_laser_xy.append((laser_x, laser_y, 0))
    world_laser_xy = MAP.mapToWorldArray(np.array(virtual_laser_xy))
    return world_laser_xy
```

Also in this function I implmented the functionality for taking one out of 10 laser beams in order to make the program faster.
I also added an if to not take into account the particles that were ouside the map.

After that, I started working on the assignment of weights, changing the function compute_particle_weights to my needs. Here I also added multiprocessing to my program, using to full capacity all my processors.

```
def compute_particle_weights(laser_robot, particles):
    """ Compute the weight of each particle.
        This function should generate a virtual laser measurement
        for each particle and compute the error (difference)
        between the virtual laser and the actual sensor measurement.
    """
    particles = np.array(particles)
    weights = []
    pool = Pool(8)
    weights = pool.starmap(compute_weights, zip(particles, repeat(laser_robot)))
    return np.array(weights)
```

Then to obtain the weights on each of this processes, I compared each robot's laser beam to each one of its particle counterpart resulting in an error, the desired weight is the inverse of that error.

```
for beam in laser_particle:
    error = abs(abs(beam[0]) - abs(laser_robot[cont][0])) + abs(abs(beam[1]) - abs(laser_robot[cont][1]))
    weight += 1/(error+0.001) 
    cont += 10
```

After all this methods of making the program faster it was still going really slow, to the point where the robot started moving like it wasn't supposed to.

[video_slow_p5.webm](https://github.com/psanchezf2021/robotica_movil_blog/assets/92941198/a3d8c2c7-5345-4fff-a934-d0d7bad4ec8e)

Thaks to the help of some classmates I noticed that the slowness was caused by HAL's virtual_laser_beam, that had to be called each time a virtual laser beam had to be made. This was easily solved by implementing the same function but in my program. This made the program run as smoothly as ever.

[video_final_p5.webm](https://github.com/psanchezf2021/robotica_movil_blog/assets/92941198/53f9d2dc-cbfb-492a-85b0-88390240902f)

It is not perfect and quite random, but i'm sure that with a better pc it would be able to process more particles and more laser beams, making it more precise.
