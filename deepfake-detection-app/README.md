# Explainable Deepfake Image Detection System

An end-to-end AI system for detecting AI-generated deepfake images using **Transfer Learning with EfficientNet**, enhanced with **Explainable AI (Grad-CAM)** and deployed as a **real-time web application**.

---

## Problem Statement

Deepfake images generated using advanced AI techniques are increasingly being used for:

- Misinformation and fake news  
- Identity fraud and impersonation  
- Cybercrime and digital manipulation  

Human visual inspection is unreliable for detecting such manipulations.  
This project aims to build an **automated, accurate, and explainable deepfake detection system**.

---

## Applications

- Social media content moderation  
- Digital forensic investigations  
- Fake identity prevention  
- News authenticity verification  
- Cybersecurity monitoring  

---

## Dataset

- Approximately **10,000 images**
- Two classes: **Real** and **Fake**
- Balanced dataset
- Split into **training and validation sets**
- Images resized to **256×256** to preserve subtle facial artifacts used for deepfake detection

### Preprocessing

- Normalization  
- EfficientNet preprocessing  
- Data augmentation  

---

## Baseline CNN Model

A custom Convolutional Neural Network was implemented as a baseline:

- 3 convolutional layers with pooling  
- Fully connected classifier  
- Sigmoid activation  

### Results

- Training Accuracy: ~94%  
- Validation Accuracy: ~75%  
- Overfitting observed  

This motivated the transition to **transfer learning**.

---

## Transfer Learning with EfficientNet

- Used **EfficientNetB0 pretrained on ImageNet**
- Leveraged pretrained visual features
- Improved convergence and generalization

EfficientNet provides powerful feature extraction capabilities, making it highly suitable for **detecting subtle visual artifacts present in deepfake images**.

---

## Data Augmentation

To improve generalization and robustness, the following augmentation techniques were applied:

- Random horizontal flipping  
- Random rotation  
- Random zoom  
- Random contrast adjustments  

Benefits:

- Reduces overfitting  
- Simulates real-world image variations  
- Improves model robustness  

---

## Model Optimization

Several techniques were applied to improve performance:

- Increased input resolution **224×224 → 256×256**
- Fine-tuned the **last 80 layers of EfficientNet**
- Added **Batch Normalization and Dropout (0.5)** for regularization
- Applied **Label Smoothing** to prevent overconfident predictions
- Implemented **learning rate scheduling (ReduceLROnPlateau)**

These optimizations improved validation accuracy from **~85% to ~91%**.

---

## Freezing & Fine Tuning Strategy

### Step 1 – Freeze backbone
- EfficientNet layers frozen
- Only classifier layers trained

### Step 2 – Fine tuning
- Backbone partially unfrozen
- Small learning rate applied

### Step 3 – Partial unfreezing
- Fine-tuned deeper layers only
- Allowed model to adapt to deepfake-specific artifacts

---

## Final Performance

After optimization and fine tuning:

- Training Accuracy: **~92%**
- Validation Accuracy: **~91%**
- Balanced dataset (~10k images)
- Minimal overfitting observed

---

## Explainable AI (Grad-CAM)

Grad-CAM (Gradient-weighted Class Activation Mapping) was implemented to visualize the regions influencing the model's decision.

Benefits:

- Highlights manipulated facial regions
- Improves transparency of predictions
- Supports digital forensic interpretation

---

## Forensic Intelligence Layer

The system includes additional reasoning features:

- Full-image + face-based predictions
- Confidence estimation
- Reliability scoring
- Consistency analysis
- Artifact indicators based on heatmap patterns

---

## Web Application Features

The deepfake detector is deployed as a **Flask web application** with the following features:

- Batch image upload
- Real-time inference
- Face detection using OpenCV
- Grad-CAM heatmap visualization
- Dual analysis:
  - Full image prediction
  - Face-only prediction
- Confidence and reliability scoring
- Automated **forensic PDF report generation**
- Detection history logging

---

## Screenshots

### Detection Interface
![Detection UI](screenshots/ui.png)

### Grad-CAM Heatmap
![GradCAM](screenshots/gradcam.png)

### Forensic Report
![Report](screenshots/report.png)

---

## Project Structure

```
deepfake-ai/
│
├── templates/
│   ├── base.html
│   ├── detect.html
│   ├── history.html
│
├── screenshots/
│
├── static/
│   ├── style2.css
│   └── app.js
│
├── app.py
├── requirements.txt
└── README.md
```

---

## Installation

### 1. Clone repository

```bash
git clone https://github.com/yourusername/deepfake-ai.git
cd deepfake-ai
```

### 2. Create virtual environment

```bash
python -m venv venv
source venv/bin/activate
# Windows
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Application

```bash
python app.py
```

Then open:

```
http://127.0.0.1:5000/
```

---

## Technologies Used

- Python
- TensorFlow / Keras
- EfficientNetB0 (Transfer Learning)
- OpenCV (Face Detection)
- Flask (Web Deployment)
- NumPy
- Grad-CAM (Explainable AI)
- ReportLab (PDF Generation)
- HTML, CSS, JavaScript

---

## Future Improvements

- Larger deepfake datasets
- Video deepfake detection
- Real-time webcam analysis
- Vision Transformers
- Cloud deployment

---

## Conclusion

This project demonstrates a complete **explainable AI pipeline for deepfake detection**, combining deep learning, model interpretability, and real-time deployment.

The system achieves **~91% validation accuracy** while providing **transparent forensic insights through Grad-CAM visualization and automated reporting**.
