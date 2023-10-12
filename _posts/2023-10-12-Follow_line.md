---
layout: post
title: Follow line
---
For this second practice I started searching how to do the image detection and the filtering of the line. Thanks to our sources I was able to apply a mask to the image in order to only select the red line and sow it in the display.

![mask](../images/masked.png)

After being able to show the camera image I started thinking about selecting the line pixel by pixel in order to find the center, but then when looking throught our sources I saw the moments opencv function and I choose to use it. By searching through various webs I discovered a snippet of code to show the centroid of the line and after adapting  some parts of the code this was the result:

![centroid](../images/centroid.png)

Whith this done I started working on the controller. 