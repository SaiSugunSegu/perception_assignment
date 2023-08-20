# Robot Kinematics Analyses using LiDAR data

The provided bag contains sensor data from both 2D and 3D LiDAR sensors (two BPearl
sensors, two Hokuyo sensors), along with odometry and the full tf tree.

## Task A
For this task, we want you to perform some analysis in order to understand the kinematics of our
robot. From replaying the data, you should be able to come up with the following:

## Introduction to Plot juggler
- dfd

- Install and run ROS Plot Juggler Package with:
```
sudo apt install ros-$ROS_DISTRO-plotjuggler-ros

ros2 run plotjuggler plotjuggler
```

- Lets Load the ros bag
<p align="center">
  <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/6e3c379b-2e18-4873-9245-9e4e01254ccd" />
</p>

### Estimate the physical dimensions of the robot base. 


### Estimate the minimum and maximum speed of the robot.
- We can use Plot Juggler to analyse and find the maximum and minimum speed of the robot in the episode (collected from bag).
- Lets Find Maximun and Mininum Linear and Angular speed.

- we can create custon function to the series to estimate the values we need from the bag.
  - lets create function for calculating speed.
    <p align="center">
  <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/ecfa6a27-a803-4c36-862b-de9070716fa1" />
    </p>
   - lets create function for calculating maximun and minimum speed of the robot in the bag.  
       <p align="center">
    <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/fae94649-11e1-4a3f-949d-29098960dddb" />
      </p>
  - print
      <p align="center">
    <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/d450e82b-8776-462c-924c-b8c96a465e8d)" />
      </p>

  - Now we can run the series to see maximun and minumum speed of the robot.
      <p align="center">
    <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/8a16a2b3-7a3f-462d-a355-555290108b5f" />
      </p>

    
  - lets estimate maximun and minimum angular speed.
    - Maximum Angular Speed 
    <p align="center">
  <img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/6e3c379b-2e18-4873-9245-9e4e01254ccd" />
    </p>
    - lets create function for calculating maximun and minimum angular speed of the robot in the bag.    


### Estimate the maximum practical range of each sensor.
- We can use Plot Juggler to analyse and find the practical range of each sensors.

  - 2D Sensor
  - 3D Sensor

### Describe what kinematic drive model you think the robot uses.
