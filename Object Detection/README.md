# Object Detection

In this exercise, we will retrain the SOTA Object Detection algorithm with our custom dataset with Forklifts and Pallets.

- Objective: To find a general methodology, to detect objects found on the shop floor.
  - Custom DataSet: Annotate Forklift and Pallet
  - Retrain YOLOv8 using our dataset.
  - Evaluate using ROS bag data.
 
## Custom DataSet:
- Let's take a few sample images from ROSBAG (.mcap) file.
<p align="center">
<img width="700" alt="Screenshot 2023-08-23 at 3 20 58 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/625ab88b-d9e8-4f21-b139-6f42495453c8">
</p>
  
- Use Roboflow to Annotate them.
  - Class 1: Forklift
  - Class 2: Pallet

<p align="center">
<img width="700" alt="Screenshot 2023-08-23 at 3 25 08 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/8f9ef55f-9091-492b-824f-83f98f963913">
<img width="700" alt="Screenshot 2023-08-23 at 3 25 23 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/7d6b1c39-f654-4eef-96a1-b12ba5f08cbf">
</p>

- Divide the Dataset into Train, Eval, and Test datasets.
- Download the data set into our notebook.
<img width="700" alt="Screenshot 2023-08-23 at 3 57 24 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/f4f72c3f-93b8-474b-b280-c37170c482d0">
<img width="300" alt="Screenshot 2023-08-23 at 3 57 57 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a9b73808-8250-4500-b248-98b1d2d5c4fe">
</p>
