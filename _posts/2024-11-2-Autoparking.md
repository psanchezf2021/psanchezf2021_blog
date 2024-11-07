---
layout: post
title: Autoparking
---
This exercise consists on three phases: aligning with the parked cars, find the spot to park and park, so I started by the first one. At first, I made it work by comparing the mean of the cosene of all the meassurements of the upper and lower half of the right laser. This posed a problem, when no cars were present at one of the halves, the alignement failed. Becouse of this, I changed to calculate the slope of the line that the cars formed by parsing the laser meassurements and using the function polyfit. With the slope I could calculate the angle and with that I could compare the angle to make a simple proportional controller. But the car was still far away, so I recycled the cosene method to calculate the overall distance to all of the cars so when it has alligned, it turns to get closer to the cars and then it alligns again.

After that I worked on the spot detection. Firstly, I made it so if it detected any obstacle in a range on its side, that is not a free spot, and if it found one, it would advance until it detected another car to then iniciate the parking action. This again, didn't take into acount that it could be no car in front of the free spot, so I changed the range detection to a zone of the back laser. But then I was informed that this was a bad way of solving the finding of the spot, so I changed it again so, by parsing the meassurements of the right laser, an imaginary rectangle was formed with a simple if, so if any meassurements were inside that rectangle, the free spot had not be found yet. With that I added a counter to let the car advance a little to get into the right position to park.

Finally, the parking, it was the simpler part to do. Firstly, before the car starts manouvering, I save the correct orientation to use it later. Now, the car turns as it reverses slowly, until it has turned 45º, then, it turns another 45º to the oposite direction until the original orientation has been met. If, in the last part of the manouver, the car finds an obstacle too close, then it starts going forward in the same direction until, again, the original orientation has been met.

This is the result:

[p3.webm](https://github.com/user-attachments/assets/99a413fe-a5a6-4e17-946b-91420173109c)
