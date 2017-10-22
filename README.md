# Term-3-P1
Path Planning

I use the codes from the walk through video as the basis to start with. I then continue the work by building the function of lane changing when safe to do so. Below is the step I have taken to accomplish this project.

## Make the car move without exceeding the max speed/jerk/acceleration
The first step is to make the car move. Frenet coordinate is very helpful in this case as it's easy to specify where the car is relative to the lane and how far it has gone through the lane. As instructed in the tutorial video, I first created five basis path points. The first two are from the previous path (line 342-363) and the next three are created to space 30 meter apart from each other (line 367-377). Spline library is then used to fill up the points between those five basis points (line 401-433) as it does a good job in preventing the jerk. The number of the points are calculated so that the speed is not over the limit (49.5 mph) (line 416). 

## Monitor the cars around and change the lane when safe to do so
I use the sensor fusion vector for the information of the cars around. I first check if there is a car in front of our lane and close enough (30m) to trigger an action. If it is, then the car takes a look at all the three lanes to see if it can make a safe lane change by projecting the other cars' position given its speed. 30m is considered as the safe range so that if there is any car within 30m in front of or behind our car, the lane change is considered not safe. Three boolean variables, left_lane/middle_lane/right_lane are used to store that judgement. Then depending on where our car is, the car will make the decision to shift to the lane that it deems to be safe. The car, however, is not able to jump from left lane to right lane, if there is another car in the middle lane. If the car finds no lane change is appropriate, then it will deaccelerate slowly to follow the car in front of it. 

## Result
The car is able to drive smoothly with no speed limit or jerk violation. It detects the car in front of it and makes the lane change decision by incorporating the movements of other cars around it. When safe to do so, the car smoothly shift to the empty lane. In my test, the car has driven safely over 5 miles without incident.
