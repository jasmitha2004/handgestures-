# ✋ Hand Gesture Recognition using PyTorch

> 🧠 A PyTorch-based hand gesture image classification project implemented in a single Google Colab notebook.

---

## 🌟 Project Overview

This project uses a custom **Convolutional Neural Network (CNN)** to classify hand-gesture images from an annotated image dataset.

The complete workflow is implemented in:

📓 **`Hand_Gesture_PyTorch.ipynb`**

The notebook covers the complete machine-learning pipeline:

**Dataset → Preprocessing → CNN → Training → Evaluation → Prediction**

---

## 🚀 Workflow

```text
📦 Annotated Dataset ZIP
          ↓
📂 Extract Train / Valid / Test Data
          ↓
📄 Read Annotation CSV Files
          ↓
✂️ Crop Images Using Bounding Boxes
          ↓
🏷️ Create Class Folders
          ↓
🖼️ Resize Images to 128 × 128
          ↓
🔄 Data Augmentation
          ↓
🧠 PyTorch CNN
          ↓
🏋️ Model Training
          ↓
📊 Validation / Evaluation
          ↓
📈 Classification Report + Confusion Matrix
          ↓
💾 Save Trained Model (.pth)
          ↓
🔍 Predict a New Image
