With the increasing demand for fair and transparent examinations, manual invigilation has become inefficient and error-prone, especially in large-scale exam settings. This project focuses on applying Machine Learning and Deep Learning techniques to automatically detect cheating behaviors in exam rooms using video analysis.

The system leverages computer vision models to analyze student posture, movements, and behaviors from classroom video streams, providing an intelligent and scalable solution for exam monitoring.

## Objectives
Automatically detect suspicious and cheating behaviors in examination rooms
Reduce reliance on manual supervision
Enable real-time or near real-time monitoring using video data
Store and manage detected incidents for post-exam review

## Methodology
1. Video Data Collection & Processing
Collected classroom and exam room video data from multiple camera angles
Preprocessed videos by frame extraction, resizing, and normalization

2. Pose Estimation & Behavior Analysis
Implemented a YOLOv8-based pose estimation model to detect student body keypoints
Analyzed posture and movement patterns to identify abnormal or suspicious behaviors (e.g., frequent head turning, leaning, unusual hand movements)

3. Data Management
Designed a backend system using MongoDB to store detected cheating events
Each incident includes timestamp, student ID (if available), and behavior type

## Technology Stack
Programming Language: Python
Deep Learning Model: YOLOv8 (Pose Estimation)
Database: MongoDB
Domain: Computer Vision, Video Analytics

## Key Features
Real-time posture analysis from video streams
Robust detection using deep learning–based pose estimation
Scalable architecture for large exam rooms
Efficient logging and management of cheating incidents

## Potential Applications
Examination monitoring in schools and universities
Online/offline hybrid exam supervision
Smart classrooms and educational analytics

## Future Work
Integrate multi-object tracking (e.g., ByteTrack) for consistent student identification
Improve behavior classification with temporal models (LSTM / Transformer)

Deploy the system as a real-time web service

Extend to multi-camera and multi-room environments
