## Session: Traditional vs. Customized CNN for Image Analysis

**Speaker:** Dr. Sulagna Mohapatra  
**Designation:** AI & Automation Strategic Architect  
**Organization:** Volktek Corporation, Taiwan  

---

## 1.0 Introduction to the Session

This session serves as a continuation of the earlier discussion on image pre-processing and shifts focus to the **core principles of image analysis using Convolutional Neural Networks (CNNs)**. The primary objective is to build a foundational understanding of how a CNN analyzes images, from defining the problem to constructing a complete model.

The discussion covered:
- Fundamental computer vision tasks
- Types of CNN architectures
- A step-by-step breakdown of CNN construction

The speaker noted that this session and the following one are **continuous**, with a **combined question-and-answer session** planned at the end of the second part to ensure a holistic understanding of the CNN workflow.

---

## 2.0 Fundamental Tasks in Medical Image Analysis

A critical first step in any AI project is translating a clinician’s qualitative problem into a **well-defined computer vision task**. The speaker explained that most medical image analysis problems fall into one of the following four categories.

---

### 2.1 Classification

**Core Question:** *What is the object?*

- Assigns a single label to the entire image.
- Considered the most fundamental computer vision task.

**Medical Examples:**
- Classifying lung nodules as **benign or malignant**
- Identifying **normal vs. ischemic stroke** cases from brain scans

---

### 2.2 Classification + Localization

**Core Question:** *What is the object, and where is it?*

- Extends classification by adding a **single bounding box** around the object.
- Typically used when only one primary object is present.

**Medical Example:**
- In her second research paper, after classifying ischemic stroke, the model drew a bounding box around the affected brain region.

---

### 2.3 Detection

**Core Question:** *What are the objects, and where are they?*

- Detects **multiple objects**, each with its own bounding box.
- Supports multiple object classes within the same image.

**Medical Examples:**
- Detecting multiple liver cysts
- Identifying both a cyst and a hemangioma in one scan

---

### 2.4 Segmentation

**Core Question:** *What is the precise shape, size, and boundary of the object?*

- Provides **pixel-level delineation** instead of bounding boxes.
- Essential for accurate quantitative analysis.

**Medical Examples:**
- Measuring tumor volume for treatment planning
- Differentiating infarcted tissue from penumbra in stroke cases

---

These four tasks are powered by the same underlying deep learning framework: **Convolutional Neural Networks**.

---

## 3.0 The Universal Architecture of CNNs

From a developer’s perspective, all CNN-based image analysis models share a **two-part universal architecture**.

### 3.1 Feature Extractor
- Composed of convolutional and pooling layers
- Learns hierarchical features such as edges, textures, and shapes
- Analogous to how humans distinguish objects using visual cues

### 3.2 Classifier / Prediction Head
- Consists of fully connected (dense) layers
- Converts extracted features into final predictions

This separation allows engineers to reuse or modify parts of a network efficiently.

---

## 4.0 Taxonomy of CNN Models

CNNs can be categorized based on **architecture design** and **implementation strategy**.

---

### 4.1 Structural Categories

#### Sequential CNN
- Linear stack of layers
- Simple and easy to implement
- Examples: **AlexNet**, **VGG16**
- The “16” in VGG16 refers to **13 convolutional + 3 fully connected layers**

#### Functional CNN
- Supports branching and skip connections
- Allows multiple inputs and outputs
- Examples: **Inception**, **ResNet**

---

### 4.2 Implementation Categories

#### Default (Pre-trained / State-of-the-Art) Models
- Widely accepted baseline architectures
- Often required by journals for benchmarking

#### Customized Models
Customization can be done in two ways:

- **Partial Customization**
  - Modify existing architectures
  - Example: Reducing VGG16’s fully connected layers from three to one to improve performance

- **Full Customization**
  - Build a model from scratch
  - Inspired by existing designs but fully task-specific
  - Example: A custom CNN for histopathology inspired by VGG-style layering

---

## 5.0 A Deeper Look into Image Classification

---

### 5.1 Types of Classification Problems

- **Binary Classification**
  - Two mutually exclusive outcomes
  - Example: disease vs. non-disease

- **Multi-Class Classification**
  - More than two mutually exclusive classes
  - Example: categorizing liver tumors into multiple cancer types

- **Multi-Label (Multi-Level) Classification**
  - Multiple labels per image
  - Example: tagging an image as *dog*, *brown*, and *wearing glasses*

---

### 5.2 Types of Input Data for CNNs

- **Whole Image Input**
- **Cropped Image (ROI-based)**
- **Patch-Based Classification**
  - Used for large images like Whole Slide Images
  - Referenced in colorectal cancer research and ischemic stroke analysis

- **Data Augmentation**
  - Increases dataset size
  - Improves generalization
  - Reduces overfitting

- **Heatmaps**
  - Rarely used as primary inputs
  - Commonly used for **model interpretation and validation**

---

## 6.0 Building a CNN: Layer-by-Layer Walkthrough

### CNN Workflow Overview

```mermaid
flowchart LR
    A[Input Image] --> B[Convolution Layer]
    B --> C[Activation ReLU]
    C --> D[Pooling Layer]
    D --> E[Flatten Layer]
    E --> F[Fully Connected Layers]
    F --> G[Output Layer]
````

---

### Step 1: Data and Library Preparation

* Dataset split into **training, validation, and testing**
* Analogy: lecture → homework → final exam

### Step 2: Convolutional Layer

* Learns spatial patterns using filters
* Key parameters: filters, kernel size, stride, padding

### Step 3: Activation Function

* Introduces non-linearity
* ReLU converts negative values to zero

### Step 4: Pooling Layer

* Reduces spatial dimensions
* Improves computational efficiency and robustness

### Step 5: Flatten Layer

* Converts 2D feature maps into a 1D vector

### Step 6: Fully Connected Layer

* Acts as the classifier
* Generates final predictions

### Step 7: Dropout (Regularization)

* Randomly deactivates neurons
* Prevents overfitting

### Step 8: Output Layer

* Binary classification: Sigmoid
* Multi-class classification: Softmax

---

