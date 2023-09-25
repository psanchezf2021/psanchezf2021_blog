---
layout: post
title: Simple vacuum
---
# Basic vacuum cleanter
This is the first practical excersise of the subject, so first i had to
familiarize with unibotics and the tools we would be using. So firstly, i added
to the code the lasser functionality and tried some simple movements like moving
forward.

```
from GUI import GUI
from HAL import HAL
import math

def parse_laser_data(laser_data):
    laser = []
    for i in range(180):
        dist = laser_data.values[i]
        angle = math.radians(i)
        laser += [(dist, angle)]
    return laser

while True:
    HAL.setV(1)
```

Then I started working with the different states. I was hessitant between making
them in different functions or using ifs to switch cases in the while True, but
functions looked more convinient for me. I started with the most basic state:
going forward.

```
def state_forward(laser):
    HAL.setV(1)

while True:
    laser_data = HAL.getLaserData()
    laser = parse_laser_data(laser_data)
    state_forward(laser)
```

After that i made a function to check the distance of the laser and another
one for moving backwards (where the state forward will jump to when an obstacle
is detected).

```
def distance_check(laser):
    for distance, _ in (laser):
        if(distance < 0.4):
            return True
    return False

def state_forward(laser):
    HAL.setV(1)
    if(distance_check(laser)):
        state_back()
    
def state_back():
    HAL.setV(-1)
```

After I checked the detection was working I added the state turn, but it didn't
make much sense without first limiting the time of state_backwards so it stops
at a safe distance. So that is what I did, using time.time() by marking the
beginning of the motion and comparing it with the actual time, I limited
state_back and state_turn.

```
def state_back():
    HAL.setV(-1)
    
    start = time.time()
    while True:
        now = time.time()
        elapsed_time = now-start
        if(elapsed_time > 2):
            break
    HAL.setV(0)
    state_turn()

def state_turn():
    HAL.setW(1)
    
    start = time.time()
    while True:
        now = time.time()
        elapsed_time = now-start
        if(elapsed_time > 3-(random.random()*2)):
            break
    HAL.setW(0)
```

Next I added randomness to its direction using random.random().

```
def state_turn():
    if(random.random() <= 0.5):
        HAL.setW(1)
    else:
        HAL.setW(-1)
```