# Annotation Format

This project uses the YOLO annotation format for labeling citrus leaf images.

## Labeling Tool
Annotations were created using **LabelImg**.

## Format Description

Each image has a corresponding `.txt` file with the same name.

Each line in the annotation file represents one object and follows this format:

class_id x_center y_center width height

All values are normalized between 0 and 1 relative to image width and height.

---

## Class Mapping

- 0 → Healthy  
- 1 → Huanglongbing (HLB)  
- 2 → Zinc Deficiency  

---

## Example

For an image `leaf_1.jpg`, the annotation file `leaf_1.txt` might look like:

1 0.512 0.433 0.245 0.378

This means:
- Class: HLB  
- Bounding box centered at (51.2%, 43.3%)  
- Width: 24.5% of image  
- Height: 37.8% of image  

---

## Notes

- Each image contain one annotated leaves  
- Bounding boxes were carefully drawn to tightly fit each leaf  
- Annotations were reviewed to ensure consistency across classes

 !(annotation/01.PNG)
