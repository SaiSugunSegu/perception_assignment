# Estimate Practical Range of 2D and 3D Lidar.

## 1. Estimate Practical Range of 3D BPearl Lidars.
- In this exercise, we will use simple analysis techniques using [rosbag2_py](https://github.com/ros2/rosbag2) library and [Open3d](http://www.open3d.org/) to estimate the Horizontal and Vertical Fields of View
of 3D BPearl Lidars.

<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/6c3307f6-4364-4d47-bacf-7bfb359a33f1">

### Step 1: Read the mcap file.
- We will use rosbag2_py to read the mcap bag file and read the necessary as shown in the image attached below. 
### Step 2: Convert PointCloud2 to PCD file.
- We will use Open3d to handle point cloud files to use it to access the points from the PCD file.

### Step 3: Calculate the Maximum Range for all PCD files.

### _Validation for `/lidars/bpearl_front_right` Practical Range = 145.135 mts._

<p align="center">
  <img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/d83be085-8db7-4ab2-a5f5-6f25634f7a8d">
</p>

### _Validation for `/lidars/bpearl_back_left` Practical Range = 145.055 Deg_

<p align="center">
  <img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/b7167b07-5099-4d41-96bb-ae74e074de9a">
</p>

-----------------------------------------------------------------------------------------------------------------------------

## 2. Estimate Practical Range of 2D Hokuyo Lidars.
- In this exercise, we will use simple analysis techniques using [rosbag2_py](https://github.com/ros2/rosbag2) library  to estimate the Horizontal Field of View
of 2D Hokuyo Lidars.

<p align="center">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/c5036292-cd72-4e77-8716-c907ea3f370d">
</p>


### Observation: 
- Theoretical Observation from the data `/lidars/hokuyo_front_left` and `/lidars/hokuyo_back_right`
  - min range = 0 mts.
  - max range = 40 mts.

  _Given Max Range is approx = 40 mts, we can ignore outliers data (range>40)._
  
  - Pre-processing of Range data.
      1. Simple Filter (Cropping Range>40)
      2. Median Kernel Filter (take a kernel of 5 with the next and previous 2 values, and replace the value with the median of the kernel value)
    - Simple analysis in [PlotJuggler](https://github.com/facontidavide/PlotJuggler) will give a max range per scan.
      
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/9b59979b-3970-4f9d-a092-0323b6a1bbaf">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/c0e9dccb-d5f7-40e4-8574-9fc92a0281fc">

  - But it will be easier if we do it with rosbag2_py for all scans.


### Step 1: Read the mcap file.
- We will use rosbag2_py to read the mcap bag file for the necessary topics as shown in the image attached below. 

### Step 2: Convert Laser Scan data (Polar Co-ordinates to Cartesian Co-ordinates).
- Laser scan data will be in Polar coordinates.
- Conversion of LaserScan data from Polar to Cartesian coordinates and analysis of the spatial spread
can be used as a validation or visualization technique.

### Step 3: Calculate and find Maximum hFOV over all scans.

### _Validated Practical Range of `/lidars/hokuyo_front_left` = 39.993 Deg_
  <p align="center">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/9cdfe284-87a6-4a02-bd4d-4b0b9ea4c266">
  </p>

### _Validated Practical Range of `/lidars/hokuyo_back_right` = 39.999 Deg_
  <p align="center">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/610897d6-5bf1-4074-92cb-4c0a925827a3">
  </p>
