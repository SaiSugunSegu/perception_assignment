# Stereo Camera Calibration

- In this exercise, we have a Horizontal Stereo Normal camera, and we will calibrate and understand the Intrinsics of each camera and rectify the Images.
- We will then apply Stereo Rectification to create a Disparity Map.
 - Intrinsics Parameter Estimation and Image Rectification.
 - Imaging matching and finding Correspondances.
 - Baseline estimation using Essential Matrix decomposition.
 - Disparity calculation for Depth Map.


## Intrincics Calibration 

### Step 1: Understanding Pinhole Camera Model and Distortion Model.
### Step 2: Using DLT (Zhang's method) and estimate 
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/adb8efb6-23ce-412c-9c52-d5574569a7dc">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/4e527818-bfee-4ced-84cf-041d7e73ab19">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/c6b4fc54-1408-4673-a2fb-770607ae38d6">

### Step 3: Calibration Using Opencv and Charuco markers.

<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/02bf3ec3-0fe2-4958-9989-6940a68ab240">


<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/8cd51e3b-5609-4322-b6a2-3638e9c1a62a">

## Stereo Rectification 

### Step 1: Image Matching

<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/16a85f2d-b3c5-4851-b471-9742dddfe98e">

### Step 2: Baseline (R and T) from Essential Matrix
### Step 3: Disparity Map and Depth Map Using Triangulation.
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/39d1753f-7c71-4efb-be5b-db0a08d81b27">
<img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/64465aa4-1337-4b1f-9b37-290cdd5670f6">
