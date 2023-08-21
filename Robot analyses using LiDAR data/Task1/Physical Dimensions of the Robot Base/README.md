# Physical Dimensions of the Robot Base.

## Determine Wheel Track Length
- As we know, the robot uses a differential drive, and at a given instance we can determine `w` using the below Equations.
 
  - $w = {Vr - Vl \over l}$
 
for the data 
- w - `/odom/twist/twist/angular/z` (rad/s)
- Vr - `/roboteq_diff_driver/right_motor_encoder` (rpm)
- Vl - `/roboteq_diff_driver/left_motor_encoder`  (rpm)

We can use [PlotJuggler](https://github.com/facontidavide/PlotJuggler) to estimate `l` (wheel track - axle distance between 2 wheels), given w, Vl, Vr

<img src ="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/c5c8c451-d209-466f-8497-4366b724ab7a">

<img src ="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/229931a3-c600-40b5-8218-723bd9bc572e">

### _Estimated Wheel Track is approx 0.81 m (can be prone to noise due to noise in rpm)_

- We can Evaluate the same with Foxglove, and measure distance between 2 links
<img src ="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a7e7837b-6721-4102-8541-b09a2ecd3f2f">


