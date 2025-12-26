## Session: 3D Radiomics in Medical Modalities

**Speaker:** Dr. Pushpanjali Gupta
**Designation:** Pursuing PhD
**Organization:** National Yang Ming Chiao Tung University , Taiwan 
---

## 1. What is Radiomics?

Radiomics converts medical images into **quantitative data**.
It extracts features invisible to the human eye, enabling deeper biological insights.

### Why Radiomics is needed:

* Similar-looking images may represent different diseases
* Tumor boundaries may be unclear
* Manual feature extraction is subjective
* Deep learning alone lacks explainability

Radiomics offers a **standardized, explainable alternative**.

---

## 2. Radiomics Feature Categories

### 2.1 First-Order (Intensity-Based) Features

* Describe pixel/voxel intensity distribution
* Do not consider spatial relationships

Examples:

* Mean
* Median
* Variance
* Energy
* Entropy

---

### 2.2 Shape-Based Features

* Describe geometry of the lesion

Examples:

* Volume
* Surface area
* Sphericity
* Elongation
* Axis length

---

### 2.3 Texture (Second-Order) Features

Capture spatial relationships and heterogeneity.

#### Major matrices:

* **GLCM**: contrast, homogeneity
* **GLSZM**: zone size and coarseness
* **GLRLM**: directional texture patterns
* **GLDM**: local gray-level dependencies
* **NGTDM**: neighborhood intensity differences

These features provide a **digital fingerprint** of tissue.

---

## 3. Radiomics Workflow

### Step-by-step process:

1. **Input**

   * DICOM medical images

2. **Segmentation**

   * ROI outlined in 3D
   * Can be manual or automated

3. **Filtering**

   * Laplacian of Gaussian
   * Wavelet filters
   * Enhances edges and textures

4. **Feature Extraction**

   * Shape features → original image
   * Texture & intensity → original + filtered images

5. **Tools Used**

   * 3D Slicer
   * MONAI Label
   * Pyradiomics

---

## 4. Clinical Impact of Radiomics

Radiomics enables:

* Early detection
* Tumor characterization
* Prognosis prediction
* Treatment response assessment

It forms the **technical backbone of precision medicine** in imaging.

---
