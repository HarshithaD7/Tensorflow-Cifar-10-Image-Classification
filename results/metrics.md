# Metrics — CIFAR-10 CNN Image Classification

## Environment
- Platform: Kaggle Notebook
- TensorFlow Version: **2.18.0**

## Dataset
- Train shape: **(50000, 32, 32, 3)**
- Train labels: **(50000,)**
- Test shape: **(10000, 32, 32, 3)**
- Test labels: **(10000,)**
- Classes printed: **10**

## Model Size (From Summary Output)
- Total params: **2,397,226 (9.14 MB)**
- Trainable params: **2,396,330 (9.14 MB)**
- Non-trainable params: **896 (3.50 KB)**

After saving & loading the model:
- Total params: **2,397,228 (9.14 MB)**
- Optimizer params: **2 (12.00 B)**

---

## Training Metrics — Baseline Training (5 Epochs)

| Epoch | Train Accuracy | Train Loss | Val Accuracy | Val Loss |
|------:|---------------:|-----------:|-------------:|---------:|
| 1 | 0.8362 | 0.4759 | 0.7773 | 0.7208 |
| 2 | 0.8700 | 0.3778 | 0.7345 | 0.8584 |
| 3 | 0.8869 | 0.3247 | 0.8158 | 0.5824 |
| 4 | 0.9062 | 0.2661 | 0.7971 | 0.7027 |
| 5 | 0.9180 | 0.2375 | 0.8137 | 0.6525 |

---

## Training Metrics — With Data Augmentation (5 Epochs)

| Epoch | Train Accuracy | Train Loss | Val Accuracy | Val Loss |
|------:|---------------:|-----------:|-------------:|---------:|
| 1 | 0.7811 | 0.6738 | 0.7963 | 0.6114 |
| 2 | 0.6562 | 0.9713 | 0.8008 | 0.6024 |
| 3 | 0.8108 | 0.5639 | 0.8171 | 0.5511 |
| 4 | 0.9062 | 0.2821 | 0.8170 | 0.5486 |
| 5 | 0.8292 | 0.5038 | 0.8282 | 0.5103 |

---

## Sample Prediction Verification
- Output shown in notebook:  
  **Original label is cat and predicted label is cat**
