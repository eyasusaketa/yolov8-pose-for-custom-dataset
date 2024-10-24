# YOLOv8 Pose for Custom Dataset

This repository demonstrates how to use YOLOv8's pose estimation capabilities on a custom dataset. YOLOv8 is an advanced object detection model that supports pose estimation, allowing for real-time prediction of keypoints such as body joints in images or videos.

## Table of Contents
- [Installation](#installation)
- [Dataset Preparation](#dataset-preparation)
- [Training](#training)
- [Evaluation](#evaluation)
- [Inference](#inference)
- [Customization](#customization)
- [Acknowledgements](#acknowledgements)

## Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/ultralytics/ultralytics.git
    cd ultralytics
    ```

2. **Install dependencies**:
    Make sure you have Python installed. Then install the required packages using:
    ```bash
    pip install ultralytics
    ```

3. **Verify Installation**:
    To ensure YOLOv8 is correctly installed, run:
    ```bash
    yolo task=pose mode=predict model=yolov8n-pose.pt source='path_to_image_or_video'
    ```

## Dataset Preparation

To train YOLOv8 Pose on a custom dataset, the dataset should be in a COCO-style format, including:

- **Images**: All images must be organized in a folder.
- **Annotations**: Keypoint annotations for the images should be in JSON format (COCO-style annotations).

**Steps for dataset preparation:**

1. **Images**:
    Place all your images in a directory, e.g., `datasets/images`.

2. **Annotations**:
    - Prepare a JSON file containing annotations in COCO format.
    - Include keypoints data, such as nose, shoulders, elbows, wrists, etc., in the `annotations` section.

3. **Directory Structure**:
    Your directory structure should look like this:
    ```text
    data/
    ├── images/
    |   |-- train/  
    │       ├── image1.jpg
    │── val
    ├       |── image2.jpg
    ├── labels/
    |   |-- train/  
    │       ├── image1.txt
    │── val
    ├       |── image2.txt
    ```

## Training

To train YOLOv8 Pose on your custom dataset, run the following command:

```bash
yolo task=pose mode=train model=yolov8n-pose.pt data=path/to/dataset.yaml epochs=100 imgsz=640 batch=16
