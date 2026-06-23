# PathMNIST Image Classification

## Overview
This project evaluates multiple deep learning architectures on the **PathMNIST** histopathology image classification dataset for colorectal cancer tissue analysis.

## Dataset: PathMNIST

- Task: Histopathology image classification
- Number of classes: 9
- Image size: 224 × 224 RGB
- Training samples: 89,996
- Validation samples: 10,005
- Test samples: 7,180

### Classes
| ID | Class |
|----|--------|
| 0 | Adipose |
| 1 | Background |
| 2 | Debris |
| 3 | Lymphocytes |
| 4 | Mucus |
| 5 | Smooth Muscle |
| 6 | Normal Colon Mucosa |
| 7 | Cancer-associated Stroma |
| 8 | Colorectal Adenocarcinoma |

## Models Evaluated

| Model | Parameters | Configuration |
|---------|---------|---------|
| TinyVGG | ~100K | Train from scratch |
| ResNet18 | ~11.2M | ImageNet Pretrained |
| ResNet50 | ~23.5M | ImageNet Pretrained |
| MobileNetV3 Large | ~5.5M | ImageNet Pretrained |
| ViT-S | ~22M | ImageNet Pretrained |
| ViT-B | ~86M | ImageNet Pretrained |

## Results

| Model | Train Acc | Test Acc | Recall | Precision |
|---------|---------|---------|---------|---------|
| TinyVGG | 96.2% | 76.4% | 71.0% | 71.8% |
| ResNet18 | 99.8% | 93.2% | 91.1% | 91.4% |
| ResNet50 | 99.6% | 93.3% | 91.1% | 91.3% |
| MobileNetV3 Large | 95.5% | 93.5% | 90.8% | 91.9% |
| ViT-S | 97.0% | 91.1% | 89.7% | 88.9% |
| ViT-B | 95.2% | 92.9% | 91.2% | 90.7% |

## Model Refinement

### MR1 - TinyVGG Analysis
- Focuses on tissue regions and ignores empty background.
- Limited contextual understanding due to shallow architecture.

### MR2 - ResNet18 / ResNet50 Error Analysis
- Larger receptive field.
- Better feature extraction.
- Still struggles with global tissue relationships.

### MR3 - Data Augmentation + Class Weighting
- Image rotation augmentation.
- Increased weight for difficult classes.
- Improved performance but challenging samples remain.

### MR4 - Unfreezing Backbone

| Configuration | Test Acc | Recall | Precision |
|--------------|----------|---------|-----------|
| ResNet18 Pretrained | 93.2% | 91.1% | 91.4% |
| Unfreeze Last 4 Layers | 94.1% | 92.2% | 92.6% |
| Unfreeze All Layers + Rotation | 95.4% | 93.3% | 94.9% |

### MR5 - ResNet18 + ViT-B

| Model | Training Time | Test Acc |
|---------|---------|---------|
| ResNet18 + ViT-B | 38 min / 5 epochs | 93.8% |
| ResNet18 + Data Augmentation | 22 min / 5 epochs | 95.0% |

## Key Findings

- Transfer learning significantly outperforms training from scratch.
- ResNet18 provides the best trade-off between accuracy, training time, and complexity.
- Full backbone fine-tuning with augmentation achieves the highest accuracy (95.4%).
- ViT-based hybrid models increase computational cost without improving performance on this dataset.

## Repository Structure

```text
├── data/
├── notebooks/
├── src/
├── models/
├── results/
├── README.md
└── requirements.txt
```

## Future Work

- Advanced augmentation strategies.
- Ensemble learning.
- Self-supervised pretraining.
- Explainable AI (Grad-CAM, Attention Maps).
