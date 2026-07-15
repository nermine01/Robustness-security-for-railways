# 🚆 Robustness & Security for Railways

A computer vision project focused on improving **railway safety and robustness** using deep learning-based object detection and distance estimation techniques.

This project explores the training, evaluation, and analysis of a custom **YOLOv8** model for railway object detection, followed by distance estimation methods that can be integrated into intelligent railway monitoring systems.

---

# Table of Contents

- [Overview](#overview)
- [Project Objectives](#project-objectives)
- [Repository Structure](#repository-structure)
- [Methodology](#methodology)
- [Dataset](#dataset)
- [Model Training](#model-training)
- [Model Evaluation](#model-evaluation)
- [Distance Estimation](#distance-estimation)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Future Improvements](#future-improvements)
- [License](#license)

---

# Overview

Railway environments require highly reliable perception systems capable of detecting obstacles and estimating their distance accurately under varying conditions.

This repository investigates:

- Custom object detection using **YOLOv8**
- Fine-tuning on a railway dataset
- Performance evaluation using standard detection metrics
- Physics-inspired distance estimation
- Comparison between multiple distance estimation methods

The goal is to build a robust perception pipeline that can contribute to safer railway monitoring and autonomous inspection systems.

---

# Project Objectives

The project focuses on:

- Detecting railway-related objects using deep learning
- Fine-tuning a YOLOv8 detector
- Evaluating detection robustness
- Estimating object distance from monocular images
- Comparing different distance estimation techniques
- Providing a reproducible experimental pipeline

---

# Repository Structure

```
Robustness-security-for-railways/
│
├── README.md
│
├── retrain v3 finetuned.ipynb
│   ├── Dataset exploration
│   ├── Annotation processing
│   ├── YOLOv8 fine-tuning
│   ├── Training
│   └── Performance visualization
│
├── evaluation on Golden Standard.ipynb
│   ├── Model loading
│   ├── Validation
│   ├── mAP evaluation
│   ├── Confusion matrix
│   ├── Precision-Recall curves
│   └── Visual inference
│
└── distance.ipynb
    ├── Bounding box extraction
    ├── Distance estimation
    ├── Empirical distance model
    ├── Pinhole camera model
    └── Method comparison
```

---

# Methodology

The workflow consists of three major stages.

## 1. Dataset Preparation

The dataset is organized into:

- Training images
- Validation images
- Test images
- COCO-style annotations

Images are converted into the format required by YOLOv8 for training.

---

## 2. Model Training

The object detector is trained using **Ultralytics YOLOv8**.

The training notebook includes:

- Dataset inspection
- Annotation loading
- Data preprocessing
- Fine-tuning from pretrained weights
- Monitoring training performance

---

## 3. Model Evaluation

The trained model is evaluated on a validation dataset using:

- Precision
- Recall
- mAP@50
- mAP@50-95
- Per-class performance
- Precision-Recall curves
- Confusion matrix

Visual predictions are also generated for qualitative inspection.

---

## 4. Distance Estimation

After detecting an object, its bounding box dimensions are used to estimate its distance from the camera.

Two different approaches are compared.

### Physics-Based Pinhole Camera Model

The first method estimates distance using:

- Camera focal length
- Estimated object dimensions
- Bounding box size

This approach follows the standard pinhole camera projection model.

---

### Empirical Distance Model

A second model estimates distance using an empirical relationship between:

- Bounding box width
- Bounding box height

The empirical model serves as a lightweight approximation and is compared against the pinhole method.

---

### Comparison

The notebook computes:

- Estimated distances
- Absolute differences
- Average disagreement
- Maximum disagreement

Scatter plots are generated to visualize the relationship between object size and estimated distance.

---

# Dataset

The project expects a railway dataset organized similarly to:

```
dataset/
│
├── images/
│   ├── train/
│   ├── val/
│   └── test/
│
├── labels/
│   ├── train/
│   ├── val/
│   └── test/
│
└── data.yaml
```

The dataset configuration is provided through the `data.yaml` file used by YOLOv8.

---

# Model Training

Training is performed using the Ultralytics framework.

Typical workflow:

1. Load pretrained YOLOv8 weights
2. Configure dataset
3. Fine-tune on railway images
4. Save the best-performing weights

The notebook also includes exploratory analysis of annotations before training.

---

# Model Evaluation

Evaluation includes:

- Validation on a held-out dataset
- Class-wise mAP
- Precision
- Recall
- Confusion Matrix
- Precision-Recall Curves
- Qualitative prediction visualization

These metrics help identify strengths and weaknesses of the trained detector.

---

# Distance Estimation

The `distance.ipynb` notebook demonstrates:

- Detection loading
- Bounding box measurements
- Distance calculation
- Comparison between estimation methods

Outputs include:

- Estimated distance per object
- Average distance
- Error comparison
- Scatter plots
- Statistical summaries

---

# Technologies Used

- Python
- YOLOv8 (Ultralytics)
- PyTorch
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook

---

# Installation

Clone the repository:

```bash
git clone https://github.com/nermine01/Robustness-security-for-railways.git

cd Robustness-security-for-railways
```

Install the required dependencies:

```bash
pip install ultralytics
pip install torch torchvision
pip install opencv-python
pip install pandas
pip install matplotlib
pip install seaborn
pip install pyyaml
```

---

# Usage

## Train the Model

Open:

```
retrain v3 finetuned.ipynb
```

Run all cells to:

- Explore the dataset
- Fine-tune YOLOv8
- Save trained weights

---

## Evaluate the Model

Open:

```
evaluation on Golden Standard.ipynb
```

Run the notebook to:

- Load trained weights
- Evaluate performance
- Generate confusion matrices
- Generate PR curves
- Perform visual inference

---

## Estimate Distance

Open:

```
distance.ipynb
```

The notebook:

- Computes object distances
- Applies multiple estimation methods
- Compares the obtained results
- Produces statistical analyses and plots

---

# Results

The project provides:

- Custom-trained railway object detector
- Comprehensive evaluation metrics
- Class-wise performance analysis
- Visual prediction examples
- Distance estimation pipeline
- Comparative analysis of distance estimation methods

---

# Future Improvements

Potential extensions include:

- Stereo vision-based distance estimation
- Real-time inference on video streams
- Multi-object tracking
- Sensor fusion with LiDAR
- Railway anomaly detection
- Weather robustness evaluation
- Edge deployment optimization
- Integration into autonomous railway inspection systems

---

# License

This repository is intended for academic and research purposes.

Feel free to fork, modify, and extend the project while providing appropriate attribution.

---

# Author

**Nermine Haouala**

Computer Science Engineering Student (Data Science)

Interested in:

- Computer Vision
- Deep Learning
- AI for Transportation
- Railway Safety Systems
- Autonomous Perception
