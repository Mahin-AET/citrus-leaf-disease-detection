# citrus-leaf-disease-detection
Deep learning-based differentiation of HLB and zinc deficiency in citrus leaves (Sylhet dataset)

## Introduction

Citrus production in Sylhet, Bangladesh is affected by both Huanglongbing (HLB) and zinc deficiency. These two conditions often exhibit visually similar symptoms on leaves, making manual diagnosis difficult for farmers. Misidentification can lead to incorrect treatment decisions and reduced crop yield.

This project proposes a deep learning-based approach to automatically classify citrus leaves into Healthy, HLB, and Zinc Deficiency categories using field-collected data.

---

## Problem Statement

Huanglongbing (HLB) and zinc deficiency show similar visual characteristics such as leaf chlorosis and mottling, which makes them difficult to distinguish, especially without expert knowledge.

As a result:
- Farmers often confuse HLB with zinc deficiency  
- Incorrect diagnosis leads to improper treatment  
- This increases economic loss and affects citrus production  

The main objective of this project is to develop an automated system that can accurately differentiate between HLB and zinc deficiency in citrus leaves.

## Dataset

The dataset consists of **3557 citrus leaf images** collected from five different gardens in Sylhet, Bangladesh during 2025.

### Data Split
- Training: 2489 images (**70%**)  
- Validation: 534 images (**15%**)  
- Testing: 534 images (**15%**)  

### Classes
- Zinc Deficient  
- Huanglongbing (HLB)
- Healthy
  

---

## Data Collection

Data were collected under real field conditions using a DSLR camera during daytime with natural lighting. Images were captured at an approximate distance of **20 cm** from the leaves.

To ensure consistency and reduce background noise:
- Leaves were placed on a **uniform white board background**  
- Each image contained **3 to 5 leaves per frame**, depending on leaf size  

This multi-leaf acquisition strategy significantly improved data collection efficiency by reducing time and cost compared to capturing single leaves per image.

---

## Preprocessing Pipeline

A multi-stage preprocessing pipeline was developed to convert raw images into model-ready samples:

### Pipeline Overview

Raw Image (multiple leaves)  
→ Background Removal  
→ Leaf Separation  
→ Aspect Ratio Preservation  
→ Final Dataset  

---

### Background Removal

Background removal was performed using a color-based segmentation approach in HSV color space. A broad color range was used to detect and remove background regions, followed by morphological operations (closing, opening, erosion, dilation) to refine the leaf mask and eliminate noise.

---

### Leaf Separation

After background removal, individual leaves were extracted using contour detection:

- Contours were identified and sorted based on area  
- Each leaf was cropped using bounding boxes with padding  
- Noise and small artifacts were removed using area thresholding  

---

### Aspect Ratio Preservation

Each extracted leaf was resized (4000x4000) while preserving its original aspect ratio. The processed leaf was then placed onto a fixed-size canvas to ensure uniform input dimensions for model training.

---

### Annotation

All processed images were annotated using **LabelImg** in YOLO format, where each image contains bounding box annotations corresponding to the target classes.
