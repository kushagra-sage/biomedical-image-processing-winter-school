# Session: Bridging the Gap: Addressing Unmet Clinical and Technical Needs for AI Implementation in Hepatology

**Speaker:** Dr. Aziana Azman Abdullah
**Designation:** Associate Professor
**Organization:** University Malaysia Perlis, Malaysia
**Topic:** Deep Learning-Based Classification of Degenerative Spine Conditions from Lumbar MRI

---

## 1.0 Introduction: The Global Challenge of Low Back Pain and Diagnosis

Low back pain represents a significant and escalating global health issue, imposing a substantial burden on healthcare systems and diminishing the quality of life for millions. Since 1990, the number of reported cases has increased by approximately 60%, framing the problem as an accelerating crisis. This trend underscores the strategic importance of developing more accurate, efficient, and standardized diagnostic methods to ensure timely and effective patient care.

---

## 1.1 The Scale of the Problem

The prevalence of low back pain is substantial and projected to increase, highlighting the urgency of the problem. Key statistics presented by the speaker include:

* **Global Cases:** Approximately 619 million cases were reported worldwide in 2020.
* **Projected Growth:** This number is expected to rise to 843 million cases in the near future.
* **Prevalence by Age:**

  * 24.4% of adults aged 18–44
  * 33% of adults aged 45–64
  * 37.3% of adults aged 75 and older
* **Gender Disparity:** Studies indicate that low back pain affects women more frequently than men, a difference potentially linked to hormonal changes, particularly post-menopause.

---

## 1.2 Limitations of Manual Diagnosis

The current standard for diagnosing degenerative spine conditions relies on the manual interpretation of Magnetic Resonance Imaging (MRI) scans by radiologists. This process has several core limitations:

* **Subjectivity and Variability:**
  Manual interpretation is inherently subjective and can vary significantly between radiologists, leading to diagnostic errors and inconsistencies. This variability can result in inconsistent patient pathways where treatment effectiveness depends on the individual radiologist rather than standardized assessment.

* **Risk of Missing Early Detection:**
  Subtle, early-stage degenerative changes are often missed during manual review, delaying necessary interventions and worsening patient outcomes.

* **Data Complexity and Fatigue:**
  The large volume and complexity of MRI datasets can overwhelm radiologists, slowing diagnosis and increasing the risk of fatigue-related errors.

This research project was initiated to explore an automated, deep learning-based approach as a potential solution to these diagnostic challenges.

---

## 2.0 The Research Project: An Automated Approach to Spine Condition Analysis

This section outlines the research project presented by Dr. Abdullah, undertaken as a student’s final year project. The goal was to develop a practical AI-driven tool capable of automatically analyzing lumbar MRI scans to classify the severity of degenerative spine conditions.

---

## 2.1 Project Objectives

The research was guided by three primary objectives:

1. To implement data visualization and exploratory data analysis (EDA) techniques to understand the lumbar spine dataset.
2. To implement and compare deep learning models to detect and classify degenerative spine conditions from lumbar MRI data.
3. To develop a user-friendly Graphical User Interface (GUI) to automate the diagnostic process.

---

## 2.2 Project Scope

The project scope was clearly defined:

* **Data Source:**
  Large open-source dataset from the Radiological Society of North America (RSNA), available on Kaggle.

* **Technical Stages:**

  * Exploratory Data Analysis (EDA)
  * Image pre-processing
  * Deep learning model implementation

* **Final Deliverable:**
  A functional GUI capable of generating an automated diagnostic report from uploaded MRI images.

---

## 3.0 Background: Understanding the Medical Context

Understanding spinal anatomy and diagnostic imaging is essential to appreciating the AI methodology.

---

## 3.1 Degenerative Spine Conditions Explained

Degenerative spine conditions refer to gradual wear and tear of spinal structures, including discs, joints, and vertebrae. This process, often accelerated by aging, leads to chronic pain, discomfort, and reduced mobility.

---

## 3.2 The Role of MRI in Diagnosis

MRI is the most effective imaging technique for diagnosing degenerative spine conditions because it provides clear visualization of soft tissues.

