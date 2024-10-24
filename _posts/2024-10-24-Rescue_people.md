---
layout: post
title: Rescue people
---

Firstly I started by converting the GPS locations to UTM. The ressults were the safety boat located at 430492 East 4459162 North and the survivors at 430532 East 4459132 North. By substracting the boat coordinates (origin) to the survivor coordinates (target) i obtained the position of the survivors on the simulated map: 40, -30.

Then I started working on the algorithm of the spiral. At first, I thought about using the mixed control, with a constant z value and speed imput on the x and y axis, but then, as i was implementing it and thinking about a simpler position control, the latter seemed much easier. At the end the algorithm works this way: with a position control, it draws squares from corner to corner at a distance form the origin point (the survivor coordinates), then when it has done a lap, that distance is increased, maken the squares bigger each time.

For the face detection I basically used the function detectMultiscale for opencv. The problem was, it does not detect faces that are not straight. For the detection to work I rotated each frame 12 times with a rotation matrix. But it was not detecting the faces correctly yet, so I started changing the parameters of detectMultiscale in order for the 6 faces to be counted and their locations saved.
