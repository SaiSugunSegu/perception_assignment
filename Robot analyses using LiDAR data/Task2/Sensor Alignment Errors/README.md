# Sensor Alignment Error.

- In this exercise, we will analyze the data in order to look for errors that result from LiDAR sensors being physically misaligned
in some axes when installed on a robot.

## Step 1: A Quantitative approach using Iterative Closest Point algorithm
Iterative Closest Point (ICP) is a geometric registration algorithm, given an initial transformation estimate, it iteratively finds correspondences and refines transformation minimizing the transformation between the correspondence points until convergence.
This can used to quantitatively estimate misalignment error.
<p align="center">
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/7e69c3fe-3dd5-4594-9c05-c1d2f4b7c68e">
</p>
- where `np` is the effect of the kernel, `K` is the correspondence set between target PCD `P` and source PCD `Q`.

- There are many ICP techniques
  - Point-to-Point ICP
  - Point-to-Plane ICP
  - Generalized ICP
- Outlier Rejection using Robust Kernels
  - Huber Loss Kernels
  - Turkey Loss kernels 


## Step 2: A Qualitative approach that inspects the Data Visually
_Just by visual analysis, we can see the 1.05 meter (at farther dist) error due to the misalignment_
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/4c0c2fab-b19b-440b-b91c-41419f254773">

_Just by visual analysis, we can see the 0.08 meter (at closest dist) error due to the misalignment_
<img src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/79170bc6-0038-4ed9-afd0-a9b5abb4fcfe">

## Step 3: Possible effects of these misalignment errors.

