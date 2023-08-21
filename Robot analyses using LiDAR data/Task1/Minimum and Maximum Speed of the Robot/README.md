
# Estimate the Minimum and Maximum Speed of the robot.
- In this exercise, We will use `PlotJuggler` to analyze and find the maximum and minimum speed of the robot in the episode (collected from the bag).
- Let's Find maximum and Minimum Linear and Angular speed.

## Step 1: Create a function to estimate "Linear Velocity..
- We can create a custom function for the series to estimate the values we need using Odometry Topic -  `/odom/twist/twist/linear/x`, `/odom/twist/twist/linear/y`, `/odom/twist/twist/linear/z` topics.
- Let's create a function for calculating resultant velocity from velocity components.
    $v = √(vx^2 + vy^2 + vz^2)$ 
  <p align="center">
  <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/ecfa6a27-a803-4c36-862b-de9070716fa1" />
  </p>
### Observations:
- As we can see, the robot has linear velocity only in the x-axis from 0~1 m/s (theoretically). 
  
## Step 2: Estimate the Maximum and Minimum Linear Velocity.
### Maximum Velocity.
- We can just compare the previous velocity to the current to find the Maximum Velocity that the robot exhibited from live data.
   <p align="center">
    <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/fae94649-11e1-4a3f-949d-29098960dddb" />
  </p>
### Observations:
The estimated Maximum Velocity is 1.048 m/s.

### Minimum Velocity.
- We can just compare the previous velocity to the current to find the Minimum Velocity that the robot exhibited from live data.
  <p align="center">
  <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/d450e82b-8776-462c-924c-b8c96a465e8d)" />
  </p>
### Observations:
The estimated Minimum Velocity is 0.0 m/s.

### _- Now we can run the series to see the Maximum and Minimum Velocity of the robot._
  <p align="center">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/8a16a2b3-7a3f-462d-a355-555290108b5f" />
  </p>

## Step 3: Create a function to estimate "Angular Velocity".
- We can create a custom function for the series to estimate the values we need using Odometry Topic -`/odom/twist/twist/angular/z` topics.
   
<p align="center">
    <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/b948cd9e-3fa0-4961-a492-38eea74bd3ce" />
</p>
  
### Observations:
- As we can see, the robot has Angular velocity only in the z-axis from -0.8 ~ 0.8 rad/s (theoretically).
  
## Step 4: Estimate the Maximum and Minimum Angular Velocity.
### Maximum Angular Velocity.
- We can just compare the previous angular velocity to the current to find the Maximum angular Velocity that the robot exhibited from live data.

<p align="center">
    <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/aa32b518-2791-4cd5-b115-f1b38e7f41bc" />
  </p>

### Observations:
The estimated Maximum Angular Velocity is  0.7852 rad/s.

### Minimum Velocity.
- We can just compare the previous angular velocity to the current to find the Minimum Angular Velocity that the robot exhibited from live data.
  
<p align="center">
    <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/aa32b518-2791-4cd5-b115-f1b38e7f41bc" />
  </p>
  
### Observations:
The estimated Minimum Angular Velocity is -0.7358 rad/s.

