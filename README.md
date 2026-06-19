# Exam Cheating Detection System

This is a 4/2024 backup.

An AI-powered exam monitoring system that automatically detects cheating behaviors in examination rooms using Computer Vision, Pose Estimation, and Deep Learning techniques.

## Overview

Academic dishonesty remains a significant challenge in educational environments. This project aims to develop an intelligent surveillance system capable of detecting suspicious behaviors during examinations through real-time camera monitoring.

The system utilizes the YOLOv8-Pose model to estimate human poses and classify student behaviors based on upper-body keypoints.

---

## Objectives

* Automatically detect cheating behaviors during examinations.
* Monitor students in real time.
* Store evidence images for reporting and analysis.
* Build a dataset for future model improvement and retraining.
* Reduce manual labeling efforts through automatic annotation tools.

---

## Key Features

### 1. Cheating Behavior Detection

The system currently supports three behavior classes:

| Class        | Description                                          |
| ------------ | ---------------------------------------------------- |
| Normal       | Student behaves normally during the exam             |
| Looking Side | Looking left or right to copy answers or communicate |
| Looking Down | Looking down at hidden notes or mobile devices       |

### 2. Human Pose Estimation

* Based on YOLOv8n-Pose
* Tracks 13 upper-body keypoints
* Real-time video processing

### 3. Evidence Collection

When suspicious behavior is detected, the system can:

* Capture evidence images
* Record timestamps
* Store information in a database

### 4. Automatic Data Annotation

* Uses a pre-trained YOLOv8x-Pose-P6 model
* Automatically generates pose labels
* Significantly reduces dataset preparation time

---

## System Architecture

```text
Camera
   │
   ▼
YOLOv8 Pose Estimation
   │
   ▼
Feature Extraction
   │
   ▼
Behavior Classification
   │
   ├── Normal
   ├── Looking Side
   └── Looking Down
   │
   ▼
Alert & Evidence Storage
   │
   ▼
MongoDB Database
```

---

## Technologies Used

### Artificial Intelligence

* YOLOv8n-Pose
* YOLOv8x-Pose-P6
* Pose Estimation
* Computer Vision
* Deep Learning

### Backend

* Python
* OpenCV
* Ultralytics YOLO

### Database

* MongoDB

---

## Dataset

The dataset was collected manually from multiple participants performing different exam-related behaviors under various viewing angles.

### Classes

```text
0 - Normal
1 - Looking_Side
2 - Looking_Down
```

### Dataset Size

| Dataset        | Samples                 |
| -------------- | ----------------------- |
| Training Set   | ~4,000 images per class |
| Validation Set | ~1,000 images per class |

### Annotation Format

Each sample contains:

```text
image.jpg
label.txt
```

The label file includes:

* Bounding box coordinates
* 13 body keypoints
* Class label

---

## Model Training

### Installation

```bash
pip install ultralytics
pip install opencv-python
pip install pymongo
```

### Train Model

```bash
yolo pose train \
data=data.yaml \
model=yolov8n-pose.pt \
epochs=100 \
imgsz=640
```

### Validation

```bash
yolo pose val \
model=best.pt \
data=data.yaml
```

---

## Running the System

```bash
python main.py
```

Using a webcam:

```bash
python detect.py --source 0
```

Using an IP camera:

```bash
python detect.py --source rtsp://...
```

---

## Database Design

### ExamCheatingEvent

```json
{
  "id": "",
  "action_type": "",
  "evidence_image": "",
  "timestamp": "",
  "exam_id": "",
  "subject_id": "",
  "confirmed": false
}
```

### ActionType

```json
{
  "id": "",
  "name": ""
}
```

### TrainingImage

```json
{
  "id": "",
  "image": "",
  "action_type": ""
}
```

---

## Results

After training for 100 epochs:

* The model can detect cheating-related behaviors in real time.
* Experimental results demonstrate promising performance for research purposes.
* Additional real-world exam room data is required to improve robustness and deployment readiness.

---

## Future Improvements

* Mobile phone detection.
* Multi-student interaction analysis.
* Multi-camera support.
* Real-time monitoring dashboard.
* Continuous model retraining from newly collected data.
* Deployment on Edge AI devices such as Jetson Nano and Raspberry Pi.


---

## References

* Ultralytics YOLOv8 Documentation
* LearnOpenCV
* MongoDB Documentation
* Computer Vision: Algorithms and Applications (Richard Szeliski)
* Machine Learning Basics
* Deep Learning Fundamentals

---

## License

This project is developed for academic and research purposes only.

Scientific research 2024
