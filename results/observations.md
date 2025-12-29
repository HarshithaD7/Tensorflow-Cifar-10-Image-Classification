# Observations — CIFAR-10 CNN Image Classification

## Dataset Loading & Preprocessing
- CIFAR-10 was loaded locally from Kaggle input and confirmed with shapes:
  - Train: **(50000, 32, 32, 3)**, Labels: **(50000,)**
  - Test: **(10000, 32, 32, 3)**, Labels: **(10000,)**
- Pixel values were normalized to **0–1** using division by **255.0**
- Labels were flattened to 1D arrays using `flatten()`
- A 5×5 grid visualization was generated to confirm input images are being read correctly.

## Model Architecture Observations
- The CNN uses 3 convolution blocks (32 → 64 → 128 filters), each with:
  - Conv2D + BatchNormalization
  - MaxPooling to reduce spatial size
- Dense layers include Dropout which helps reduce overfitting.
- Model size from summary:
  - **2,397,226 parameters**
  - Very low non-trainable params: **896**

## Training Behavior — Baseline Fit (5 epochs)
- Training accuracy improved steadily from **0.8362 → 0.9180**
- Validation accuracy varied:
  - Lowest val_accuracy: **0.7345** (Epoch 2)
  - Highest val_accuracy: **0.8158** (Epoch 3)
  - Final val_accuracy: **0.8137**
- Validation loss fluctuated (0.7208 → 0.8584 → 0.5824 → 0.7027 → 0.6525), indicating some instability and possible overfitting in certain epochs.

## Training Behavior — Data Augmentation Fit (5 epochs)
- Data augmentation improved final validation accuracy:
  - Final val_accuracy: **0.8282**
  - Final val_loss: **0.5103**
- There is a visible interruption warning in Epoch 2 (augmentation stage):
  - Training got interrupted due to generator running out of data.
  - Despite this, validation accuracy still increased overall and ended at the best value shown: **0.8282**

## Model Output Verification
- A manual single-image test was done from the test set:
  - Output: **Original label is cat and predicted label is cat**
- Model was saved as: `cifar10_cnn_model.h5`
- Reloading the saved model produced a valid summary with:
  - Total params: **2,397,228**
  - Optimizer params: **2 (12.00 B)**

## Key Takeaway
- Baseline training ended with **val_accuracy = 0.8137**
- Augmented training ended with **val_accuracy = 0.8282**
- Data augmentation helped improve generalization on the test set.
