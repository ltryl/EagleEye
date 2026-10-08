# EagleEye: AI-Powered Detection of Small Objects in UAV Footage

## Overview

**EagleEye** is an artificial intelligence-based framework designed to tackle the critical challenges of small object detection in unmanned aerial vehicle (UAV) imagery. Developed as a graduation project within the Information Technology Department at Qassim University, the system addresses inherent difficulties in aerial remote sensing, such as extremely small target sizes (often 10 to 30 pixels), scale variations, dense clustering, and complex backgrounds.

The framework systematically evaluates modern deep learning object detection models—specifically the YOLO family—and delivers an optimized architecture tailored for high-altitude aerial surveillance, traffic monitoring, and public safety applications.

## Key Features & Contributions

* **Rigorous Architectural Benchmarking:** Systematic comparison of YOLOv8m, YOLOv9m, and YOLO11m under identical baseline conditions.


* **Optimized Backbone:** Integration of YOLO11m as the core feature extractor due to its superior balance of accuracy and computational efficiency (67.7 GFLOPs).


* **Enhanced Small-Target Acquisition:** Implementation of a high-resolution P2 detection head to preserve fine-grained spatial details for minute targets.


* **Progressive Training Pipeline:** A custom four-stage training strategy utilizing mosaic and mixup augmentations to refine detection capabilities.



## Dataset

The model was trained and evaluated on the publicly available **VisDrone2019-DET** benchmark dataset.

* **Scope:** 6,471 training images and 548 validation images.


* **Classes:** 10 categories, including pedestrian, people, bicycle, car, van, truck, tricycle, awning-tricycle, bus, and motor.


* **Preprocessing:** Annotations were converted from the proprietary VisDrone format to YOLO-compatible normalized center-coordinates.



## Methodology

The EagleEye system isolates failure modes in high-entropy backgrounds through a specialized pipeline:

1. **Baseline Evaluation:** YOLO11m was selected over YOLOv8m and YOLOv9m for yielding the highest mAP with the lowest computational weight.


2. **Multi-Stage Training:** A 4-stage pipeline incorporating extended epochs and adaptive learning rates (AdamW optimizer) to stabilize convergence.


3. **Architectural Extension:** A P2 detection layer (stride 8) was added to generate anchors for objects as small as $8\times8$ pixels.



## Results & Performance

EagleEye outperforms several state-of-the-art (SOTA) lightweight methods while maintaining practical real-time efficiency.

* **mAP@0.5:** 0.459


* **mAP@0.5:0.95:** 0.275


* **Precision:** 0.570


* **Recall:** 0.459



## Tech Stack

* **Frameworks & Libraries:** Ultralytics (YOLO), PyTorch, PIL


* **Hardware Environment:** Google Colab, NVIDIA Tesla T4 GPU


* **Languages:** Python 3



## Future Roadmap

Based on qualitative error analysis, future developments for EagleEye will target:

* **Resolution Scaling:** Moving from 640x640 input resolution to 1280x1280 or utilizing Slicing-Aided Hyper Inference (SAHI) tiling to recover targets smaller than 15x15 pixels.


* **Density-Aware Suppression:** Replacing standard Non-Maximum Suppression (NMS) with Soft-NMS to prevent the suppression of genuine adjacent objects in tightly clustered scenes.


* **Class-Balanced Training:** Implementing frequency-weighted loss scaling to improve detection for underrepresented classes like bicycles and awning-tricycles.



## Team

**Students:** Abdullah Aldahami, Meshal Alfehaid, Abdulaziz Almutiri, and Turki Alharbi.
**Supervisor:** Prof. Dina M. Ibrahim.
College of Computer, Information Technology Dept., Qassim University.