### MRI Modalities and Conditions Detected

| MRI Modality       | Condition Detected       | Spinal Area                  |
| ------------------ | ------------------------ | ---------------------------- |
| Axial T2           | Subarticular Stenosis    | Lumbar Spine (Cross-Section) |
| Sagittal T1        | Neuroforaminal Narrowing | Lumbar Spine (Side View)     |
| Sagittal T2 / STIR | Spinal Canal Stenosis    | Lumbar Spine (Side View)     |

**Note:**

* Axial plane → top-down, cross-sectional view
* Sagittal plane → side view for alignment and disc space evaluation

---

## 4.0 Methodology: AI-Powered Workflow

---

## 4.1 Data Acquisition and Pre-processing

Dataset used: **RSNA 2024 Lumbar Spine Degenerative Classification** (147,218 MRI scans)

Pre-processing steps:

1. **DICOM to PNG Conversion**
   MRI scans converted to PNG for compatibility with deep learning frameworks.

2. **Data Condition Splitting**
   Images organized into folders for:

   * Neuroforaminal Narrowing
   * Subarticular Stenosis
   * Spinal Canal Stenosis

3. **ROI Cropping**
   Images cropped to retain only relevant spinal regions.

4. **Data Augmentation**
   Techniques such as noise injection and rotation applied to improve generalization and reduce overfitting.

---

## 4.2 Deep Learning Model Implementation

* **Object Detection:**
  YOLOv8 used to detect relevant spinal structures.

* **Severity Classification:**
  Severity levels: Normal/Mild, Moderate, Severe
  Models compared:

  * DeepScoreNet
  * Wide ResNet 28-10

---

## 4.3 Performance Evaluation Strategy

* **5-Fold Cross-Validation**

  * 80% training
  * 20% validation
  * Repeated five times

### Evaluation Metrics:

* Accuracy
* Precision
* Recall
* F1 Score

---

## 5.0 Key Findings and Results

---

## 5.1 Insights from Exploratory Data Analysis (EDA)

The dataset was highly imbalanced, with most cases labeled as **Normal/Mild**, and far fewer **Moderate** and **Severe** cases. This imbalance poses challenges for detecting rare but critical conditions.

---

## 5.2 Model Performance Comparison

| Spinal Condition         | DeepScoreNet | Wide ResNet 28-10 |
| ------------------------ | ------------ | ----------------- |
| Neuroforaminal Narrowing | 80.5%        | 84.6%             |
| Spinal Canal Stenosis    | 90.4%        | 91.3%             |
| Subarticular Stenosis    | 80.6%        | 82.0%             |

Wide ResNet 28-10 outperformed DeepScoreNet across all conditions.

---

## 5.3 Benchmarking Against Prior Research

| Spinal Condition         | Prior Study | Proposed Work |
| ------------------------ | ----------- | ------------- |
| Neuroforaminal Narrowing | 81.0%       | 84.6%         |
| Spinal Canal Stenosis    | 89.0%       | 91.3%         |
| Subarticular Stenosis    | 74.0%       | 82.0%         |

---

## 6.0 Practical Application: Diagnostic GUI

---

## 6.1 GUI Functionality

1. Upload MRI images
2. Click **Analyze**
3. View automated diagnostic report

---

## 6.2 Interpreting the Output

* Severity classification for lumbar levels (e.g., L2–L3, L3–L4)
* Clear recommendations (e.g., “See a spine specialist”)

---

## 7.0 Conclusion and Future Directions

---

## 7.1 Summary of Achievements

* Effective image pre-processing and augmentation
* Wide ResNet 28-10 identified as best model
* Outperformed prior benchmark studies
* Functional GUI developed

---

## 7.2 Acknowledged Limitations

* Unbalanced dataset
* Limited GPU availability
* Morphology-only analysis

---

## 7.3 Future Work

* Model optimization
* Smarter GUI automation
* Expanded clinical usability

---

## 8.0 Resources for Further Learning

* **Platform:** Kaggle
* **Dataset:** RSNA 2024 Lumbar Spine Degenerative Classification

---
