# 🧠 Brain Tumor Detection

A deep learning-based **Brain Tumor Detection and Classification** system that analyzes MRI brain scans and classifies them into four categories using **VGG16 Transfer Learning**.

The project includes image preprocessing, augmentation, model training, evaluation using classification metrics and a confusion matrix, and prediction on new MRI images.

---

## 📌 Overview

Brain tumor classification from MRI scans is an image classification problem where different tumor types can have visually similar characteristics.

This project uses a pretrained **VGG16 convolutional neural network** and transfer learning to classify MRI images into:

* 🧠 **Glioma**
* 🧠 **Meningioma**
* 🧠 **Pituitary Tumor**
* ✅ **No Tumor**

The model learns visual patterns from the MRI images and predicts the most likely class for a given scan.

---

## 🎯 Objectives

* Process and prepare MRI brain images for deep learning.
* Apply basic image augmentation to improve training data variety.
* Use **VGG16 transfer learning** for feature extraction and classification.
* Train a four-class MRI image classifier.
* Evaluate model performance using:

  * Classification Report
  * Confusion Matrix
  * Training Accuracy
  * Training Loss
* Save the trained model for later predictions.
* Test the model on individual MRI images.

---

## 🗂️ Dataset

The project uses the **Brain Tumor MRI Dataset** available through Kaggle.

Dataset:

**Brain Tumor MRI Dataset — Masoud Nickparvar**

The dataset is organized into:

```text
Training/
├── glioma/
├── meningioma/
├── notumor/
└── pituitary/

Testing/
├── glioma/
├── meningioma/
├── notumor/
└── pituitary/
```

The notebook downloads the dataset using `kagglehub`.

---

## ⚙️ Technologies Used

| Technology         | Purpose                        |
| ------------------ | ------------------------------ |
| Python             | Main programming language      |
| TensorFlow / Keras | Deep learning framework        |
| VGG16              | Transfer learning model        |
| NumPy              | Numerical operations           |
| OpenCV / PIL       | Image processing               |
| Matplotlib         | Visualization                  |
| Seaborn            | Confusion matrix visualization |
| Scikit-learn       | Model evaluation               |
| KaggleHub          | Dataset download               |
| Google Colab       | Development environment        |

---

## 🔄 Project Workflow

```text
MRI Dataset
     ↓
Dataset Download
     ↓
Load Training & Testing Images
     ↓
Shuffle Dataset
     ↓
Image Visualization
     ↓
Image Preprocessing
     ↓
Brightness & Contrast Augmentation
     ↓
VGG16 Transfer Learning
     ↓
Model Training
     ↓
Model Evaluation
     ↓
Confusion Matrix & Classification Report
     ↓
Save Trained Model
     ↓
Predict New MRI Images
```

---

## 🧹 Image Preprocessing

Before feeding images into the model:

1. Images are resized to **128 × 128 pixels**.
2. Pixel values are normalized to the range **0–1**.
3. Training images receive random:

   * Brightness adjustment
   * Contrast adjustment
4. Labels are encoded into numerical classes.

Example:

```text
glioma     → 0
meningioma → 1
notumor    → 2
pituitary  → 3
```

The exact numerical mapping is generated from the sorted dataset folder names.

---

## 🧠 Model Architecture

The project uses **VGG16 pretrained on ImageNet** as the base model.

Most of the pretrained layers are frozen, while a few deeper layers are made trainable for fine-tuning.

The classification architecture is:

```text
Input Image
    ↓
128 × 128 × 3
    ↓
VGG16
    ↓
Flatten
    ↓
Dropout (0.3)
    ↓
Dense (128, ReLU)
    ↓
Dropout (0.2)
    ↓
Dense (4, Softmax)
    ↓
Predicted Class
```

### Training Configuration

```text
Optimizer: Adam
Learning Rate: 0.0001
Batch Size: 20
Epochs: 5
Loss: Sparse Categorical Crossentropy
```

---

## 📊 Model Evaluation

The trained model is evaluated using the testing dataset.

### Classification Report

The classification report provides:

* Precision
* Recall
* F1-score
* Support

This helps evaluate how well the model performs for each tumor category.

### Confusion Matrix

A confusion matrix is generated to visualize:

```text
Actual Class
     ↓
Predicted Class
```

It helps identify which tumor categories are being classified correctly and where the model makes mistakes.

---

## 🔍 Prediction

After training, the model is saved as:

```text
model.h5
```

The trained model can then be loaded and used to classify individual MRI images.

Example output:

```text
Tumor: glioma
Confidence: XX.XX%
```

or

```text
No Tumor
Confidence: XX.XX%
```

The notebook also allows users to upload their own MRI image through Google Colab and obtain a prediction.

---

## 📸 Project Screenshots

### Dataset Visualization

![Dataset Visualization](screenshots/dataset.png)

### Training Results

![Training Results](screenshots/training.png)

### Confusion Matrix

![Confusion Matrix](screenshots/confusion_matrix.png)

### MRI Prediction

![Prediction](screenshots/prediction.png)

> Update the screenshot filenames above to match the files you upload to the repository.

---

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone https://github.com/atharvtamboli/Brain-Tumor-Detection.git
cd Brain-Tumor-Detection
```

### 2. Open the notebook

Open:

```text
brain_tumor_detection.ipynb
```

The recommended environment is **Google Colab**.

### 3. Run the notebook

The notebook will:

* Download the dataset through KaggleHub
* Prepare the images
* Train the VGG16-based model
* Evaluate the model
* Save the trained model
* Perform sample predictions

---

## 📁 Repository Structure

```text
Brain-Tumor-Detection/
│
├── brain_tumor_detection.ipynb
├── model.h5
├── README.md
│
├── report/
│   └── Brain_Tumor_Detection_Report.pdf
│
└── screenshots/
    ├── dataset.png
    ├── training.png
    ├── confusion_matrix.png
    └── prediction.png
```

---

## 📄 Project Report

The detailed project report is available here:

```text
report/Brain_Tumor_Detection_Report.pdf
```

It contains the methodology, implementation details, results, and project analysis.

---

## ⚠️ Disclaimer

This project is intended for **educational and research purposes only**.

The predictions generated by this model should **not be considered a medical diagnosis** and should not be used as a substitute for evaluation by qualified medical professionals.

---

## 👨‍💻 Author

**Atharv Tamboli**

B.Tech Computer Science
SRM Institute of Science and Technology

---

⭐ If you find this project useful, consider giving the repository a star.
