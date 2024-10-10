---
layout: post
title: Localized vacuum cleaner
---

First i started on representing the map and transforming it to tiles. I decided giving each tile a space of 34x34 since the robot is 35x35 pixels. Firstly, I divided the map in tiles and created an array of tiles, a tile map. Then I checked the map, if the space corresponding to one tile had one black pixel, then the tile is occupied.

With that done I started working on the transformation of coordinates from 3d to 2d, taking measures and making a transformation matrix, but due to the lack of precission of the meassures, the transformation was not accurate, so I asked my classmates for help and they gave me more accurate meassurements. With that the transformation was done.

Then I started working of the movement and I decided to simplify it, just go to x and y coordinates with two proportional controllers, one for linear and the other for angular speed. It is not perfect, but it works.

[video plan.webm](https://github.com/user-attachments/assets/53f431a1-144c-4e37-a486-0878f6a4b041)


[video ejecucion.webm](https://github.com/user-attachments/assets/658ef83e-6ea0-4f39-afdc-6aa0a97778b9)


The video is not complete becouse if i filmed the whole thing it wouldn't be done in time.
