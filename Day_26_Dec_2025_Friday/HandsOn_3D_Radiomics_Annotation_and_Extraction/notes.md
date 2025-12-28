
#  Hands-on: Basic 3D Medical Image Annotation using 3D Slicer

## Objective

To understand the **end-to-end workflow of loading 3D medical imaging data, performing manual ROI segmentation, visualizing it in 3D, and exporting the segmentation mask**, which forms the foundational step for radiomics and AI-based medical image analysis.

---

## 1. Software Setup

* Installed **3D Slicer (v5.10.0)** on local machine
* Installed **MONAI Label extension** via Slicer Extension Manager
  *(Note: MONAI Label server setup is optional; this exercise focuses on core annotation workflow)*

---

## 2. Loading Sample Medical Imaging Data

Instead of using external datasets, **built-in Sample Data** provided by 3D Slicer was used.

### Steps:

1. Open **3D Slicer**
2. Navigate to **Modules → Sample Data**
3. Downloaded a sample dataset (e.g., CT/MRI volume)
4. Verified successful loading by scrolling through:

   * Axial (Red)
   * Sagittal (Yellow)
   * Coronal (Green) views

 This confirms correct loading of 3D volumetric medical data.

---

## 3. Image Visualization & Basic Interaction

* Adjusted **window and level (brightness/contrast)** using mouse interaction
* Scrolled through slices to understand anatomical structures
* Identified a **region of interest (ROI)** suitable for annotation

Purpose:

> To become familiar with volumetric navigation and anatomical context.

---

## 4. Manual ROI Segmentation (Core Step)

### Module Used:

**Segment Editor**

### Steps:

1. Open **Modules → Segment Editor**
2. Click **Add Segment**
3. Renamed the segment to a meaningful name (e.g., `ROI_Test`)
4. Used:

   * **Paint tool** for slice-wise annotation
   * **Erase tool** for corrections
5. Annotated a **small region across 5–10 consecutive slices** (demonstration-level segmentation)

 Focus was on understanding the process, not full organ segmentation.

---

## 5. 3D Visualization of Segmentation

* Enabled **Show 3D** option
* Inspected the segmented ROI in the 3D view
* Ensured:

  * No isolated artifacts
  * Reasonable anatomical continuity

Purpose:

> To verify spatial consistency of slice-wise segmentation.

---

## 6. Exporting the Segmentation Mask

To prepare the output for radiomics or AI pipelines:

1. Open **Segmentations** module
2. Click **Export**
3. Exported segmentation as a **Labelmap**
4. Saved the mask in **.nii / .nii.gz** format

 Final outputs:

* Original 3D medical image
* Corresponding ROI segmentation mask

---

## 7. Relevance to Radiomics & AI Workflows

This workflow represents the **standard preprocessing stage** used in:

* Radiomics feature extraction
* AI-based segmentation and classification pipelines
* Clinical annotation and dataset preparation

Manual segmentation remains a **gold standard reference** in many biomedical imaging studies.

---
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/bfe1ca0f-6a39-4737-bf72-d632b71ebf06" />


## Summary

> Successfully performed manual 3D ROI annotation using 3D Slicer, including data loading, slice-wise segmentation, 3D verification, and mask export—forming a foundational step for radiomics and AI-based medical image analysis.

---
