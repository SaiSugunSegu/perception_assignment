# Object Detection

In this exercise, we will retrain the SOTA Object Detection algorithm with our custom dataset with Forklifts and Pallets.

- Objective: To find a general methodology, to detect objects found on the shop floor.
  - Custom DataSet: Annotate Forklift and Pallet
  - Retrain YOLOv8 using our dataset.
  - Evaluate using ROS bag data.

- Instance Segmentation gives both object detection and semantic segmentation, using this we can properly detect the Fork only on Forklift. 
  
## Custom DataSet:
- Let's take a few sample images from the ROSBAG (.mcap) file.
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


## Retrain the YOLOV8
### Let's load our dataset using the code download mode Ultralytics offers, where it downloads the data from its API key.
<p align="center">
<img width="600" alt="Screenshot 2023-08-23 at 9 45 40 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/73b3be52-d006-43ca-a2e7-bcaedb914df5">

### Re-train the YOLOV8 with our data set.
<p align="center">
<img width="600" alt="Screenshot 2023-08-23 at 9 46 05 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a3c96119-897a-49a0-a3ef-8c73340e5a4a">
  
<img width="600" alt="Screenshot 2023-08-23 at 9 46 21 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/cca2c40a-320f-4f3c-8f88-3ff45329c844">
</p>

### Results on the Validation set.
<p align="center">
<img width="800" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a3c4c278-31dc-4281-8bf6-4a15b448bf96">

<img width="600" alt="Screenshot 2023-08-23 at 9 29 50 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/fad3bbf2-7807-4d5a-8519-62b862152c33">
</p>

### Confusion Matrix
<p align="center">
<img width="500" alt="Screenshot 2023-08-23 at 9 30 14 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/48fc637e-051e-40f8-be40-e42cc2e8558a">
</p>

- Looking at the Confusion Matrix, we need to train with a little more data to get the ideal confusion matrix to get confidence diagonally.

## Evaluate on streamer data

<video  alt="Detection on Video Stream" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/496cf8b6-f9ce-49ab-a10c-5ebe06f83e98">

