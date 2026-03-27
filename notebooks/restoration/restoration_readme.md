# Restoration Module — Training Strategy and Implementation

## Overview

The restoration stage is designed to recover visual information lost due to real-world degradations such as blur, rain, and exposure issues. This module plays a critical role in improving the quality of inputs before they are processed by detection and classification models.

Most restoration models in this pipeline are based on the Restormer architecture and are adapted using transfer learning and task-specific fine-tuning strategies.

---

## Degradation Types

### Blur
Blur is caused by motion or defocus, leading to loss of sharpness and unclear object boundaries.

### Exposure
Exposure degradation includes both under-exposure (dark regions losing detail) and over-exposure (bright regions becoming saturated), reducing contrast and visibility.

### Rain
Rain introduces streaks and occlusions that obscure scene content and reduce overall clarity.

---

## Pretrained Initialization

Most models are initialized using pretrained Restormer checkpoints trained on large-scale and diverse restoration datasets. These pretrained weights capture general image priors such as edges, textures, and structural patterns.

This initialization:

- Reduces training time
- Improves convergence stability
- Helps prevent overfitting

---

## Task-Specific Fine-Tuning

### Deblurring

For defocus deblurring, the model is fine-tuned on lens blur data. This allows the network to learn both spatially varying defocus patterns (lens blur) and more uniform smoothing effects (Gaussian blur).

### Deraining

For rain removal, the model is fine-tuned on rain-degraded images. The network learns rain-specific patterns such as streak direction, intensity variation, and occlusion behavior.

### Generalization vs Specialization

Fine-tuning enables specialization for each degradation type while preserving general visual features from pretraining. This balance ensures restored outputs remain consistent and useful for downstream tasks.

---

## Exposure Restoration

Unlike deblurring and deraining, Restormer does not provide pretrained checkpoints specifically for exposure correction. Exposure degradation is closely related to luminance distribution and dynamic range, making it more challenging to model.

### Transfer Learning Setup

To address this, the model is initialized from a Restormer checkpoint trained on motion blur (DIV2K dataset). This provides a strong baseline for learning structural and textural features.

### Synthetic Data Generation

Due to the lack of real paired exposure datasets, synthetic exposure degradations are applied to the DIV2K dataset. These include:

- Brightness reduction
- Saturation
- Contrast compression

This allows controlled and supervised training.

### Limitations

While this approach improves visibility, performance is lower compared to deblurring and deraining. Exposure correction requires luminance-aware modeling and dynamic range understanding, which are not fully captured by standard pixel-wise loss functions.

---

## Fine-Tuning Strategy

A decoder-first fine-tuning strategy is used:

- Encoder layers are frozen initially
- Training focuses on decoder and refinement blocks

This preserves pretrained representations while adapting reconstruction layers to specific degradations.

---

## Training Configuration

- **Input:** 256 × 256 patches
- **Batch size:** 2
- **Gradient accumulation:** 4 steps
- **Optimizer:** AdamW
  - Learning rate: 2 × 10⁻⁴
  - Weight decay: 1 × 10⁻²

### Training Process

- Maximum epochs: 40
- Early stopping:
  - Patience: 6 epochs
  - Minimum improvement: 0.05
  - Early fluctuations are ignored to ensure stable convergence

### Mixed Precision Training

Automatic Mixed Precision (AMP) is enabled to:

- Reduce memory usage
- Improve training speed
- Maintain numerical stability

---

## Summary

The restoration module uses pretrained initialization and task-specific fine-tuning to adapt a single architecture to multiple degradation types. While deblurring and deraining perform strongly, exposure restoration remains more challenging due to its dependence on luminance and dynamic range.

Overall, this approach provides a flexible and scalable solution for integrating image restoration into a full perception pipeline.