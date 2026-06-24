# Deep Learning for Semantic Image Segmentation

Semantic segmentation project developed for the **Deep Learning for Computer Vision (DL4CV)** course at Ho Chi Minh City University of Technology (HCMUT).

## Overview

This project explores and compares multiple deep learning architectures for semantic image segmentation on the PASCAL VOC 2012 dataset.

The goal is to assign a semantic label to every pixel in an image, enabling precise object localization and scene understanding.

Applications include:

- Autonomous Driving
- Medical Image Analysis
- Robotics
- Intelligent Surveillance
- Image Editing and Understanding

---

## Dataset

### PASCAL VOC 2012

- 21 classes (20 foreground classes + background)
- 2,913 annotated RGB images
- Pixel-level segmentation masks
- Images resized to **512×512** during training

### Data Split

| Dataset | Ratio |
|----------|----------|
| Train | 80% |
| Validation | 10% |
| Test | 10% |

### Data Processing

- Image resizing
- Normalization
- Data augmentation
- Custom Dataset & DataLoader implementation

---

## Models

### CNN-Based Architectures (ResNet50 Backbone)

- FCN
- U-Net
- DeepLabV3
- DeepLabV3+
- PSPNet

### Transformer-Based Architectures (MiT Backbone)

- FPN
- U-Net (U-MixFormer)
- DeepLabV3
- DeepLabV3+
- SegFormer

---

## Evaluation Metrics

The following metrics are used to evaluate model performance:

- Mean Intersection over Union (mIoU)
- Dice Score
- Pixel Accuracy
- Training/Validation Loss
- Inference Speed

---

## Results

### Transformer-Based Models

| Model | mIoU | Pixel Accuracy | Time / Epoch |
|---------|---------|---------|---------|
| SegFormer | **89.14%** | **94.26%** | 34s |
| FPN | 89.12% | 94.25% | 22s |
| DeepLabV3 | 89.11% | 94.24% | 33s |
| DeepLabV3+ | 88.70% | 94.01% | 31s |
| U-Net | 88.25% | 93.76% | 23s |

### Key Findings

- DeepLabV3 and DeepLabV3+ achieve the best overall segmentation quality among CNN-based models.
- SegFormer achieves the highest mIoU and Pixel Accuracy among Transformer-based architectures.
- FCN provides a strong baseline with lower computational complexity.
- U-Net improves boundary reconstruction through skip connections.
- PSPNet benefits from global context aggregation and fast inference.

---

## Visualization

The project includes:

- Ground Truth vs Prediction Comparison
- Per-Class IoU Analysis
- Feature Map Visualization
- Grad-CAM Analysis
- Training Curves

These visualizations help interpret model behavior and segmentation performance.

---





## License

This project is developed for educational and research purposes.
