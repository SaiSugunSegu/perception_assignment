#  Differential Drive Kinematic Model

## Intro to Differential Drive
The differential drive consists of 2 drive wheels
mounted on a common axis, and each wheel can independently be driven either forward or backward.

While we can vary the velocity of each wheel, for the robot to perform the rolling motion, the robot
must rotate about a point that lies along its common left and right wheel axis. The point that the
robot rotates about is known as the ICC - Instantaneous Center of Curvature 

<p align="center">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a46c2754-f9a3-4eb6-962c-e786a436c326">
</p>

By varying the velocities of the two wheels, we can vary the trajectories that the robot takes.
Because the rate of rotation ω about the ICC must be the same for both wheels. We can write the following equations:

  - $w * (R + {L/2}) = Vr$
  - $w * (R - {L/2}) = Vl$

where l is the distance between the centers of the two wheels, Vr, and Vl are the right and left wheel
velocities along the ground, and R is the signed distance from the ICC to the midpoint between the
wheels. 


At any instance in time we can solve for R and ω:
-   $R = {l \over 2}{(Vr + Vl) \over (Vr - Vl)}$
-   $w = {Vr - Vl \over l}$

## Understanding the Differential Drive from Data.

- If we compare Vr and Vl i.e `/roboteq_diff_driver/left_motor_speed_cmd` and `/roboteq_diff_driver/right_motor_speed_cmd`

<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a391660b-1425-4f39-b585-8310ff8ea394">

### Observation
- It is clear that it uses a differential drive.
- If Vl = Vr, then we have forward linear motion in a straight line. R becomes infinite, and there
is effectively no rotation - ω is zero.
- If Vl = − Vr, then R = 0, and we have a rotation about the midpoint of the wheel axis - we rotate
in place
- If Vl = 0, then we have a rotation about the left wheel. In this case R = l/2. The same is true if Vr = 0.

### _Note: right cmd and left cmd are in reverse direction because one is connected right (rotates clockwise) and one is connected left (rotates anticlock)_

