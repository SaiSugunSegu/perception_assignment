# Stereo Camera Calibration

- In this exercise, we have a Horizontal Stereo Normal camera, and we will calibrate and understand the Intrinsics of each camera and rectify the Images.
- We will then apply Stereo Rectification to create a Disparity Map.
  - Intrinsics Parameter Estimation and Image Rectification.
  - Imaging matching and finding correspondence.
  - Baseline estimation using Essential Matrix decomposition.
  - Disparity calculation for Depth Map.


## Intrincics Calibration 

### Step 1: Understanding Pinhole Camera Model and Distortion Model.
<p align = "center">
<img width="500" src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/adb8efb6-23ce-412c-9c52-d5574569a7dc">
</p>

The pinhole camera model is a simple representation of how light creates an inverted image on a surface through a small hole. It doesn't require a lens, forms inverted images, has a large depth of field, and longer exposures. It's a basic concept in imaging despite its limitations.

- **Camera Model** - Pinhole Model - Camera Parameters are `fx`, `fy` (focal length) and `cx`, `cy` (principal points), and `s` (scale in analog cameras).
- **Distortion Model** - Deviations can arise due to imperfections in camera lenses or the camera's sensor.

- There are two kinds of distortion models:
- **Brown-Conrady (Radial-Tangen)**: k1, k2, p1, p2, p3
  - Barrel distortion
  - Pincushion Distortion
- **Kannala-Brandt**: k1, k2, k3, k4.
  - for wide angle, fish eye lens.

  

### Step 2: Using DLT (Zhang's method) and estimate 
  - We can use Direct Linear Transform to estimate pixel (2D) to checker points (3D) mapping.
  - In this exercise, we will use the OpenCV function to estimate the camera parameters and Distortion parameters by minimizing the reprojection error.

<img width="500"  src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/4e527818-bfee-4ced-84cf-041d7e73ab19">
<img width="500" src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/c6b4fc54-1408-4673-a2fb-770607ae38d6">

### Step 3: Calibration Using Opencv and Charuco markers.
- We use the Charuco board to collect corners and IDs, I personally prefer April Tags to make detection robust detection in rotation.
  
<img width="700" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/02bf3ec3-0fe2-4958-9989-6940a68ab240">
<img width="300" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/8cd51e3b-5609-4322-b6a2-3638e9c1a62a">


- Use the parameters to rectify (undistort) the image.
  - See the barreled board became straight after rectification.
<p align ="center" >
<img width="800" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/52252ffb-c7fb-4787-8190-3c04df0a36ee">
</p>

### Step 4: Validate the Intrinsics using Reprojection Error
- Opencv inherently minimizes re-projection error by projecting the pixel back using transformation estimate vs. target pixels (charuko config).
- **Re-Projection Error of less than 1 pixel is considered good calibration, we got 0.3 pixels**

<p align ="center" >
<img width="300" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/c98f101c-9bc6-4abf-8202-c3e6e3290eee">
</p>


## Stereo Rectification 

### Step 1: Image Matching
- We should use Good Feature Detectors and Feature Descriptors for detection and description.
  - SIFT - Scale Invariant Feature Transform
  - SURF - Speeded Up Robust Feature
  - ORB - Oriented Fast and Rotated Brief.

- These are good enough detectors and descriptors, we get key points from this. if we get the less correspondences, we can use the charuco corners as key points.


<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/16a85f2d-b3c5-4851-b471-9742dddfe98e">

- We use simple Hamming distance to do the nearest neighborhood search.

- But we can use better Matchers, one good and fast Matcher is [LightGlue](https://github.com/cvg/LightGlue), see the dense match that we get from `LightGlue`.

<p align ="center" >
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/13d9e514-e72f-49bf-89ed-cb84d062140d">
</p>



### Step 2: Baseline (R and T) from Essential Matrix.
- We know the intrinsics, so, we can estimate Essential Matrix and decompose it with SVD(singular value decomposition) and find R and t between cam1 to cam2.
- We need to estimate b (baseline) to find disparity.

  
### Step 3: Disparity Map and Depth Map Using Triangulation.
<img width="500" src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/39d1753f-7c71-4efb-be5b-db0a08d81b27">
<img width="500" src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/64465aa4-1337-4b1f-9b37-290cdd5670f6">
