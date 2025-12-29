# Project Report — CIFAR-10 Image Classification Using CNN

## 1. Problem Statement
The goal of this project is to classify small color images into one of **10 predefined object classes** using a **Convolutional Neural Network (CNN)**. CIFAR-10 images are low-resolution (**32×32**) but contain enough object-level patterns for a CNN to learn meaningful features.

## 2. Dataset Description
- Dataset: **CIFAR-10**
- Total images: **60,000**
  - Training images: **50,000**
  - Test images: **10,000**
- Image size: **32×32**
- Channels: **3 (RGB)**
- Classes: **10**
  - airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck

### Confirmed Dataset Shapes (Notebook Output)
- Train: **(50000, 32, 32, 3)**
- Train labels: **(50000,)**
- Test: **(10000, 32, 32, 3)**
- Test labels: **(10000,)**

## 3. Tools & Environment
- Platform: **Kaggle Notebook**
- TensorFlow version printed: **2.18.0**
- Libraries used:
  - TensorFlow / Keras
  - NumPy
  - Matplotlib
  - pickle, os (for loading CIFAR batch files locally)

## 4. Methodology

### 4.1 Data Loading (Offline Kaggle Input)
Instead of downloading CIFAR-10 using internet access, the dataset is loaded directly from the Kaggle input folder:
- Local root folder used:
  `/kaggle/input/cifar-10-image/cifar-10-batches-py`

The batch files were unpickled and concatenated into full training and test arrays.

### 4.2 Preprocessing
- Pixel values scaled from **0–255** to **0–1**:
  - `x_train, x_test = x_train/255.0, x_test/255.0`
- Labels flattened:
  - `y_train, y_test = y_train.flatten(), y_test.flatten()`
- A 5×5 image grid was plotted to validate correct loading and label alignment.

## 5. Model Architecture
A CNN was built using TensorFlow Keras Functional API:

- Convolution Block 1:
  - Conv2D(32) → BatchNorm → Conv2D(32) → BatchNorm → MaxPool
- Convolution Block 2:
  - Conv2D(64) → BatchNorm → Conv2D(64) → BatchNorm → MaxPool
- Convolution Block 3:
  - Conv2D(128) → BatchNorm → Conv2D(128) → BatchNorm → MaxPool
- Flatten
- Dropout(0.2)
- Dense(1024, ReLU) + Dropout(0.2)
- Dense(10, Softmax)

### Model Size (Notebook Summary Output)
- Total params: **2,397,226 (9.14 MB)**
- Trainable params: **2,396,330 (9.14 MB)**
- Non-trainable params: **896 (3.50 KB)**

## 6. Training Setup

### Compilation
- Optimizer: **Adam**
- Loss: **sparse_categorical_crossentropy**
- Metric: **accuracy**

### Baseline Training (5 epochs)
| Epoch | Train Accuracy | Train Loss | Val Accuracy | Val Loss |
|------:|---------------:|-----------:|-------------:|---------:|
| 1 | 0.8362 | 0.4759 | 0.7773 | 0.7208 |
| 2 | 0.8700 | 0.3778 | 0.7345 | 0.8584 |
| 3 | 0.8869 | 0.3247 | 0.8158 | 0.5824 |
| 4 | 0.9062 | 0.2661 | 0.7971 | 0.7027 |
| 5 | 0.9180 | 0.2375 | 0.8137 | 0.6525 |

### Training With Data Augmentation (5 epochs)
Augmentation used:
- width_shift_range = **0.1**
- height_shift_range = **0.1**
- horizontal_flip = **True**
- batch_size = **32**

| Epoch | Train Accuracy | Train Loss | Val Accuracy | Val Loss |
|------:|---------------:|-----------:|-------------:|---------:|
| 1 | 0.7811 | 0.6738 | 0.7963 | 0.6114 |
| 2 | 0.6562 | 0.9713 | 0.8008 | 0.6024 |
| 3 | 0.8108 | 0.5639 | 0.8171 | 0.5511 |
| 4 | 0.9062 | 0.2821 | 0.8170 | 0.5486 |
| 5 | 0.8292 | 0.5038 | 0.8282 | 0.5103 |

## 7. Evaluation & Verification

### Accuracy Curve
A plot was generated comparing:
- Training accuracy (`acc`)
- Validation accuracy (`val_acc`)

### Single Image Prediction Check (Notebook Output)
A sample from the test set was predicted and matched correctly:
- **Original label is cat and predicted label is cat**

## 8. Model Saving & Reloading
The trained model was saved as:
- `cifar10_cnn_model.h5`

Reloading the model was successful and produced a valid summary with:
- Total params: **2,397,228 (9.14 MB)**
- Optimizer params: **2 (12.00 B)**

## 9. Conclusion
- Baseline training ended at validation accuracy **0.8137**
- Data augmentation improved final validation accuracy to **0.8282**
- The project proves CNNs can learn meaningful features even from low-resolution images (32×32) and benefit from augmentation for better generalization.

## 10. Future Improvements
- Add early stopping and learning rate scheduling
- Use a confusion matrix + classification report
- Try deeper architectures (ResNet-like blocks)
- Train longer with stable generator batching and improved augmentation pipeline
