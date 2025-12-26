# Applied AI Research Projects in Medical Image Analysis  
**Speaker: Dr. Daphne**

---

## 1. Overview of the Session

Dr. Daphne’s presentation focused on how artificial intelligence is applied to real-world medical imaging problems. Instead of concentrating on a single algorithm, the session covered four applied student research projects, each addressing a different challenge commonly encountered in medical AI.

A central message of the session was that medical AI must operate under practical constraints such as limited data access, patient privacy, interpretability, and clinical complexity. High accuracy alone is insufficient; AI systems must also be trustworthy, explainable, and clinically usable.

---

## 2. Cross-Project Themes

Several recurring themes emerged across all four projects:

- Public datasets play a crucial role due to difficulties in accessing hospital data caused by privacy and legal restrictions.
- Explainable AI (XAI) is treated as a necessity rather than an optional feature, with tools like LIME and Grad-CAM used to support clinical trust.
- The projects reflect increasing clinical complexity, progressing from simple classification tasks to prognosis, privacy-preserving learning, and multi-disease detection.

---

## 3. Project 1: Ischemic Stroke Classification Using DenseNet

### 3.1 Motivation

The project aimed to support clinicians by detecting ischemic stroke from CT scans. Early diagnosis is critical, and AI can provide a reliable second opinion. The project was personally motivated, as the student researcher had experienced ischemic stroke himself.

### 3.2 Methodology

- DenseNet-121 architecture was used to mitigate vanishing gradient issues.
- Dataset consisted of approximately 2,500 CT scans from 130 patients (Kaggle).
- Eight experiments tested different preprocessing techniques such as Gaussian blur and erosion.
- One experiment acted as a baseline with no preprocessing.

### 3.3 Results

- Baseline model achieved an F1 score of 0.87.
- Applying erosion improved the F1 score to 0.89, showing the impact of preprocessing.

### 3.4 Explainability and Limitations

- LIME was used to analyze model focus areas.
- Activations were consistent within the skull, especially midbrain and lower brain regions.
- A major limitation was the absence of ground truth annotations for stroke regions.

### 3.5 CT vs MRI Discussion

- MRI datasets were difficult to obtain.
- CT scans are faster and more suitable for emergency stroke diagnosis.

---

## 4. Project 2: Alzheimer’s Cognitive Score Prediction

### 4.1 Objective

The project focused on predicting future cognitive decline rather than simple disease classification by forecasting survey scores at month 24.

### 4.2 Methodology

- Vision Transformer (ViT) used for feature extraction.
- Weighted multitask learning framework predicted multiple survey scores.
- Strong, moderated, and uniform weighting strategies were evaluated.

### 4.3 Dataset and Preprocessing

- ADNI cohort 1 dataset was used.
- Image registration and normalization were performed using ANTs.

### 4.4 Results and Challenges

- Strong weighted models performed best internally.
- Performance was weaker for early Alzheimer’s patients, highlighting the difficulty of early-stage prognosis.

---

## 5. Project 3: Diabetic Retinopathy Detection Using Federated Learning

### 5.1 Motivation

The project addressed data privacy by using federated learning, allowing training across institutions without sharing raw data.

### 5.2 Federated Learning Workflow

1. Local model training
2. Weight sharing
3. Global aggregation
4. Model update

### 5.3 Model and Dataset

- U-Net for segmentation
- Xception V3 for classification
- Indian Diabetic Retinopathy Image Dataset

### 5.4 Results

- Federated learning achieved approximately 98% accuracy.
- Performance exceeded non-federated approaches, demonstrating privacy-preserving effectiveness.

---

## 6. Project 4: Multi-label Chest X-ray Classification with Improved Grad-CAM

### 6.1 Clinical Motivation

Patients often present with multiple simultaneous conditions, making single-label classification unrealistic.

### 6.2 Architectural Modifications

- Multi-class classifier replaced with multiple binary classifiers.
- Disease-specific gradients enabled clearer explainability.

### 6.3 Explainability and Results

- Separate Grad-CAM heatmaps were generated per disease.
- Accuracy ranged between 70–80%.
- Some localization errors remained, marking the project as ongoing.

---

## 7. Summary

Dr. Daphne’s session illustrated how applied medical AI research evolves from basic classification toward clinically realistic, privacy-aware, and explainable systems. Each project addressed real limitations faced in healthcare AI deployment.
