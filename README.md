# CIFAR-10 Image Classification Using CNN (Keras / TensorFlow)

## Abstract / Description
This project implements **image classification on the CIFAR-10 dataset** using a **Convolutional Neural Network (CNN)** built with **TensorFlow/Keras**.  
CIFAR-10 contains **60,000 color images (32×32)** across **10 classes**: airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck.

The full pipeline includes:
- Loading CIFAR-10 **directly from Kaggle input directory (offline, no internet download)**
- Image normalization (0–255 → 0–1)
- CNN model building using the Functional API
- Training (baseline + data augmentation)
- Accuracy plotting
- Single image prediction verification
- Saving and re-loading the trained model (`.h5`)

## Objectives
- Load CIFAR-10 dataset locally from Kaggle input folder
- Preprocess images and labels for CNN training
- Build a deep CNN with convolution blocks + batch normalization + dropout
- Train and validate the model for multiple epochs
- Apply data augmentation to improve generalization
- Visualize training/validation accuracy trends
- Validate model prediction on a sample image
- Save the trained model and reload it successfully

## Setup Steps (Kaggle Notebook)
1. Open Kaggle Notebook
2. Add dataset as Kaggle input: `cifar-10-image`
3. Run notebook cells in order (imports → dataset load → preprocessing → model training → augmentation → evaluation → save/load)

## Usage (How to Run)
- Run the notebook inside `src/` sequentially.
Key outputs produced during execution:
- TensorFlow version: **2.18.0**
- Dataset shapes: **(50000, 32, 32, 3), (50000,), (10000, 32, 32, 3), (10000,)**
- Model has **10 classes**
- Training logs for baseline training and augmented training
- Accuracy plot
- Sample prediction output:
  - **Original label is cat and predicted label is cat**
- Saved model file:
  - `cifar10_cnn_model.h5`

## Results (Exact Values From Notebook Output)

### Dataset Loaded
- Training data: **(50000, 32, 32, 3)**
- Training labels: **(50000,)**
- Test data: **(10000, 32, 32, 3)**
- Test labels: **(10000,)**
- Number of classes printed: **10**

### Model Architecture Summary (Key Values)
- Total parameters: **2,397,226 (9.14 MB)**
- Trainable parameters: **2,396,330 (9.14 MB)**
- Non-trainable parameters: **896 (3.50 KB)**

After saving & reloading model:
- Total parameters: **2,397,228 (9.14 MB)**
- Optimizer params: **2 (12.00 B)**

### Training Logs (Baseline fit - 5 epochs)
- Epoch 1: accuracy **0.8362**, loss **0.4759**, val_accuracy **0.7773**, val_loss **0.7208**
- Epoch 2: accuracy **0.8700**, loss **0.3778**, val_accuracy **0.7345**, val_loss **0.8584**
- Epoch 3: accuracy **0.8869**, loss **0.3247**, val_accuracy **0.8158**, val_loss **0.5824**
- Epoch 4: accuracy **0.9062**, loss **0.2661**, val_accuracy **0.7971**, val_loss **0.7027**
- Epoch 5: accuracy **0.9180**, loss **0.2375**, val_accuracy **0.8137**, val_loss **0.6525**

### Training Logs (With data augmentation - 5 epochs)
- Epoch 1: accuracy **0.7811**, loss **0.6738**, val_accuracy **0.7963**, val_loss **0.6114**
- Epoch 2: accuracy **0.6562**, loss **0.9713**, val_accuracy **0.8008**, val_loss **0.6024**
- Epoch 3: accuracy **0.8108**, loss **0.5639**, val_accuracy **0.8171**, val_loss **0.5511**
- Epoch 4: accuracy **0.9062**, loss **0.2821**, val_accuracy **0.8170**, val_loss **0.5486**
- Epoch 5: accuracy **0.8292**, loss **0.5038**, val_accuracy **0.8282**, val_loss **0.5103**

### Sample Prediction Output
- **Original label is cat and predicted label is cat**

## Repository Structure (As Per Assignment)
- `src/` → notebook implementation (`.ipynb`)
- `data/` → dataset info note (dataset loaded via Kaggle input)
- `docs/` → detailed report (`report.md`)
- `results/` → metrics + observations + screenshots
- `.gitignore` and `LICENSE` (optional)

## Files to Check
- `results/metrics.md`
- `results/observations.md`
- `docs/report.md`
- `results/screenshots/` (training logs, plots, prediction proof, model summary)
