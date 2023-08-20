# Estimate FOV coverage of 2D and 3D Lidar.

## 1. Estimate Horizontal and Vertical FOV of 3D BPearl Lidars.
- In this exercise, we will use simple analysis techniques using [rosbag2_py](https://github.com/ros2/rosbag2) library and [Open3d](http://www.open3d.org/) to estimate the Horizontal and Vertical Fields of View
of 3D BPearl Lidars.
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/3641c81b-aa95-466f-bbc3-629d8ba2a711">

### Step 1: Read the mcap file.
- We will use rosbag2_py to read the mcap bag file and read the necessary as shown in the image attached below. 
### Step 2: Convert PointCloud2 to PCD file.
- We will use Open3d to handle point cloud files to use it to access the points from the PCD file.

### Step 3: Calculate Maximum Horizontal and Vertical FOV for all PCD files.

### _Validation for `/lidars/bpearl_front_right` HFOV = 359.9995 Deg; VFOV = 89.4946 Deg_

<p align="center">
  <img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/d83be085-8db7-4ab2-a5f5-6f25634f7a8d">
</p>

### _Validation for `/lidars/bpearl_back_left` HFOV = 359.9996 Deg; VFOV =  89.4944 Deg_

<p align="center">
  <img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/b7167b07-5099-4d41-96bb-ae74e074de9a">
</p>


-----------------------------------------------------------------------------------------------------------------------------


## 2. Estimate Horizontal FOV of 2D Hokuyo Lidars.
- In this exercise, we will use simple analysis techniques using [rosbag2_py](https://github.com/ros2/rosbag2) library  to estimate the Horizontal Field of View
of 2D Hokuyo Lidars.

<p align="center">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/c5036292-cd72-4e77-8716-c907ea3f370d">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/176e76e2-f590-4208-813e-462ecd5ec72b">
</p>

### Observation: 
- Theoretical Observation from the data `/lidars/hokuyo_front_left` and `/lidars/hokuyo_back_right`
  - min angle = -2.312561273574829 rad = -132.5 Deg
  - max angle = 2.2951080799102783 rad = 131.5 Deg
  - with a resolution of 0.00436 rad = 0.249 Deg

  _Giving Total Vertical FOV is approx = 264 Deg._


### Step 1: Read the mcap file.
- We will use rosbag2_py to read the mcap bag file and read the necessary as shown in the image attached below. 

### Step 2: Convert Laser Scan data (Polar Co-ordinates to Cartesian Co-ordinates).
- Laser scan data will be in Polar coordinates.
- Conversion of LaserScan data from Polar to Cartesian coordinates and analysis of the spatial spread
can be used as a validation or visualization technique.

### Step 3: Calculate and find Maximum hFOV over all scans.

### _Validated HFOV of `/lidars/hokuyo_front_left` = 248.45 Deg_
  <p align="center">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/51d7ef0d-2573-4bc5-ae8b-c49669cbd697">
  </p>
  

### _Validated HFOV of `/lidars/hokuyo_back_right` = 256.19 Deg_

  <p align="center">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/9c0a6483-8b55-4f05-9f45-0e7791e7dbb4">
  </p>
