# Sensor Alignment Error.

- In this exercise, we will analyze the data to look for errors that result from LiDAR sensors being physically misaligned
in some axes when installed on a robot using [Open3d](http://www.open3d.org/docs/release/introduction.html).

## Step 1: A Quantitative approach using Iterative Closest Point algorithm
Iterative Closest Point (ICP) is a geometric registration algorithm, given an initial transformation estimate, it iteratively finds correspondences and refines transformation minimizing the transformation between the correspondence points until convergence.
This can used to quantitatively estimate misalignment error.

## Understanding ICP
In general, the ICP algorithm iterates over two steps:

1. Find correspondence set k={(𝐩,𝐪)} from target point cloud 𝐏, and source point cloud 𝐐 transformed with the current transformation matrix 𝐓.
2. Update the transformation 𝐓 by minimizing an objective function 𝐸(𝐓) defined over the correspondence set k.
   
<p align="center">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/7e69c3fe-3dd5-4594-9c05-c1d2f4b7c68e">
</p>

where `np` is the normal of the point, and `K` is the correspondence set between target PCD `P` and source PCD `Q`.
There are many ICP techniques
  - **Point-to-Point ICP** - uses the point-to-point correspondence
  - **Point-to-Plane ICP** - uses point to normal of point correspondence
  - **Generalized ICP** - uses both p2p and p2l correspondence.
However due to noise in the data correspondence estimation will be corrupted by outliers, so it is very important to use Robust Kernels that use Outlier Rejections.

Outlier Rejection using Robust Kernels
  - **Huber Loss Kernels**
  - **Turkey Loss kernels**

Using these kernels (**Huber loss**), the Outlier impact of transformation estimation will be reduced.
In this exercise, we will use Huber loss
<p align ="center">
  <img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/1f1c2105-c33b-4222-b534-b63fa177f8e3" >
  <img src = "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/9c1182da-37db-4e9c-b40e-5288eabcf79a" >
</p>

### Step 1: Lets understand the frames of lidars
  - From `tf_static`, we can get the transformation between `base_footprint` to `base_bpearl_front_right_link` and `base_bpearl_back_left_link`
    as shown in the attached picture.
  - For a better understanding of relative misalignment between sensors, let's make `base_bpearl_back_left_link` as a reference and transform from `base_bpearl_back_left_link` to `base_bpearl_front_right_link` can be computed.
  - For this exercise, let's assume `base_bpearl_back_left_link` as a reference and estimate misalignment to `base_bpearl_front_right_link`.
  
<p align ="center">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/3e1464a5-298f-4894-8b1b-3bc5718edc5f">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/7a0b99bc-7d9a-40a5-b531-ab314afc2b10">

<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/d58eae7d-47a1-43ce-9716-4c2915adf8f9">
</p>

_Note: For the exercise, we have taken the first scan as PCD and to estimate transformation from `back_left` PCD to `front_right` PCD_

### Step 2: Global Registration for Initial Transformation
- Global registration techniques like **RANSAC** work well to estimate the initial transformation.
- Better to downsample the PCD into voxels, which helps in faster processing.
- Let's run RANSAC using `from_features` or `from_correspondences` for a better initial transformation estimate, for noisy data better to use `from_features`.
  
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/2f0126e9-883c-4003-a3d0-c64fdbae27c3">

### Observation:
- Compare the initial RANSAC estimate and `tf_static` transformation.
- If we know the initial Estimation, we can directly feed known transformation rather than RANSAC, cause it is only lose Registration.

<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/3469ed3e-223e-4464-917d-ad1a16931814">

- In this exercise, Let's assume we do not know the Transformation, and run ICP with RANSAC output.
   
### Step 3: Tight Local Registration for Transformation Estimation.
- In this exercise, we will use **Point to Plane using Robust Kernel (Huber Loss)**.

<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/4de3dfeb-d975-4b1b-9cec-55ed86d222ca">

<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/bb784a9d-c1d4-4332-8567-51ee47c54eab">

  
### Step 4: Understanding the Misalignment

- Open3d Window showing the tightly merged PCD using point-to-plane ICP.
  
<img src= "https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/690e7e2f-173c-4243-a7f4-ae5ccc4fb731">

***Translation Error*** from `back_left` to `front_right`
- As calculated 1.5705 m is a translation in the x-axis based on `tf_static`.
- As calculated 0.2828 m is a translation in the y-axis based on `tf_static`.
- As calculated 180 deg is a rotation in the z-axis based on `tf_static`.

- And this is the Final Transformation
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/bb784a9d-c1d4-4332-8567-51ee47c54eab">

- If we have used transformation from `tf_static` as the initial transform, we could better estimate the error.

## Step 2: A Qualitative approach that inspects the Data Visually
_Just by visual analysis, we can see the 1.05 meter (at farther dist) error due to the misalignment_
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/4c0c2fab-b19b-440b-b91c-41419f254773">

_Just by visual analysis, we can see the 0.08 meter (at closest dist) error due to the misalignment_
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/79170bc6-0038-4ed9-afd0-a9b5abb4fcfe">

## Step 3: Possible effects of these misalignment errors.

Navigation Impacts:
1. **Inaccurate Mapping:** Misalignment can lead to discrepancies between the maps created by each sensor, causing confusion for navigation algorithms.

2. **Localization Errors:** Mismatched sensor data can result in incorrect localization, affecting the vehicle's ability to understand its position accurately within the environment.

Perception Impacts:
1. **Incomplete Point Clouds:** Misalignment can lead to gaps and overlaps in the point cloud data, making it difficult to accurately perceive the entire environment.

2. **Semantic Understanding:** Misalignment may cause difficulties in associating correct semantic labels with objects in the environment, affecting high-level scene understanding.

3. **Calibration Complexity:** Continuous calibration adjustments are required to mitigate misalignment effects, adding complexity to maintenance and deployment.

Overall, the misalignment of two 3D LiDAR sensors can lead to compromised navigation accuracy, reduced perception quality, and increased computational and calibration efforts to compensate for the errors.
