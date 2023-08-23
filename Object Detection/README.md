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


## Retrain the YOLOV8
- Let's load our dataset using the code download mode Ultralytics offers, where it downloads the data from its API key.
<img width="600" alt="Screenshot 2023-08-23 at 9 45 40 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/73b3be52-d006-43ca-a2e7-bcaedb914df5">

- Re-train the YOLOV8 with our data set.
<img width="600" alt="Screenshot 2023-08-23 at 9 46 05 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a3c96119-897a-49a0-a3ef-8c73340e5a4a">

<img width="600" alt="Screenshot 2023-08-23 at 9 46 21 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/cca2c40a-320f-4f3c-8f88-3ff45329c844">

- Let's see the Matrix and results.
<img width="600" alt="Screenshot 2023-08-23 at 9 33 05 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/e1bf16d9-79ce-46bc-a663-fd1ba3980f94">

![train_batch15](https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/5906e760-95bb-4ae9-8858-3050bd5adb5b)
![val_batch0_pred](https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/f1009f31-15b8-40db-b6aa-48e44fadf9ae)
<img width="1277" alt="Screenshot 2023-08-23 at 9 29 16 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/a3c4c278-31dc-4281-8bf6-4a15b448bf96">
![results](https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/1f9a7825-8a45-4b4b-9009-76104bac892a)
<img width="1277" alt="Screenshot 2023-08-23 at 9 29 50 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/fad3bbf2-7807-4d5a-8519-62b862152c33">
![confusion_matrix_normalized](https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/1e1909d3-3222-4995-a72e-e7069e18a0cf)
<img width="1115" alt="Screenshot 2023-08-23 at 9 30 14 PM" src="https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/48fc637e-051e-40f8-be40-e42cc2e8558a">
![labels_correlogram](https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/033360c5-9e46-407a-8458-57878e3769d1)
![labels](https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/8ba846ce-d439-42b9-8675-c3c6665928f5)
![F1_curve](https://github.com/SaiSugunSegu/perception_sugun_dex/assets/50354583/6333d159-fe44-4842-bec7-3b0e99810532)




