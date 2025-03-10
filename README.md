YOLOv8 Dataset Preparation and Helmet Detection using YOLOv8


This project implements a helmet detection system using the YOLOv8 object detection model. It is designed to detect helmets and heads in images, with a focus on balancing the dataset and training the model for optimal performance.

Table of Contents

1.Overview

2.Features

3.Usage

4.Dataset Preparation

5.Training

6.Inference

7.Results

Overview

The goal of this project is to detect helmets and heads in images using YOLOv8. The workflow includes:
Uploading and extracting a dataset.
Balancing the dataset to ensure equal representation of classes.
Training the YOLOv8 model.
Performing inference on test images.
Visualizing the results.

Features

Dataset Balancing: Automatically balances the dataset by downsampling the majority class.
YOLOv8 Training: Trains a YOLOv8 model with customizable parameters.
Inference: Performs inference on new images and visualizes the results.
Visualization: Displays ground truth and predicted bounding boxes side by side.
Usage

Dataset Preparation

1.Upload your dataset in a ZIP file.

2.Use the upload_and_extract_zip_colab function to extract and organize the dataset:

dataset_path = upload_and_extract_zip_colab("/content/dataset")

3.Update the YAML configuration file with the correct paths and class names:

update_yaml("my_data.yaml", train_images_path, val_images_path, test_images_path, ["head", "helmet"])

Training

Train the YOLOv8 model using the train_yolo function:

model = train_yolo("my_data.yaml", model_path="yolov8n.pt", epochs=100)

Inference

Perform inference on test images and visualize the results:

visualize_predictions(
    model_path="runs/detect/train/weights/best.pt",
    test_images_path="dataset/test/images",
    test_labels_path="dataset/test/labels",
    yaml_path="my_data.yaml",
    num_images=10
)

Results

After training, the model's performance can be evaluated using the validation set. The results, including precision, recall, and mAP, are saved in the runs/detect/train directory.

![image](https://github.com/user-attachments/assets/b151fa33-a82e-47d1-9d94-d2394bf17a6d)

![image](https://github.com/user-attachments/assets/aec1333f-9e07-42d7-8cae-6b9311a9a246)



