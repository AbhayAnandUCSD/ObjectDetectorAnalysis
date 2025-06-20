# Object Detector Analysis

This repository contains code, data, and analysis for a comparative study of modern object detection algorithms: **Faster R-CNN**, **YOLO-World**, and **GroundingDINO**. The project evaluates models on their **bounding box accuracy** and **prompt-based detection capabilities**, using metrics like **IoU**, **Precision**, **Recall**, and **F1 Score**.

📄 **[View full project report (PDF)](https://drive.google.com/file/d/1dXUqsT8HuQmQKK1dGLFox6stfrqnkcA5/view)**

---

## 🔍 Objective

To analyze the effectiveness of prompt-based and traditional object detectors across:
- Standard object detection (e.g., apples)
- Prompt-based open-vocabulary detection
- Robustness under diverse, real-world conditions

---

## Models Analyzed

### 1. **Faster R-CNN (ResNet-50)**
- Closed-vocabulary detector pretrained on COCO
- Reliable for fixed-label detection
- Not suitable for prompt-based or novel object recognition

### 2. **YOLO-World**
- Single-stage detector with CLIP-based text embedding
- Supports open-vocabulary detection using prompts
- Highly sensitive to threshold tuning and prompt wording

### 3. **GroundingDINO**
- Transformer-based architecture using CLIP for text grounding
- Achieved highest IoU and F1 scores
- Robust to prompt rewording and image complexity

---

 <pre> 
   ObjectDetectorAnalysis/ 
   ├── apl/ # Apple image dataset for evaluation 
   ├── data/ # Dataset for robustness testing 
   ├── ResultIMGS/ # Model prediction output images 
   ├── FinalModelComp.ipynb # Comparison of YOLO-World, RCNN, GroundingDINO 
   ├── WeirdImgData.ipynb # Robustness testing on challenging images 
   ├── README.md # Project overview and usage instructions 
   └── .DS_Store # (System file — safe to delete) </pre> 


---

## Datasets

### Apple Detection Dataset
Used to benchmark box prediction accuracy across models.

### Robustness Evaluation Dataset
Curated to test:
- Complex scenes
- Small and overlapping objects
- Occlusions
- Unusual prompts
- Blurry / noisy images
- Symbol and scene detection

---

## Metrics

- **Intersection over Union (IoU)**
- **Precision / Recall**
- **F1 Score**

> Key Findings:
> - GroundingDINO performed best in almost all categories.
> - YOLO-World requires precise threshold tuning and prompt phrasing.
> - Faster R-CNN lacks prompt support, good only for known COCO classes.

| Model          | Box Thresh | Text Thresh | Precision | Recall | F1 Score | Mean IoU |
|----------------|-------------|--------------|-----------|--------|----------|----------|
| GroundingDINO  | 0.35        | 0.2          | 0.690     | 0.825  | 0.712    | 0.830    |
| YOLO-World     | 0.08        | -            | 0.673     | 0.910  | 0.732    | 0.897    |
| Faster R-CNN   | -           | -            | ✓ (COCO only) | ✗ (no prompts) | ✗ | ✗ |

---

