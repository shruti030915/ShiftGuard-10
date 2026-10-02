# ShiftGuard-10: Robust Image Classification

## Overview

ShiftGuard-10 is a robust image classification project developed as part of an image classification competition.

The objective was to classify 32×32 RGB images into 10 classes while maintaining strong Macro F1 performance under class imbalance and distribution shift.

## Problem Statement

The task is to classify low-resolution RGB images into one of 10 classes:

- airplane
- automobile
- bird
- cat
- deer
- dog
- frog
- horse
- ship
- truck

The primary evaluation metric is Macro F1-score.

## Challenges

The dataset presented several challenges:

- Low-resolution 32×32 RGB images
- Class imbalance
- Distribution shift between training and test data
- Limited spatial information

## Approach

The project followed a progressive model improvement strategy.

### 1. Baseline

A WideResNet-28-10 architecture was used as the initial model.

### 2. Class Balancing

Weighted sampling and class-frequency-aware loss adjustments were introduced to reduce bias toward majority classes.

### 3. Data Augmentation

The training pipeline incorporated:

- Random Crop
- Horizontal Flip
- AutoAugment
- Patch Masking

### 4. Advanced Regularization

To improve generalization:

- MixUp
- CutMix
- Label Smoothing

were incorporated into training.

### 5. Optimization

The model was trained using:

- AdamW
- Weight Decay
- Warm-up Learning Rate
- Cosine Learning Rate Scheduling
- Gradient Clipping

### 6. Model Averaging

Stochastic Weight Averaging (SWA) was used to improve model stability.

### 7. Test-Time Augmentation

Test-Time Augmentation (TTA) was used during inference to reduce prediction variance.

## Training Pipeline

```text
Input Images
     ↓
Data Preprocessing
     ↓
Class-Balanced Sampling
     ↓
Data Augmentation
     ↓
WideResNet-28-10
     ↓
MixUp / CutMix
     ↓
Label Smoothing
     ↓
AdamW + Cosine LR
     ↓
Stochastic Weight Averaging
     ↓
Test-Time Augmentation
     ↓
Final Predictions
